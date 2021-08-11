---
title: Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям
description: В рамках этого курса вы узнаете, как предоставить доступ к движениям объектов нескольким пользователям в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, многопользовательские возможности, Photon, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure
ms.localizationpriority: high
ms.openlocfilehash: c9a37dd94083b796da6d5fba2727d739112e411b494af5882ad08525e733a722
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200791"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям

В этом руководстве показано, как совместно использовать перемещения объектов, чтобы все участники общего взаимодействия могли взаимодействовать друг с другом и наблюдать за этими процессами.

## <a name="objectives"></a>Задачи

* Настройка проекта для совместного использования перемещений объектов
* Создать простое многопользовательское приложение для совместной работы.

## <a name="preparing-the-scene"></a>Подготовка сцены

В рамках этого раздела вы подготовите сцену, добавив в нее заготовку для учебника.

В окне Hierarchy (Иерархия) разверните объект **MixedRealityPlayspace** и выберите дочерний объект **Main Camera** (Главная камера), а затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **AR Camera Manager (Script)** (Диспетчер камеры дополненной реальности (скрипт)) к объекту **Main Camera**:

![Unity с частично настроенным компонентом диспетчера камеры дополненной реальности](images/mr-learning-sharing/sharing-04-section1-step1-0.png)

В окне Project (Проект) перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Заготовки) и перетащите заготовку **TableAnchor** на объект **SharedPlayground** в окне Hierarchy (Иерархия), чтобы добавить ее в сцену в качестве дочернего элемента объекта SharedPlayground.

![Unity с выбранной созданной заготовкой TableAnchor](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

В окне Hierarchy (Иерархия) убедитесь, что объект **MixedRealityPlayspace** развернут, а объект **TableAnchor** выбран. Перетащите компонент **Main Camera** (Главная камера) в поле **Camera** (Камера) компонента **AR Session Origin** (Источник сеанса дополненной реальности) для **TableAnchor**:

![Unity с настроенным назначением главной камеры для источника сеанса дополненной реальности](images/mr-learning-sharing/sharing-04-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Настройка PUN для создания объектов

С помощью инструкций из этого раздела вы настроите в проекте использование взаимодействия Rover Explorer, созданного с помощью [руководств по началу работы](mr-learning-base-01.md), и определите расположение, в котором буде создан его экземпляр.

В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).

В окне "Иерархия" разверните объект **NetworkLobby** и выберите дочерний объект **NetworkRoom**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.

* В поле **Rover Explorer Prefab** (Заготовка Rover Explorer) назначьте заготовку **RoverExplorer_Complete_Variant** из папки Resources (Ресурсы).

![Unity с частично настроенным компонентом Photon Room](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

Сохраняя выделение объекта **NetworkRoom**, в окне "Иерархия" разверните объект **TableAnchor**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.

* В поле **Rover Explorer Location** (Расположение Rover Explorer) укажите дочерний объект TableAnchor > **Table** из окна Hierarchy (Иерархия).

![Unity с настроенным компонентом Photon Room](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Использование возможности общего перемещения объектов

Если вы теперь создадите и развернете проект Unity в HoloLens, а затем вернетесь в Unity и во время выполнения приложения на устройстве HoloLens нажмете кнопку Play (Играть), чтобы перейти в игровой режим, вы увидите, как при перемещении объекта в HoloLens перемещается объект в Unity.

![Анимация, показывающая Unity с сетевыми объектами](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>Поздравляем!

Вы успешно настроили проект. Теперь перемещения объектов синхронизированы и пользователи могут видеть, как перемещаются объекты, когда их перемещают другие пользователи. В следующем руководстве показано, как реализовать функциональность для согласования взаимодействия с физическим миром. Благодаря этому пользователи будут видеть друг друга в фактическом физическом расположении, а объекты будут отображаться в одном физическом расположении и с одним поворотом для всех пользователей.

> [!div class="nextstepaction"]
> [Следующее руководство: 5. Интеграция Пространственных привязок Azure в общий интерфейс](mr-learning-sharing-05.md)
