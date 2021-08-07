---
title: Центр с примерами MRTK
description: Обзор примера сцен в МРТК
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 6f86a7b6469a8dc7f6253d81f8cf647fbcfe35830fa8cf044066ba8ae9c5a286
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209302"
---
# <a name="mrtk-examples-hub"></a>Центр с примерами MRTK

![Центр с примерами MRTK](../images/examples-hub/MRTK_ExamplesHub.png)

Центр примеров МРТК — это сцена Unity, которая упрощает работу в нескольких сценах. Для загрузки & выгрузки сцены используется система сцены МРТК.

**Мрткексамплешуб. Unity** — это сцена контейнера, в которой есть общие компоненты, включая ``MixedRealityToolkit`` и ``MixedRealityPlayspace`` . В сцене **мрткексамплешубмаинмену. Unity** есть кнопки Куба.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>скачать приложение из Microsoft Store в HoloLens 2
если у вас HoloLens 2 устройство, вы можете напрямую скачать и установить приложение на устройстве.

<a href='//www.microsoft.com/store/apps/9mv8c39l2sj4?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="prerequisite"></a>Предварительное требование

В центре примеров МРТК используется [Служба переходов сцены](../extensions/scene-transition-service.md) и связанные сценарии. если вы используете мртк через пакеты Unity, импортируйте **Microsoft. микседреалити. набор средств. Unity. Extensions. x. x. x. пакет unitypackage** , который является частью [пакетов выпуска](https://github.com/microsoft/MixedRealityToolkit-Unity/releases). Если вы используете МРТК через клон репозитория, в проекте уже должна быть папка **мртк/Extensions** .

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

Сцена работает как в игровом режиме Unity, так и на устройстве. Запустите сцену **мрткексамплешуб** в редакторе Unity и используйте имитацию ввода мртк для взаимодействия с содержимым сцены. Для сборки и развертывания просто создайте **мрткексамплешуб** сцену с другими сценами, которые включены в список системы сцены. инспектор также упрощает добавление сцен в Параметры сборки. в Параметры сборки убедитесь, что сцена **мрткексамплешуб** находится в верхней части списка с индексом 0.

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
