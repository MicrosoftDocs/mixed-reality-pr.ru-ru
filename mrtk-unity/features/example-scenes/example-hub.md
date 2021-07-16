---
title: Центр с примерами MRTK
description: Обзор примера сцен в МРТК
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: b7a55e46b2c283b5a75395b9e99874af6020a171
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282007"
---
# <a name="mrtk-examples-hub"></a><span data-ttu-id="ab869-104">Центр с примерами MRTK</span><span class="sxs-lookup"><span data-stu-id="ab869-104">MRTK Examples Hub</span></span>

![Центр с примерами MRTK](../images/examples-hub/MRTK_ExamplesHub.png)

<span data-ttu-id="ab869-106">Центр примеров МРТК — это сцена Unity, которая упрощает работу в нескольких сценах.</span><span class="sxs-lookup"><span data-stu-id="ab869-106">MRTK Examples Hub is a Unity scene that makes it easy to experience multiple scenes.</span></span> <span data-ttu-id="ab869-107">Для загрузки & выгрузки сцены используется система сцены МРТК.</span><span class="sxs-lookup"><span data-stu-id="ab869-107">It uses MRTK's Scene System to load & unload the scenes.</span></span>

<span data-ttu-id="ab869-108">**Мрткексамплешуб. Unity** — это сцена контейнера, в которой есть общие компоненты, включая ``MixedRealityToolkit`` и ``MixedRealityPlayspace`` .</span><span class="sxs-lookup"><span data-stu-id="ab869-108">**MRTKExamplesHub.unity** is the container scene that has shared components including ``MixedRealityToolkit`` and ``MixedRealityPlayspace``.</span></span> <span data-ttu-id="ab869-109">В сцене **мрткексамплешубмаинмену. Unity** есть кнопки Куба.</span><span class="sxs-lookup"><span data-stu-id="ab869-109">**MRTKExamplesHubMainMenu.unity** scene has the cube buttons.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="ab869-110">Предварительное требование</span><span class="sxs-lookup"><span data-stu-id="ab869-110">Prerequisite</span></span>

