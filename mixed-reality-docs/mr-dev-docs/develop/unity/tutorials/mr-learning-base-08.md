---
title: Использование функции отслеживания взгляда
description: Из этого курса вы узнаете, как использовать отслеживание глаз в приложениях смешанной реальности в Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, отслеживание глаз
ms.localizationpriority: high
ms.openlocfilehash: 5efe1c54d9e3b4096dfec4221e4ce04e7370ca47
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635476"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="87c12-104">8. Использование функции отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="87c12-104">8. Using eye-tracking</span></span>

<span data-ttu-id="87c12-105">Из этого руководства вы узнаете, как включить функцию отслеживания взгляда для HoloLens 2 и добавить ее в объекты, чтобы активировать действия, когда пользователь смотрит на объекты.</span><span class="sxs-lookup"><span data-stu-id="87c12-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="87c12-106">Если вы также развертываете этот проект в HoloLens (1-е поколение), обратите внимание, что функция отслеживания взгляда поддерживается только в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="87c12-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="87c12-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="87c12-107">Objectives</span></span>

* <span data-ttu-id="87c12-108">Узнайте, как включить функцию отслеживания взгляда для HoleLens 2</span><span class="sxs-lookup"><span data-stu-id="87c12-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="87c12-109">Узнайте, как с помощью функции отслеживания взгляда активировать действие</span><span class="sxs-lookup"><span data-stu-id="87c12-109">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="87c12-110">Проверка того, включена ли функция ввода с использованием взгляда</span><span class="sxs-lookup"><span data-stu-id="87c12-110">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="87c12-111">В меню Unity последовательно выберите элементы Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Затем перейдите в раздел **UWP Capabilities** (Возможности UWP) и убедитесь, что раздел **Enable Eye Gaze Input Capability** (Включить ввод с использованием взгляда) выделен серым цветом.</span><span class="sxs-lookup"><span data-stu-id="87c12-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Окно конфигурации проекта MRTK в Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="87c12-113">Функция ввода с использованием взгляда должна была быть включена в ходе выполнения инструкций, приведенных в разделе [Применение параметров конфигуратора проекта MRTK](mr-learning-base-02.md#creating-and-configuring-the-scene), при настройке проекта Unity в начале работы с этой серией руководств.</span><span class="sxs-lookup"><span data-stu-id="87c12-113">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-and-configuring-the-scene) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="87c12-114">Если функция отключена, включите ее сейчас.</span><span class="sxs-lookup"><span data-stu-id="87c12-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="87c12-115">Включение отслеживания взгляда в поставщике данных о направлении взгляда</span><span class="sxs-lookup"><span data-stu-id="87c12-115">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="87c12-116">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, затем в окне Inspector (Инспектор) перейдите на вкладку MixedRealityToolkit > **Input** (Ввод) и выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="87c12-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="87c12-117">Клонируйте профиль **DefaultHoloLens2InputSystemProfile** и присвойте ему понятное имя, например _GettingStarted_HoloLens2InputSystemProfile_.</span><span class="sxs-lookup"><span data-stu-id="87c12-117">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="87c12-118">Разверните раздел **Pointers** (Указатели).</span><span class="sxs-lookup"><span data-stu-id="87c12-118">Expand the **Pointers** section</span></span>
* <span data-ttu-id="87c12-119">Клонируйте профиль **DefaultMixedRealityPointerProfile** и присвойте ему понятное имя, например _GettingStarted_MixedRealityPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="87c12-119">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="87c12-120">В разделе **Gaze Settings** (Параметры взгляда) установите флажок **Is Eye Tracking Enabled** (Включено отслеживание взгляда).</span><span class="sxs-lookup"><span data-stu-id="87c12-120">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Компонент MixedRealityToolkit в Unity с примененными созданными профилями и включенным отслеживанием глаз](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="87c12-122">Сведения о том, как правильно клонировать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="87c12-122">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="87c12-123">Включение имитации отслеживания взгляда для редактора Unity</span><span class="sxs-lookup"><span data-stu-id="87c12-123">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="87c12-124">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, в окне инспектора откройте вкладку **Input** (Ввод) и сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="87c12-124">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="87c12-125">Разверните раздел **Input Data Providers**  > **Input Simulation Service** (Поставщики входных данных > Служба имитации ввода).</span><span class="sxs-lookup"><span data-stu-id="87c12-125">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="87c12-126">Клонируйте профиль **DefaultMixedRealityInputSimulationProfile** и присвойте ему понятное имя, например _GettingStarted_MixedRealityInputSimulationProfile_.</span><span class="sxs-lookup"><span data-stu-id="87c12-126">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="87c12-127">Найдите раздел **Eye Gaze Simulation** (Имитация направления взгляда) и задайте для параметра **Default Eye Gaze Simulation Mode** (Режим имитации направления взгляда по умолчанию) значение **Camera Forward Axis** (Ось камеры, направленная вперед).</span><span class="sxs-lookup"><span data-stu-id="87c12-127">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![Unity с выбранным объектом TextMeshPro](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="87c12-129">Добавление функции отслеживания взгляда в объекты</span><span class="sxs-lookup"><span data-stu-id="87c12-129">Adding eye-tracking to objects</span></span>

<span data-ttu-id="87c12-130">В окне Hierarchy (Иерархия) разверните объект RoverExplorer > **Buttons** (Кнопки). Для каждого из трех дочерних объектов кнопок разверните и выберите объект SeeItSayItLabel > **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="87c12-130">In the Hierarchy window, expand the RoverExplorer > **Buttons** object, then for each of the three child button objects, expand and select the SeeItSayItLabel > **TextMeshPro** object:</span></span>

![Unity с выбранным объектом TextMeshPro](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="87c12-132">Выбрав три объекта TextMeshPro, в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить следующие компоненты ко всем выбранным объектам:</span><span class="sxs-lookup"><span data-stu-id="87c12-132">With the three TextMeshPro objects still selected, in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="87c12-133">компонент **Box Collider** (Прямоугольный коллайдер);</span><span class="sxs-lookup"><span data-stu-id="87c12-133">**Box Collider** component</span></span>
* <span data-ttu-id="87c12-134">компонент **EyeTrackingTarget**.</span><span class="sxs-lookup"><span data-stu-id="87c12-134">**EyeTrackingTarget** component</span></span>

![Unity с выбранным объектом TextMeshPro и добавленными компонентами](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="87c12-136">В окне Hierarchy (Иерархия) выберите объект **Hints** (Указания) > SeeItSayItLabel > **TextMeshPro**, а затем настройте компонент **EyeTrackingTarget** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="87c12-136">In the Hierarchy window, select the **Hints** > SeeItSayItLabel > **TextMeshPro** object, then configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="87c12-137">В разделе события **On Look At Start ()** (При взгляде на начало ())</span><span class="sxs-lookup"><span data-stu-id="87c12-137">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="87c12-138">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="87c12-138">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="87c12-139">Назначьте сам объект, т. е. тот же объект **TextMeshPro** полю **None (Object)** (Нет (объект)).</span><span class="sxs-lookup"><span data-stu-id="87c12-139">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="87c12-140">В раскрывающемся списке **No Function** (Нет функции) выберите **TextMeshPro** > **float fontSize**, чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="87c12-140">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="87c12-141">Задайте для аргумента значение **0,06**, чтобы увеличить текущий размер шрифта 0,04 на 50 %.</span><span class="sxs-lookup"><span data-stu-id="87c12-141">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="87c12-142">В разделе события **On Look At Start ()** (При отведении взгляда ())</span><span class="sxs-lookup"><span data-stu-id="87c12-142">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="87c12-143">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="87c12-143">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="87c12-144">Назначьте сам объект, т. е. тот же объект **TextMeshPro** полю **None (Object)** (Нет (объект)).</span><span class="sxs-lookup"><span data-stu-id="87c12-144">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="87c12-145">В раскрывающемся списке **No Function** (Нет функции) выберите **TextMeshPro** > **float fontSize**, чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="87c12-145">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="87c12-146">Задайте для аргумента значение **0,04**, чтобы сбросить размер шрифта обратно до значения 0,04.</span><span class="sxs-lookup"><span data-stu-id="87c12-146">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity с выбранным объектом TextMeshPro для Hints и настроенным компонентом EyeTrackingTarget](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="87c12-148">**Повторите** это действие для объекта **Explode** (Развернуть) > SeeItSayItLabel > **TextMeshPro** и объекта **Reset** (Сброс) > SeeItSayItLabel > **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="87c12-148">**Repeat** this step for the **Explode** > SeeItSayItLabel > **TextMeshPro** object and the **Reset** > SeeItSayItLabel > **TextMeshPro** object.</span></span>

<span data-ttu-id="87c12-149">Если теперь перейти в режим игры, а затем нажать и удерживать правую кнопку мыши при перемещении указателя мыши до тех пор, пока взгляд не достигнет одной из меток, вы увидите, что размер шрифта увеличится на 50 %. При отведении взгляда текст вернется к исходному размеру.</span><span class="sxs-lookup"><span data-stu-id="87c12-149">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the labels, you will see the font size increase by 50% and reset back to its original size when looking away:</span></span>

![Разделенное представление Unity в режиме воспроизведения с взглядом, направленным на метку кнопки Explode с отслеживанием взгляда](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="87c12-151">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="87c12-151">Congratulations</span></span>

<span data-ttu-id="87c12-152">Из этого руководства вы узнали, как включить функцию отслеживания взгляда для HoloLens 2 и добавить ее в объекты, чтобы активировать действия, когда пользователь смотрит на объекты.</span><span class="sxs-lookup"><span data-stu-id="87c12-152">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="87c12-153">Следующее руководство: 9. Использование речевых команд</span><span class="sxs-lookup"><span data-stu-id="87c12-153">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
