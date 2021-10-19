---
title: Объемная отрисовка
description: Код, позволяющий эффективно визуализировать насыщенные объемные изображения с непрозрачностью и цветом в Windows Mixed Reality.
author: kevinkennedy
ms.author: v-vtieto
ms.date: 09/02/2021
ms.topic: article
keywords: образ объемные, подготовка тома, производительность, Смешанная реальность
ms.openlocfilehash: 91d6661df71abe9dda917198ae116fedb5f2fd64
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130157628"
---
# <a name="volume-rendering"></a>Объемная отрисовка

Если вы не знакомы с отрисовкой тома, рекомендуем ознакомиться с [нашим обзором](../advanced-concepts/volume-rendering-overview.md).

## <a name="representing-3d-textures"></a>Представление трехмерных текстур

На ЦП:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

На GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>Заливка и градиенты

Как затенить том, например MRI, для полезной визуализации. Основным методом является «окно интенсивности» (минимальное и максимальное), интенситиес в рамках, и просто масштабируется в это пространство, чтобы увидеть интенсивность черной и белой шкалы. Цветовая шкала может быть применена к значениям в пределах этого диапазона и сохранена в виде текстуры, чтобы различные части спектра интенсивности можно было затенить разными цветами:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

Во многих наших приложениях мы сохраняем на нашем томе значение интенсивности необработанных данных и "индекс сегментации" (для сегментирования различных частей, таких как Обложка и кость; эти сегменты создаются экспертами в выделенных инструментах). Это можно сочетать с описанным выше способом, чтобы задать другой цвет или даже разную цветовую шкалу для каждого индекса сегмента:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Срез томов в шейдере

Отличным первым шагом является создание "плоскости среза", которая может перемещаться по тому, "размещая ее" и проверять значения в каждой точке. Предполагается, что существует куб «Волумеспаце», который представляет место, где находится том в мировом пространстве, который можно использовать в качестве ссылки для размещения точек:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Трассировка тома в шейдере

Как использовать GPU для трассировки подразделов (проходит несколько вокселс, а затем слои данных с обратно на передний план):

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>Отрисовка всего тома

Изменив приведенный выше код подтома, мы получаем:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Отображение сцены смешанного разрешения

Как отобразить часть сцены с низким разрешением и вернуть ее на месте:
1. Установка двух экранных камер: один для отслеживания каждого глаза, который обновляет каждый кадр
2. Настройка двух целевых объектов отрисовки с низким разрешением (т. е. 200x200 каждый), которые визуализируются камерами
3. Настройка «четыре», которые переходят перед пользователем

Каждый кадр:
1. Нарисуйте цели рендеринга для каждого взгляда с низким разрешением (данные тома, дорогостоящие шейдеры и т. д.).
2. Отрисовка сцены в обычном режиме с полным разрешением (сетки, Пользовательский интерфейс и т. д.)
3. Нарисуйте «четыре» перед пользователем, на сцене и проецирование низкого уровня просмотра на этот
4. Результат: визуальное сочетание элементов с полным разрешением с низким разрешением, но с данными с высокой плотностью