<span data-ttu-id="ab869-111">В центре примеров МРТК используется [Служба переходов сцены](../extensions/scene-transition-service.md) и связанные сценарии.</span><span class="sxs-lookup"><span data-stu-id="ab869-111">MRTK Examples Hub uses [Scene Transition Service](../extensions/scene-transition-service.md) and related scripts.</span></span> <span data-ttu-id="ab869-112">если вы используете мртк через пакеты Unity, импортируйте **Microsoft. микседреалити. набор средств. Unity. Extensions. x. x. x. пакет unitypackage** , который является частью [пакетов выпуска](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="ab869-112">If you are using MRTK through Unity packages, please import **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** which is part of the [release packages](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="ab869-113">Если вы используете МРТК через клон репозитория, в проекте уже должна быть папка **мртк/Extensions** .</span><span class="sxs-lookup"><span data-stu-id="ab869-113">If you are using MRTK through the repository clone, you should already have the **MRTK/Extensions** folder in your project.</span></span>

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a><span data-ttu-id="ab869-114">Мрткексамплешуб сцены и система сцен</span><span class="sxs-lookup"><span data-stu-id="ab869-114">MRTKExamplesHub scene and the scene system</span></span>

<span data-ttu-id="ab869-115">Открытый **мрткексамплешуб. Unity** `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` — это пустая сцена с микседреалититулкит, микседреалитиплайспаце и лоадхубонстартуп.</span><span class="sxs-lookup"><span data-stu-id="ab869-115">Open **MRTKExamplesHub.unity** which is located at `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` It is an empty scene with MixedRealityToolkit, MixedRealityPlayspace and LoadHubOnStartup.</span></span> <span data-ttu-id="ab869-116">Эта сцена настроена для использования системы сцены МРТК.</span><span class="sxs-lookup"><span data-stu-id="ab869-116">This scene is configured to use MRTK's Scene System.</span></span> <span data-ttu-id="ab869-117">Щелкните `MixedRealitySceneSystem` в разделе микседреалититулкит.</span><span class="sxs-lookup"><span data-stu-id="ab869-117">Click `MixedRealitySceneSystem` under MixedRealityToolkit.</span></span> <span data-ttu-id="ab869-118">На панели инспектора отображаются сведения о системе сцены.</span><span class="sxs-lookup"><span data-stu-id="ab869-118">It will display the Scene System's information in the Inspector panel.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

<span data-ttu-id="ab869-119">В нижней части инспектора отображается список сцен, определенных в системном профиле сцены.</span><span class="sxs-lookup"><span data-stu-id="ab869-119">On the bottom of the Inspector, it displays the list of the scenes defined in the Scene System Profile.</span></span> <span data-ttu-id="ab869-120">Чтобы загрузить или выгрузить их, можно щелкнуть имена сцен.</span><span class="sxs-lookup"><span data-stu-id="ab869-120">You can click the scene names to load/unload them.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3"><span data-ttu-id="ab869-121">Пример загрузки сцены _мрткексамплешуб_ , щелкнув имя сцены в списке.</span><span class="sxs-lookup"><span data-stu-id="ab869-121">Example of loading _MRTKExamplesHub_ scene by clicking the scene name in the list.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4"><span data-ttu-id="ab869-122">Пример загрузки сцены _хандинтерактионексамплес_ .</span><span class="sxs-lookup"><span data-stu-id="ab869-122">Example of loading _HandInteractionExamples_ scene.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
<span data-ttu-id="ab869-123">Пример загрузки нескольких сцен.</span><span class="sxs-lookup"><span data-stu-id="ab869-123">Example of loading multiple scenes.</span></span>

## <a name="running-the-scene"></a><span data-ttu-id="ab869-124">Запуск сцены</span><span class="sxs-lookup"><span data-stu-id="ab869-124">Running the scene</span></span>

<span data-ttu-id="ab869-125">Сцена работает как в игровом режиме Unity, так и на устройстве.</span><span class="sxs-lookup"><span data-stu-id="ab869-125">The scene works in both Unity's game mode and on device.</span></span> <span data-ttu-id="ab869-126">Запустите сцену **мрткексамплешуб** в редакторе Unity и используйте имитацию ввода мртк для взаимодействия с содержимым сцены.</span><span class="sxs-lookup"><span data-stu-id="ab869-126">Run the **MRTKExamplesHub** scene in the Unity editor and use MRTK's input simulation to interact with the scene contents.</span></span> <span data-ttu-id="ab869-127">Для сборки и развертывания просто создайте **мрткексамплешуб** сцену с другими сценами, которые включены в список системы сцены.</span><span class="sxs-lookup"><span data-stu-id="ab869-127">To build and deploy, simply build **MRTKExamplesHub** scene with other scenes that are included in the Scene System's list.</span></span> <span data-ttu-id="ab869-128">инспектор также упрощает добавление сцен в Параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="ab869-128">The inspector also makes it easy to add scenes to the Build Settings.</span></span> <span data-ttu-id="ab869-129">в Параметры сборки убедитесь, что сцена **мрткексамплешуб** находится в верхней части списка с индексом 0.</span><span class="sxs-lookup"><span data-stu-id="ab869-129">In the Building Settings, make sure **MRTKExamplesHub** scene is on the top of the list at index 0.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a><span data-ttu-id="ab869-130">Как Мрткексамплешуб загружает сцену</span><span class="sxs-lookup"><span data-stu-id="ab869-130">How MRTKExamplesHub loads a scene</span></span>

<span data-ttu-id="ab869-131">В сцене **мрткексамплешуб** можно найти ``ExamplesHubButton`` prefab.</span><span class="sxs-lookup"><span data-stu-id="ab869-131">In the **MRTKExamplesHub** scene, you can find the ``ExamplesHubButton`` prefab.</span></span>
<span data-ttu-id="ab869-132">В prefab содержится объект **фронтплате** , содержащий ``Interactable`` .</span><span class="sxs-lookup"><span data-stu-id="ab869-132">There is a **FrontPlate** object in the prefab which contains ``Interactable``.</span></span>
<span data-ttu-id="ab869-133">Используя взаимодействующее ``OnClick()`` событие и ``OnTouch()`` , оно запускает функцию **LoadContent ()** скрипта **лоадконтентсцене** .</span><span class="sxs-lookup"><span data-stu-id="ab869-133">Using the Interactable's ``OnClick()`` and ``OnTouch()`` event, it triggers the **LoadContentScene** script's **LoadContent()** function.</span></span>
<span data-ttu-id="ab869-134">В инспекторе сценария **лоадконтентсцене** можно определить имя сцены для загрузки.</span><span class="sxs-lookup"><span data-stu-id="ab869-134">In the **LoadContentScene** script's Inspector, you can define the scene name to load.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

<span data-ttu-id="ab869-135">Для загрузки сцены скрипт использует функцию LoadContent () в системе сцены.</span><span class="sxs-lookup"><span data-stu-id="ab869-135">The script uses the Scene System's LoadContent() function to load the scene.</span></span>
<span data-ttu-id="ab869-136">Дополнительные сведения см. на странице " [сцена](../scene-system/scene-system-getting-started.md) ".</span><span class="sxs-lookup"><span data-stu-id="ab869-136">Please refer to the [Scene System](../scene-system/scene-system-getting-started.md) page for more details.</span></span>

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a><span data-ttu-id="ab869-137">Возвращение в основную сцену меню</span><span class="sxs-lookup"><span data-stu-id="ab869-137">Returning to the main menu scene</span></span>

<span data-ttu-id="ab869-138">Чтобы вернуться к основной сцене меню (Мрткексамплешубмаинмену сцена), можно использовать тот же метод системы сцены `LoadContent()` .</span><span class="sxs-lookup"><span data-stu-id="ab869-138">To return to the main menu scene (MRTKExamplesHubMainMenu scene), you can use the same Scene System `LoadContent()` method.</span></span> <span data-ttu-id="ab869-139">**Тогглефеатуреспанелексамплешуб. prefab** предоставляет кнопку Home, которая содержит скрипт **лоадконтентсцене** .</span><span class="sxs-lookup"><span data-stu-id="ab869-139">The **ToggleFeaturesPanelExamplesHub.prefab** provides the 'Home' button which contains the **LoadContentScene** script.</span></span> <span data-ttu-id="ab869-140">Используйте этот prefab или предоставьте пользовательскую кнопку Home в каждой сцене, чтобы пользователь возвращался в основную сцену.</span><span class="sxs-lookup"><span data-stu-id="ab869-140">Use this prefab or provide a custom home button in each scene to allow the user to return to the main scene.</span></span> <span data-ttu-id="ab869-141">Можно поместить **тогглефеатуреспанелексамплешуб. prefab** в сцене **мрткексамплешуб** , чтобы сделать его всегда видимым, так как **мрткексамплешуб** — это общая сцена контейнера.</span><span class="sxs-lookup"><span data-stu-id="ab869-141">One can put the **ToggleFeaturesPanelExamplesHub.prefab** in the **MRTKExamplesHub** scene to make it always visible since **MRTKExamplesHub** is a shared container scene.</span></span> <span data-ttu-id="ab869-142">Не забудьте скрыть или деактивировать **тогглефеатуреспанел. prefab** в каждом примере сцены.</span><span class="sxs-lookup"><span data-stu-id="ab869-142">Make sure to hide/deactivate **ToggleFeaturesPanel.prefab** in each example scene.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a><span data-ttu-id="ab869-143">Добавление дополнительных кнопок</span><span class="sxs-lookup"><span data-stu-id="ab869-143">Adding additional buttons</span></span>

<span data-ttu-id="ab869-144">В объекте **кубеколлектион** создайте дубликат (или добавьте) _ексамплехуббуттон_ Prefabs и щелкните **Update Collection (обновить коллекцию** ) в `GridObjectCollection` .</span><span class="sxs-lookup"><span data-stu-id="ab869-144">In the **CubeCollection** object, duplicate (or add) _ExampleHubButton_ prefabs and click **Update Collection** in the `GridObjectCollection`.</span></span>
<span data-ttu-id="ab869-145">Это приведет к обновлению макета цилиндра на основе нового общего числа кнопок.</span><span class="sxs-lookup"><span data-stu-id="ab869-145">This will update the cylinder layout based on the new total number of buttons.</span></span>
<span data-ttu-id="ab869-146">Дополнительные сведения см. на странице [коллекции объектов](../ux-building-blocks/object-collection.md) .</span><span class="sxs-lookup"><span data-stu-id="ab869-146">Please refer to the [Object Collection](../ux-building-blocks/object-collection.md) page for more details.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

<span data-ttu-id="ab869-147">После добавления кнопок обновите имя сцены в скрипте **лоадконтентсцене** (описанном выше).</span><span class="sxs-lookup"><span data-stu-id="ab869-147">After adding the buttons, update the scene name in the **LoadContentScene** script(explained above).</span></span>
<span data-ttu-id="ab869-148">Добавьте дополнительные сцены в профиль системы сцены.</span><span class="sxs-lookup"><span data-stu-id="ab869-148">Add additional scenes to the Scene System's profile.</span></span>
