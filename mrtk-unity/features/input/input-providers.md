---
title: Поставщики входных данных
description: Документация по различным типам поставщиков входных данных в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 134ab9304a9fb56ff67dd52e46d030dec2ca4b4c8e528e2c51046fc60c1918f7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207652"
---
# <a name="input-providers"></a>Поставщики входных данных

поставщики входных данных зарегистрированы в **профиле зарегистрированных поставщиков служб**, который находится в компоненте набор средств смешанной реальности:

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

Это поставщики входных данных, доступные из комплекта, вместе с соответствующими контроллерами:

| Поставщик входных данных | Контроллеры |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | Имитация руки |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | Мышь  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | Generic опенвр, naopak палочка, naopak кнукклес, окулус Touch, окулус Remote, Windows Mixed Reality опенвр  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | Универсальный джойстик  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | Сенсорный контроллер Unity  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | *None*  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | ВМРая рука, ВМР контроллер, ВМР ГГВ (взгляд, жест и речь) |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | *None* |

Поставщики диктовки и речи не создают контроллеры, они создают собственные специализированные события ввода.

Пользовательские поставщики входных данных могут быть созданы путем реализации [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) интерфейса.

Дополнительные сведения см. в разделе [Создание входного системного поставщика данных](create-data-provider.md).
