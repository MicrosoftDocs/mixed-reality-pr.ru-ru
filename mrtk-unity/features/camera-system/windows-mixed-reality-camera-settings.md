---
title: Параметры камеры Windows Mixed Reality
description: документация по использованию Windows Mixed Reality параметров камеры в мртк
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, камера,
ms.openlocfilehash: 6d0231c070cd001d7e01b4a82ab66c2a9c5c115240b03e28b7d49a14de1753f1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212699"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>поставщик параметров камеры Windows Mixed Reality

поставщик параметров камеры Windows Mixed Reality определяет тип устройства, на котором выполняется приложение, и применяет соответствующие параметры конфигурации на экране (прозрачный или непрозрачный).

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>включение поставщика параметров камеры Windows Mixed Reality

В следующих шагах предполагается использование объекта Микседреалититулкит. Действия, необходимые для других регистраторов служб, могут отличаться.

1. Выберите объект Микседреалититулкит в иерархии сцены.

    ![МРТК настроенная иерархия сцены](../images/MRTK_ConfiguredHierarchy.png)

2. перейдите на панель инспектора к разделу система камеры и разверните раздел **поставщики Параметры камеры** .

    ![Разверните узел Параметры поставщики.](../images/camera-system/ExpandProviders.png)

3. щелкните **добавить камера Параметры поставщик** и разверните добавленную **новую запись параметров камеры** .

    ![Развернуть поставщик новых параметров](../images/camera-system/ExpandNewProvider.png)

4. выбор поставщика Параметры Windows Mixed Reality камеры

    ![выбор поставщика параметров Windows Mixed Reality](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> при использовании профилей по умолчанию для набор средств Microsoft Mixed Reality поставщик параметров Windows Mixed Reality камеры будет включен и настроен.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>настройка поставщика параметров камеры Windows Mixed Reality

Windows Mixed Reality камера Параметры также поддерживает профиль. Этот профиль предоставляет следующие возможности.

![конфигурация параметров камеры Windows Mixed Reality](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>Отображение записи смешанной реальности из фото-или видеокамеры

с помощью этого параметра на HoloLens 2 можно включить выравнивание голограмм в записи смешанной реальности. Если этот параметр включен, платформа предоставит дополнительные Холографиккамера для приложения при создании фотографии или видео с записью смешанной реальности. Этот Холографиккамера предоставляет матрицы представлений, соответствующие расположению фотографии или видеокамеры, и предоставляет матрицы проекции с помощью поля "Фото-видеокамера" представления. Это обеспечит, чтобы голограммы, такие как сетки, оставались видимыми в выводе видео.

### <a name="hololens-2-reprojection-method"></a>HoloLens 2 метод репроекции

задает начальный метод для HoloLens 2 репроекции. По умолчанию рекомендуется использовать репроект глубины, так как все части сцены будут независимо изменяться в зависимости от расстояния от пользователя. Если голограммы по-прежнему отображаются нестабильно, попробуйте убедиться, что все объекты правильно отправили свою глубину в буфер глубины. Иногда это параметр шейдера. Если глубина будет правильно отправлена, а нестабильность все еще присутствует, попробуйте использовать стабилизации, который использует буфер глубины для вычисления плоскости стабилизации. Если приложению не удается отправить достаточное количество данных глубины для использования одним из этих вариантов, в качестве резерва предоставляется плоская ревариантная репроецирование. Этот метод будет основан на предоставленных приложением данных фокусной точки через [сетфокуспоинтфорфраме](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).

Чтобы обновить метод РЕПРОЕКЦИИ во время выполнения, `WindowsMixedRealityReprojectionUpdater` выполните следующий доступ:

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

Это необходимо обновить только один раз, а значение повторно используется для всех последующих кадров. Если метод будет обновляться часто, рекомендуется кэшировать результат, `EnsureComponent` а не вызывать его часто.

## <a name="see-also"></a>См. также раздел

- [Обзор системы камеры](camera-system-overview.md)
- [создание поставщика Параметры камеры](create-settings-provider.md)
- [Визуализация записи смешанной реальности с камеры PV](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Holographic, репроектное](/windows/mixed-reality/hologram-stability#reprojection)