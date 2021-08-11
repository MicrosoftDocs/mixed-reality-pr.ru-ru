---
title: Подключение нескольких пользователей
description: В рамках этого курса вы узнаете, как подключить нескольких пользователей в приложении смешанной реальности HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, многопользовательские возможности, Photon, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure
ms.localizationpriority: high
ms.openlocfilehash: ba8a29844489a9153f970f6e39ff2022701c845711ffd9abc232d8da8eeb2e32
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200740"
---
# <a name="3-connecting-multiple-users"></a>3. Подключение нескольких пользователей

Из этого учебника вы узнаете, как подключить несколько пользователей для организации совместного взаимодействия в реальном времени. По завершении работы с этим руководством вы сможете запустить приложение на нескольких устройствах, и каждый пользователь сможет увидеть, как аватар других пользователей перемещается в реальном времени.

## <a name="objectives"></a>Задачи

* Подключение нескольких пользователей к общему взаимодействию

## <a name="preparing-the-scene"></a>Подготовка сцены

В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.

В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Активы > MRTK.Tutorials.MultiUserCapabilities > Заготовки), а затем щелкните и перетащите следующие заготовки в окно Hierarchy (Иерархия), чтобы добавить их в сцену:

* заготовка **NetworkLobby**;
* заготовка **SharedPlayground**.

![Unity с добавленными заготовками NetworkLobby и SharedPlayground](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Активы > MRTK.Tutorials.AzureSpatialAnchors > Заготовки), а затем щелкните и перетащите следующие заготовки в окно Hierarchy (Иерархия), чтобы добавить их в сцену:

* заготовка **DebugWindow**.

![Unity с выбранной добавленной заготовкой DebugWindow](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Настройка PUN для создания заготовки пользователя

В рамках этого раздела вы настроите проект для использования заготовки PhotonUser.

В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).

В окне "Иерархия" разверните объект **NetworkLobby** и выберите дочерний объект **NetworkRoom**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.

* В поле **Photon User Prefab** (Заготовка пользователя Photon) укажите заготовку **PhotonUser** из папки Resources (Ресурсы).

![Unity с частично настроенным компонентом Photon Room](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Взаимодействие с несколькими пользователями

Если вы теперь создадите и развернете проект Unity в HoloLens, а затем вернетесь в Unity и во время выполнения приложения на устройстве HoloLens перейдете в игровой режим, вы увидите, как с движением вашей головы (HoloLens) перемещается аватар пользователя HoloLens.

![Анимация, показывающая Unity с сетевыми пользователями](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Сведения о том, как правильно скомпилировать проект Unity и развернуть его в HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!CAUTION]
> Этому приложению требуется подключение к Photon, поэтому не забудьте проверить подключение компьютера или устройства к Интернету.

## <a name="congratulations"></a>Поздравляем!

Вы успешно настроили проект. Теперь несколько пользователей могут подключаться к одному интерфейсу и просматривать перемещения друг друга. В следующем учебнике вы реализуете функциональность, чтобы предоставить общий доступ к перемещению объектов на нескольких устройствах.

> [!div class="nextstepaction"]
> [Следующее руководство: 4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям](mr-learning-sharing-04.md)
