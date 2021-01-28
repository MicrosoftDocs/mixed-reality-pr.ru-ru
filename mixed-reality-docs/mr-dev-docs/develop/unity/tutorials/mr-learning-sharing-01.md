---
title: Введение в руководства по многопользовательским возможностям
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, многопользовательские возможности, Photon, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure
ms.localizationpriority: high
ms.openlocfilehash: c18bd7c10ed042278053a51c2d1894564000dfe2
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699023"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a>1. Введение в руководства по многопользовательским возможностям

Приветствуем в руководствах по многопользовательским возможностям! Из этой серии руководств вы узнаете об основных принципах создания многопользовательских взаимодействий с помощью <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN). PUN — это одна из нескольких сетевых платформ, на основе которых разработчики смешанной реальности могут создавать совместные взаимодействия.

Руководства в этой серии:

* [Настройка Photon Unity Networking](mr-learning-sharing-02.md)
* [Подключение нескольких пользователей](mr-learning-sharing-03.md)
* [Предоставление разным пользователям общего доступа к перемещениям объекта](mr-learning-sharing-04.md)
* [Интеграция Пространственных привязок Azure в общее взаимодействие](mr-learning-sharing-05.md)

## <a name="objectives"></a>Задачи

* Узнать, как создать приложение PUN и подключить к нему проект Unity.
* Подключение нескольких пользователей к общему взаимодействию
* Узнать, как предоставлять разным пользователям общий доступ к перемещениям объекта.
* Узнать, как реализовать пространственное выравнивание на нескольких устройствах.

## <a name="prerequisites"></a>Предварительные условия

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019 LTS и модулем поддержки сборки универсальной платформы Windows
* Выполненные инструкции из раздела [Создание ресурса Пространственных привязок](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) статьи [Краткое руководство. Создание приложения Unity HoloLens, которое использует Пространственные привязки Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).
* Знакомство с серией [руководств по началу работы](mr-learning-base-01.md) или базовый опыт работы с Unity и MRTK.
* Знакомство с серией [руководств по Пространственным привязкам Azure](mr-learning-asa-01.md) или опыт создания учетной записи Пространственных привязок Azure.
* Если планируется развертывание на устройствах Android и HoloLens
  * Устройство Android с <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">включенными возможностями разработки</a> и <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">поддержкой ARCore</a>, подключенное через USB к компьютеру Windows или macOS.
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019 LTS и модулем Android Build Support.
* Если планируется развертывание на устройствах iOS и HoloLens
  * Компьютер macOS с последней версией <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> и <a href="https://cocoapods.org" target="_blank">CocoaPods</a>.
  * <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">Совместимое с ARKit</a> устройство iOS, подключенное через USB к компьютеру macOS.
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019 LTS и модулем iOS Build Support.

> [!CAUTION]
> Рекомендуемая версия набора средств для смешанной реальности для этой серии учебников — MRTK 2.5.1.

> [!CAUTION]
> Рекомендуемая версия Unity для этой серии учебников — Unity 2019 LTS. Это заменяет все требования к версии Unity, указанные в приведенных выше предварительных требованиях.

> [!div class="nextstepaction"]
> [Следующее руководство: 2. Настройка Photon Unity Networking](mr-learning-sharing-02.md)
