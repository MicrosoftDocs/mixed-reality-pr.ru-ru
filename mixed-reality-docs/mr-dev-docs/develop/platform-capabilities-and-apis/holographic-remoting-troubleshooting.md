---
title: Устранение неполадок и ограничения удаленного взаимодействия с holographic
description: найдите материалы по устранению неполадок и инструкции для функции holographic remoting на HoloLens 2 устройствах.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, удаленное взаимодействие, дистанционная визуализация, подготовка к просмотру сети, HoloLens, удаленные голограммы, устранение неполадок, помощь, гарнитура смешанной реальности, гарнитура Windows mixed reality, гарнитура виртуальной реальности
ms.openlocfilehash: fa984e89fb6eb770917d9a1d62ce7c1007d45fab7fbcb2723f9642ac81814054
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223574"
---
# <a name="holographic-remoting-troubleshooting"></a>Устранение неполадок удаленного взаимодействия с holographic

> [!IMPORTANT]
> Это руководство относится к удаленному взаимодействию с HoloLens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Не найдены библиотеки, снижающие опасность устранением рисков Spectre.

В примере приложений с удаленным взаимодействием с устранением рисков Spectre (/Qspectre) включено устранение рисков в конфигурации выпуска.

если вы получаете *vccorlib. lib не удается открыть* неустранимую ошибку, убедитесь, что ваша рабочая нагрузка Visual Studio включает [библиотеки, снижающие опасность устранением рисков spectre](/cpp/build/reference/qspectre) .

## <a name="speech"></a>Речь

Проигрыватель holographic Remoting поддерживает наложение диагностики, которую можно включить, произнося ```Enable Diagnostics``` и отключая с помощью ```Disable Diagnostics``` . Если у вас возникли проблемы с этими голосовыми командами, можно также запустить проигрыватель holographic Remoting через веб-браузер, используя ```ms-holographic-remoting:?stats``` в качестве URL-адреса.

## <a name="h265-video-codec-not-available"></a>Кодек H265 Video недоступен

установите [Расширения для видео HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) при использовании видеокодека H265 в удаленном приложении. При возникновении проблем, когда кодек установлен, но не может использоваться, ознакомьтесь с руководством по [устранению неполадок](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) .

## <a name="limitations"></a>Ограничения

в настоящее время следующие api **не** поддерживаются при использовании удаленного взаимодействия holographic для HoloLens 2 и вызовут ```ERROR_NOT_SUPPORTED``` ошибку, если не указано иное:

[Windows.Graphics.Holographic](/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - Поддерживается начиная с версии [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - В предыдущих версиях всегда вызывает ошибку.
* [HolographicCamera.IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - Поддерживается начиная с версии [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - В предыдущих версиях не происходит сбой, но размер целевого объекта рендеринга не изменяется.
* [Холографиккамерапосе. Оверридепрожектионтрансформ](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [Холографиккамерапосе. Оверридевиевпорт](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [Холографиккамерапосе. Оверридевиевтрансформ](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - Поддерживается начиная с версии [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [Холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Петров.
  - Поддерживается начиная с версии [2.1.0](holographic-remoting-version-history.md#v2.1.0)
* [HolographicDisplay.TryGetViewConfiguration](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - Запрос Холографиквиевконфигуратионкинд. Фотовидеокамера всегда будет возвращать ```nullptr``` .
  - Поддерживается начиная с версии [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - В предыдущих версиях всегда вызывает ошибку.
* [Холографикспаце. Креатефрамепресентатионмонитор](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [Холографикдисплай. по умолчанию](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - Сообщает об ошибке, если она вызвана до установления соединения.


[Windows.Perception.Spatial](/uwp/api/windows.perception.spatial)

* [SpatialLocation. Абсолутеангуларакцелератион](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. АбсолутеангуларвелоЦити](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. Абсолутелинеаракцелератион](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. АбсолутелинеарвелоЦити](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [Спатиалстажефрамеофреференце. Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Поддерживается начиная с версии [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - В предыдущих версиях всегда возвращает ```nullptr``` .
* [Спатиалстажефрамеофреференце. Рекуестневстажеасинк](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - Поддерживается начиная с версии [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [Спатиаланчор. Ремоведбюсер](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - В предыдущих версиях всегда возвращает ```nullptr``` . 
* [SpatialAnchorExporter.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Поддерживается начиная с версии [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - В предыдущих версиях асинхронная операция всегда завершилась с ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [Спатиаланчортрансферманажер. Рекуестакцессасинк](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - Асинхронная операция всегда завершается с ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [Спатиаланчортрансферманажер. Трекспортанчорсасинк](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - Асинхронная операция всегда завершается с ```false``` .
* [Спатиаланчортрансферманажер. Тримпортанчорсасинк](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - Асинхронная операция всегда завершается с ```nullptr``` .

[Windows.UI.Input.Spatial](/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [Спатиалинтерактионсаурце. Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - Поддерживается начиная с версии [2.2.0](holographic-remoting-version-history.md#v2.2.0)

[Windows.Perception.Spatial.Preview](/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>См. также:
* [Журнал версий службы удаленного взаимодействия с holographic](holographic-remoting-version-history.md)
* [создание удаленного приложения holographic с удаленным взаимодействием с помощью Windows Mixed Reality api](holographic-remoting-create-remote-wmr.md)
* [Создание удаленного приложения holographic с удаленным взаимодействием с помощью API-интерфейсов Опенкср](holographic-remoting-create-remote-openxr.md)
* [Создание пользовательского проигрывателя для голографического удаленного взаимодействия](holographic-remoting-create-player.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)