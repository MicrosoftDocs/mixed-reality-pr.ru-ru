---
ms.openlocfilehash: 45b171d3d5856dd17f9223d945a1d0fd46326600b3ed65bc4198c6da5fa524f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207589"
---
# <a name="426"></a>[4.26](#tab/426) 

## <a name="pv-camera-feed-setup"></a>Настройка потока данных с фотовидеокамеры

> [!IMPORTANT]
> Фото- и видеокамера реализована в подключаемых модулях для Windows Mixed Reality и OpenXR. Но для работы OpenXR необходимо установить [подключаемый модуль Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal). Кроме того, OpenXR имеет ограничение: камера может работать только с DirectX11 RHI. Это ограничение будет устранено в будущей версии Unreal. 

- В разделе **Project Settings > HoloLens** (Параметры проекта > HoloLens) включите возможность **Webcam** (Веб-камера):

![Снимок экрана: параметры проекта HoloLens с выделенным свойством Webcam](../images/unreal-pvc-img-01.png)

- Создайте субъект с именем CamCapture и добавьте плоскость для визуализации данных с камеры:

![Снимок экрана: субъект с добавленной плоскостью](../images/unreal-pvc-img-02.png)

- Добавьте субъект в сцену, создайте материал с именем CamTextureMaterial с параметром объекта текстуры и пример текстуры.  Отправьте RGB-данные текстуры в выходной излучаемый цвет:

