---
title: Поставщики входных данных
description: Документация по различным типам поставщиков входных данных в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145262"
---
# <a name="input-providers"></a>Поставщики входных данных

Поставщики входных данных регистрируются в **профиле зарегистрированных поставщиков служб**, который находится в компоненте набора средств Mixed Reality:

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

Это поставщики входных данных, доступные из комплекта, вместе с соответствующими контроллерами:

| Поставщик входных данных | Контроллеры |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | Имитация руки |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | Мышь  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | Generic Опенвр, Naopak палочка, Naopak Кнукклес, Окулус Touch, Окулус Remote, Windows Mixed Reality Опенвр  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | Универсальный джойстик  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | Сенсорный контроллер Unity  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | *Нет*  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | ВМРая рука, ВМР контроллер, ВМР ГГВ (взгляд, жест и речь) |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | *Нет* |

Поставщики диктовки и речи не создают контроллеры, они создают собственные специализированные события ввода.

Пользовательские поставщики входных данных могут быть созданы путем реализации [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) интерфейса.

Дополнительные сведения см. в разделе [Создание входного системного поставщика данных](create-data-provider.md).
