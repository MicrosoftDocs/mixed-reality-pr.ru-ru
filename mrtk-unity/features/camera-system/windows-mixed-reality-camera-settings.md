---
title: Параметры камеры Windows Mixed Reality
description: Документация по использованию параметров камеры Windows Mixed Reality в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, Камера,
ms.openlocfilehash: 49b178b7ebd1fbcdaab9648baeaa6abfa9e885ea
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121642"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Поставщик параметров камеры Windows Mixed Reality

Поставщик параметров камеры Windows Mixed Reality определяет тип устройства, на котором выполняется приложение, и применяет соответствующие параметры конфигурации, основанные на отображении (прозрачном или непрозрачном).

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>Включение поставщика параметров камеры Windows Mixed Reality

В следующих шагах предполагается использование объекта Микседреалититулкит. Действия, необходимые для других регистраторов служб, могут отличаться.

1. Выберите объект Микседреалититулкит в иерархии сцены.

    ![МРТК настроенная иерархия сцены](../images/MRTK_ConfiguredHierarchy.png)

2. Перейдите на панель инспектора к разделу система камеры и разверните раздел **поставщики параметров камеры** .

    ![Разверните узел Параметры поставщики.](../images/camera-system/ExpandProviders.png)

3. Нажмите кнопку **Добавить поставщик параметров камеры** и разверните добавленную **новую запись параметров камеры** .

    ![Развернуть поставщик новых параметров](../images/camera-system/ExpandNewProvider.png)

4. Выберите поставщик параметров камеры Windows Mixed Reality

    ![Выберите поставщик параметров Windows Mixed Reality](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> При использовании профилей Microsoft Mixed Reality Toolkit по умолчанию поставщик параметров камеры Windows Mixed Reality уже будет включен и настроен.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Настройка поставщика параметров камеры Windows Mixed Reality

Параметры камеры Windows Mixed Reality также поддерживают профиль. Этот профиль предоставляет следующие возможности.

![Конфигурация параметров камеры Windows Mixed Reality](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>Отображение записи смешанной реальности из фото-или видеокамеры

С помощью этого параметра в HoloLens 2 можно включить выравнивание голограмм в записи смешанной реальности. Если этот параметр включен, платформа предоставит дополнительные Холографиккамера для приложения при создании фотографии или видео с записью смешанной реальности. Этот Холографиккамера предоставляет матрицы представлений, соответствующие расположению фотографии или видеокамеры, и предоставляет матрицы проекции с помощью поля "Фото-видеокамера" представления. Это обеспечит, чтобы голограммы, такие как сетки, оставались видимыми в выводе видео.

### <a name="hololens-2-reprojection-method"></a>Метод репроекта HoloLens 2

Задает начальный метод для РЕПРОЕКЦИИ HoloLens 2. По умолчанию рекомендуется использовать репроект глубины, так как все части сцены будут независимо изменяться в зависимости от расстояния от пользователя. Если голограммы по-прежнему отображаются нестабильно, попробуйте убедиться, что все объекты правильно отправили свою глубину в буфер глубины. Иногда это параметр шейдера. Если глубина будет правильно отправлена, а нестабильность все еще присутствует, попробуйте использовать стабилизации, который использует буфер глубины для вычисления плоскости стабилизации. Если приложению не удается отправить достаточное количество данных глубины для использования одним из этих вариантов, в качестве резерва предоставляется плоская ревариантная репроецирование. Этот метод будет основан на предоставленных приложением данных фокусной точки через [сетфокуспоинтфорфраме](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).

Чтобы обновить метод РЕПРОЕКЦИИ во время выполнения, `WindowsMixedRealityReprojectionUpdater` выполните следующий доступ:

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

Это необходимо обновить только один раз, а значение повторно используется для всех последующих кадров. Если метод будет обновляться часто, рекомендуется кэшировать результат, `EnsureComponent` а не вызывать его часто.

## <a name="see-also"></a>См. также

- [Обзор системы поддержки камер](camera-system-overview.md)
- [Создание поставщика параметров камеры](create-settings-provider.md)
- [Визуализация записи смешанной реальности с камеры PV](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Holographic, репроектное](/windows/mixed-reality/hologram-stability#reprojection)