![Схема материала и пример текстуры](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a>Визуализация потока данных с фотовидеокамеры

- В схеме CamCapture включите фотовидеокамеру:

![Схема функции Toggle ARCapture с включенной фотовидеокамерой](../images/unreal-pvc-img-04.png)

- Создайте экземпляр динамического материала из CamTextureMaterial и назначьте этот материал плоскости субъекта:

![Схема функции Create Dynamic Material Instance](../images/unreal-pvc-img-05.png)

- Получите текстуру из потока данных камеры и назначьте ее динамическому материалу (если она допустимая).  Если текстура не является допустимой, запустите таймер и повторите попытку после его истечения:

![Схема текстуры из потока данных камеры, назначенной динамическому материалу](../images/unreal-pvc-img-06.png)

- Наконец, масштабируйте плоскость по пропорциям изображения камеры:

![Схема плоскости, масштабированная относительно пропорций изображения с камеры](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a>Поиск позиций камеры в мировом пространстве

Камера на HoloLens 2 смещена вертикально по отношению к позиции отслеживания головы на устройстве.  Для компенсации такого смещения доступно несколько функций, которые позволяют определить положение камеры в абсолютном пространстве.

GetPVCameraToWorldTransform получает преобразование в абсолютном пространстве фотовидеокамеры, располагаясь на линзе камеры:

![Схема функции Get PVCamera to World Transform](../images/unreal-pvc-img-08.png)

GetWorldSpaceRayFromCameraPoint пускает луч из объектива камеры в сцену в абсолютном пространстве Unreal, чтобы определить содержимое пикселя в кадре камеры:

![Схема функции Get World Space Ray from Camera Point](../images/unreal-pvc-img-09.png)

GetPVCameraIntrinsics возвращает характерные значения камеры, которые можно использовать при обработке кадра камеры с помощью компьютерного зрения:

![Схема функций Get PVCamera Intrinsics](../images/unreal-pvc-img-10.png)

Чтобы определить, что находится в реальном пространстве по определенной пиксельной координате, используйте трассировку линии с помощью луча абсолютного пространства:

![Схема луча мирового пространства, используемого для определения того, что находится в мировом пространстве по определенной координате](../images/unreal-pvc-img-11.png)

Здесь мы выпускаем из объектива камеры луч длиной 2 метра в верхнюю левую четверть кадра камеры.  Затем мы используем результат попадания для визуализации той позиции, в которой существует объект в мировом пространстве:

![Схема выпуска из объектива камеры луча длиной 2 метра в верхнюю левую четверть кадра камеры](../images/unreal-pvc-img-12.png)

При использовании пространственного сопоставления такая позиция попадания будет соответствовать поверхности, которую видит камера.

## <a name="rendering-the-pv-camera-feed-in-c"></a>Визуализация потока данных с фотовидеокамеры в C++

- Создание нового субъекта C++ с именем CamCapture
- В файле build.cs проекта добавьте AugmentedReality в список PublicDependencyModuleNames:

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "AugmentedReality"
});
```

- в файле CamCapture.h включите ARBlueprintLibrary.h:

```cpp
#include "ARBlueprintLibrary.h"
```

- Вам также нужно добавить локальные переменные для сетки и материала:

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- В файле CamCapture.cpp обновите конструктор для добавления статической сетки в сцену:

```cpp
ACamCapture::ACamCapture()
{
    PrimaryActorTick.bCanEverTick = true;

    // Load a mesh from the engine to render the camera feed to.
    StaticMesh = LoadObject<UStaticMesh>(nullptr, TEXT("/Engine/EngineMeshes/Cube.Cube"), nullptr, LOAD_None, nullptr);

    // Create a static mesh component to render the static mesh
    StaticMeshComponent = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CameraPlane"));
    StaticMeshComponent->SetStaticMesh(StaticMesh);

    // Scale and add to the scene
    StaticMeshComponent->SetWorldScale3D(FVector(0.1f, 1, 1));
    this->SetRootComponent(StaticMeshComponent);
}
```

В BeginPlay создайте экземпляр динамического материала из материала камеры в проекте, примените его к компоненту статической сетки и запустите камеру HoloLens. 
 
В редакторе щелкните CamTextureMaterial в обозревателе содержимого и выберите Copy Reference (Копировать ссылку), чтобы получить строку для CameraMatPath.

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMaterial = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

В Tick получите текстуру с камеры, сопоставьте ее с параметром текстуры в материале CamTextureMaterial и масштабируйте компонент статической сетки по пропорциям кадра камеры:

```cpp
void ACamCapture::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    // Dynamic material instance only needs to be set once.
    if(IsTextureParamSet)
    {
        return;
    }

    // Get the texture from the camera.
    UARTexture* ARTexture = UARBlueprintLibrary::GetARTexture(EARTextureType::CameraImage);
    if(ARTexture != nullptr)
    {
        // Set the shader's texture parameter (named "Param") to the camera image.
        DynamicMaterial->SetTextureParameterValue("Param", ARTexture);
        IsTextureParamSet = true;

        // Get the camera instrincs
        FARCameraIntrinsics Intrinsics;
        UARBlueprintLibrary::GetCameraIntrinsics(Intrinsics);

        // Scale the camera mesh by the aspect ratio.
        float R = (float)Intrinsics.ImageResolution.X / (float)Intrinsics.ImageResolution.Y;
        StaticMeshComponent->SetWorldScale3D(FVector(0.1f, R, 1));
    }
}
```

# <a name="425"></a>[4.25](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a>Отрисовка с фото- и видеокамеры для MRC

> [!NOTE]
> Для этого требуется **Unreal Engine версии 4.25** и выше.

Системные и пользовательские средства MRC выполняют съемку смешанной реальности, совмещая изображение с фотовидеокамеры и голограммы, которые отрисовываются приложением.

По умолчанию для съемки смешанной реальности используется голографический вывод правого глаза. В иммерсивном приложении вместо этого можно выбрать [отрисовку с фотовидеокамеры](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in). Это улучшает соответствие между реальным миром и голограммами в видео MRC.

Чтобы включить отрисовку с фотовидеокамеры, сделайте следующее:

1. Вызовите функции **SetEnabledMixedRealityCamera** и **ResizeMixedRealityCamera**.
    * Задайте размеры видеоизображения с помощью параметров **Size X** (Размер по X) и **Size Y** (Размер по Y).

![Третья камера](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

После этого Unreal будет обрабатывать запросы от MRC на отрисовку с точки зрения фото- и видеокамеры.

> [!NOTE]
> Приложению будет даваться команда на отрисовку с точки зрения фото- и видеокамеры только в том случае, если активирована [съемка смешанной реальности](/hololens/holographic-photos-and-videos).

## <a name="using-the-pv-camera"></a>Использование фото- и видеокамеры

Текстуру с веб-камеры можно получить в игре во время выполнения, но эту возможность необходимо включить в разделе **Edit > Project Settings** (Правка > Параметры проекта) редактора:
1. Выберите **Platforms > HoloLens > Capabilities** (Платформы > HoloLens > Возможности) и установите флажок **Webcam** (Веб-камера).
    * Чтобы начать запись с веб-камеры во время выполнения, вызовите функцию **StartCameraCapture**, а чтобы остановить запись, вызовите функцию **StopCameraCapture**.

![Запуск и остановка камеры](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>Отрисовка изображения
Для отрисовки изображения с камеры:
1. Создайте динамический экземпляр материала на основе материала **PVCamMat** из проекта (см. снимок экрана ниже).  
2. Сохраните новый динамический экземпляр материала в переменной **Material Instance Dynamic Object Reference** (Ссылка на динамический объект экземпляра материала).  
3. Выберите этот динамический экземпляр материала в качестве материала объекта в сцене, где будет отрисовываться изображение с камеры.
    * Запустите таймер, по которому будет выполняться привязка изображения с камеры будет к материалу.

![Отрисовка камеры](../images/unreal-camera-render.PNG)

4. Создайте для этого таймера новую функцию (в нашем примере это **MaterialTimer**) и вызовите функцию **GetARCameraImage**, чтобы получить текстуру с веб-камеры.  
5. Если эта текстура допустима, установите это изображение в качестве значения параметра текстуры в шейдере.  В противном случае снова запустите таймер обновления материала.

![Текстура камеры с веб-камеры](../images/unreal-camera-texture.PNG)

5. У материала должен быть параметр с таким же именем, как имя параметра функции **SetTextureParameterValue**, привязанное к записи о цвете. Без этого параметра изображение с камеры не отобразится правильно.

![Текстура от камеры](../images/unreal-camera-material.PNG)