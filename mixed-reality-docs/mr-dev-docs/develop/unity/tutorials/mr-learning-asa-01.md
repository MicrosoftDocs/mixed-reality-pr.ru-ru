---
title: Знакомство с руководствами по Пространственным привязкам Azure
description: Пройдите этот курс и узнайте, как реализовать Пространственные привязки Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure, iOS, Android, Windows 10, ARCore, macOS, Android Build Support, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 2d664c79c0e2d111dc4a0b7b449399682cda1f06
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403455"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a>1. Знакомство с руководствами по Пространственным привязкам Azure

Добро пожаловать в руководства по Пространственным привязкам Azure! Из этой серии руководств вы узнаете о <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Пространственных привязках Azure</a> (ASA) и о том, как использовать возможности смешанной реальности в реальном мире. Вы также узнаете, как развернуть проект в Android и iOS.

Руководства в этой серии:

1. [Введение](mr-learning-asa-01.md) (вы уже здесь)
2. [Начало работы с Пространственными привязками Azure](mr-learning-asa-02.md)
3. [Сохранение, получение и совместное использование Пространственных привязок Azure](mr-learning-asa-03.md)
4. [Отображение сведений о Пространственных привязках Azure](mr-learning-asa-04.md)
5. [Пространственные привязки Azure для Android и iOS](mr-learning-asa-05.md)

## <a name="objectives"></a>Задачи

* Узнать, как создавать пространственные привязки и получать их из Azure.
* Узнать, как обеспечить пространственное выравнивание в сеансах приложения.
* Узнать, как реализовать пространственное выравнивание на нескольких устройствах.
* Узнать, как подготовить, создать и развернуть проект в Android и iOS.

## <a name="prerequisites"></a>Предварительные условия

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2020/2019 LTS и модулем поддержки сборки универсальной платформы Windows
* Выполненные инструкции из раздела [Создание ресурса Пространственных привязок](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) статьи [Краткое руководство. Создание приложения Unity HoloLens, которое использует Пространственные привязки Azure](/azure/spatial-anchors/quickstarts/get-started-unity-hololens).
* Знакомство с серией [руководств по началу работы](mr-learning-base-01.md) или базовый опыт работы с Unity и MRTK.
* Если планируется развертывание на устройствах Android и HoloLens
  * Устройство Android с <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">включенными возможностями разработки</a> и <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">поддержкой ARCore</a>, подключенное через USB к компьютеру Windows или macOS.
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2020/2019 LTS и модулем Android Build Support.
* Если планируется развертывание на устройствах iOS и HoloLens
  * Компьютер macOS с последней версией <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> и <a href="https://cocoapods.org" target="_blank">CocoaPods</a>.
  * <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">Совместимое с ARKit</a> устройство iOS, подключенное через USB к компьютеру macOS.
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2020/2019 LTS и модулем iOS Build Support.

> [!Important]
> В этой серии руководств учитывается поддержка Unity 2020 LTS (в настоящее время 2020.3.x), если вы используете Open XR или подключаемый модуль Windows XR, а также Unity 2019 LTS (в настоящее время 2019.4.x), если вы используете устаревшую версию WSA. Это заменяет все требования к версии Unity, указанные выше.

> [!div class="nextstepaction"]
> [Следующее руководство: 2. Начало работы с Пространственными привязками Azure](mr-learning-asa-02.md)
