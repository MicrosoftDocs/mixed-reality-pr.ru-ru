---
title: Центр примеров
description: Обзор примера сцен в МРТК
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 212fc6e1489a22995241368a9bf4db96d206c44a
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144750"
---
# <a name="mrtk-examples-hub"></a>Центр примеров МРТК

![Центр примеров МРТК](../images/examples-hub/MRTK_ExamplesHub.png)

Центр примеров МРТК — это сцена Unity, которая упрощает работу в нескольких сценах. Для загрузки & выгрузки сцены используется система сцены МРТК.

**Мрткексамплешуб. Unity** — это сцена контейнера, в которой есть общие компоненты, включая ``MixedRealityToolkit`` и ``MixedRealityPlayspace`` . В сцене **мрткексамплешубмаинмену. Unity** есть кнопки Куба.

## <a name="prerequisite"></a>Предварительное требование

В центре примеров МРТК используется [Служба переходов сцены](../extensions/scene-transition-service.md) и связанные сценарии. Если вы используете МРТК через пакеты Unity, импортируйте **Microsoft. микседреалити. Toolkit. Unity. Extensions. x. x. x. пакет unitypackage** , который входит в состав [пакетов выпуска](https://github.com/microsoft/MixedRealityToolkit-Unity/releases). Если вы используете МРТК через клон репозитория, в проекте уже должна быть папка **мртк/Extensions** .

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>Мрткексамплешуб сцены и система сцен

Открытый **мрткексамплешуб. Unity** `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` — это пустая сцена с микседреалититулкит, микседреалитиплайспаце и лоадхубонстартуп. Эта сцена настроена для использования системы сцены МРТК. Щелкните `MixedRealitySceneSystem` в разделе микседреалититулкит. На панели инспектора отображаются сведения о системе сцены.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

В нижней части инспектора отображается список сцен, определенных в системном профиле сцены. Чтобы загрузить или выгрузить их, можно щелкнуть имена сцен.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">Пример загрузки сцены _мрткексамплешуб_ , щелкнув имя сцены в списке.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">Пример загрузки сцены _хандинтерактионексамплес_ .
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
Пример загрузки нескольких сцен.

## <a name="running-the-scene"></a>Запуск сцены

Сцена работает как в игровом режиме Unity, так и на устройстве. Запустите сцену **мрткексамплешуб** в редакторе Unity и используйте имитацию ввода мртк для взаимодействия с содержимым сцены. Для сборки и развертывания просто создайте **мрткексамплешуб** сцену с другими сценами, которые включены в список системы сцены. Инспектор также упрощает добавление сцен в параметры сборки. В параметрах здания убедитесь, что **мрткексамплешуб** сцена находится в верхней части списка с индексом 0.

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>Как Мрткексамплешуб загружает сцену

В сцене **мрткексамплешуб** можно найти ``ExamplesHubButton`` prefab.
В prefab содержится объект **фронтплате** , содержащий ``Interactable`` .
Используя взаимодействующее ``OnClick()`` событие и ``OnTouch()`` , оно запускает функцию **LoadContent ()** скрипта **лоадконтентсцене** .
В инспекторе сценария **лоадконтентсцене** можно определить имя сцены для загрузки.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

Для загрузки сцены скрипт использует функцию LoadContent () в системе сцены.
Дополнительные сведения см. на странице " [сцена](../scene-system/scene-system-getting-started.md) ".

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>Возвращение в основную сцену меню

Чтобы вернуться к основной сцене меню (Мрткексамплешубмаинмену сцена), можно использовать тот же метод системы сцены `LoadContent()` . **Тогглефеатуреспанелексамплешуб. prefab** предоставляет кнопку Home, которая содержит скрипт **лоадконтентсцене** . Используйте этот prefab или предоставьте пользовательскую кнопку Home в каждой сцене, чтобы пользователь возвращался в основную сцену. Можно поместить **тогглефеатуреспанелексамплешуб. prefab** в сцене **мрткексамплешуб** , чтобы сделать его всегда видимым, так как **мрткексамплешуб** — это общая сцена контейнера. Не забудьте скрыть или деактивировать **тогглефеатуреспанел. prefab** в каждом примере сцены.

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>Добавление дополнительных кнопок

В объекте **кубеколлектион** создайте дубликат (или добавьте) _ексамплехуббуттон_ Prefabs и щелкните **Update Collection (обновить коллекцию** ) в `GridObjectCollection` .
Это приведет к обновлению макета цилиндра на основе нового общего числа кнопок.
Дополнительные сведения см. на странице [коллекции объектов](../ux-building-blocks/object-collection.md) .

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

После добавления кнопок обновите имя сцены в скрипте **лоадконтентсцене** (описанном выше).
Добавьте дополнительные сцены в профиль системы сцены.
