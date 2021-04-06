---
title: Использование функции отслеживания взгляда
description: Из этого курса вы узнаете, как использовать отслеживание глаз в приложениях смешанной реальности в Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, отслеживание глаз
ms.localizationpriority: high
ms.openlocfilehash: bf7bd266eb471193979c588d97d14dd37aed175e
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982901"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="1c72f-104">8. Использование функции отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="1c72f-104">8. Using eye-tracking</span></span>

<span data-ttu-id="1c72f-105">Из этого руководства вы узнаете, как включить функцию отслеживания взгляда для HoloLens 2 и добавить ее в объекты, чтобы активировать действия, когда пользователь смотрит на объекты.</span><span class="sxs-lookup"><span data-stu-id="1c72f-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="1c72f-106">Если вы также развертываете этот проект в HoloLens (1-е поколение), обратите внимание, что функция отслеживания взгляда поддерживается только в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1c72f-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="1c72f-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="1c72f-107">Objectives</span></span>

* <span data-ttu-id="1c72f-108">Узнайте, как включить функцию отслеживания взгляда для HoleLens 2</span><span class="sxs-lookup"><span data-stu-id="1c72f-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="1c72f-109">Узнайте, как с помощью функции отслеживания взгляда активировать действие</span><span class="sxs-lookup"><span data-stu-id="1c72f-109">Learn how to use eye-tracking to trigger action</span></span>

[!INCLUDE[](includes/ensuring-eye-gaze-capabality.md)]

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="1c72f-110">Включение отслеживания взгляда в поставщике данных о направлении взгляда</span><span class="sxs-lookup"><span data-stu-id="1c72f-110">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="1c72f-111">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, затем в окне Inspector (Инспектор) перейдите на вкладку MixedRealityToolkit > **Input** (Ввод) и выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="1c72f-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="1c72f-112">Клонируйте профиль **DefaultHoloLens2InputSystemProfile** и присвойте ему понятное имя, например _GettingStarted_HoloLens2InputSystemProfile_.</span><span class="sxs-lookup"><span data-stu-id="1c72f-112">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="1c72f-113">Разверните раздел **Pointers** (Указатели).</span><span class="sxs-lookup"><span data-stu-id="1c72f-113">Expand the **Pointers** section</span></span>
* <span data-ttu-id="1c72f-114">Клонируйте профиль **DefaultMixedRealityPointerProfile** и присвойте ему понятное имя, например _GettingStarted_MixedRealityPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="1c72f-114">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="1c72f-115">В разделе **Gaze Settings** (Параметры взгляда) установите флажок **Is Eye Tracking Enabled** (Включено отслеживание взгляда).</span><span class="sxs-lookup"><span data-stu-id="1c72f-115">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Компонент MixedRealityToolkit в Unity с примененными созданными профилями и включенным отслеживанием глаз](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="1c72f-117">Сведения о том, как правильно клонировать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="1c72f-117">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="1c72f-118">Включение имитации отслеживания взгляда для редактора Unity</span><span class="sxs-lookup"><span data-stu-id="1c72f-118">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="1c72f-119">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, в окне инспектора откройте вкладку **Input** (Ввод) и сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="1c72f-119">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="1c72f-120">Разверните раздел **Input Data Providers**  > **Input Simulation Service** (Поставщики входных данных > Служба имитации ввода).</span><span class="sxs-lookup"><span data-stu-id="1c72f-120">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="1c72f-121">Клонируйте профиль **DefaultMixedRealityInputSimulationProfile** и присвойте ему понятное имя, например _GettingStarted_MixedRealityInputSimulationProfile_.</span><span class="sxs-lookup"><span data-stu-id="1c72f-121">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="1c72f-122">Найдите раздел **Eye Gaze Simulation** (Имитация направления взгляда) и задайте для параметра **Default Eye Gaze Simulation Mode** (Режим имитации направления взгляда по умолчанию) значение **Camera Forward Axis** (Ось камеры, направленная вперед).</span><span class="sxs-lookup"><span data-stu-id="1c72f-122">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![Unity с выбранным объектом TextMeshPro](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="1c72f-124">Добавление функции отслеживания взгляда в объекты</span><span class="sxs-lookup"><span data-stu-id="1c72f-124">Adding eye-tracking to objects</span></span>

<span data-ttu-id="1c72f-125">В окне Hierarchy (Иерархия) разверните **RoverExplorer** > **Buttons (Кнопки)** и выберите все три дочерних объекта кнопки:</span><span class="sxs-lookup"><span data-stu-id="1c72f-125">In the Hierarchy window, expand the **RoverExplorer** > **Buttons**, then select all three of the child button objects:</span></span>

![Unity с выбранным объектом Button](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="1c72f-127">Выбрав три объекта Button, в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **EyeTrackingTarget** ко всем выбранным объектам:</span><span class="sxs-lookup"><span data-stu-id="1c72f-127">With all three Button objects still selected, in the Inspector window use the **Add Component** button to add the **EyeTrackingTarget** component to all the selected objects:</span></span>

![Unity с выбранным объектом TextMeshPro и добавленными компонентами](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="1c72f-129">В окне Hierarchy (Иерархия) разверните **RoverExplorer** > **Buttons (Кнопки)**  > **Hints (Подсказки)**  > **SeeItSayItLabel** > **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="1c72f-129">In the Hierarchy window, expand **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro**</span></span>

<span data-ttu-id="1c72f-130">Затем в окне Hierarchy (Иерархия) выберите объект кнопки **Hints** (Советы) и настройте компонент **EyeTrackingTarget** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1c72f-130">Then in the Hierarchy window, select the **Hints** button object , and configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="1c72f-131">В разделе события **On Look At Start ()** (При взгляде на начало ())</span><span class="sxs-lookup"><span data-stu-id="1c72f-131">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="1c72f-132">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="1c72f-132">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="1c72f-133">Назначьте объект **TextMeshPro** от кнопки **Hints** (Советы) полю **None (Object)** (Нет (объект)).</span><span class="sxs-lookup"><span data-stu-id="1c72f-133">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="1c72f-134">В раскрывающемся списке **No Function** (Нет функции) выберите **TextMeshPro** > **float fontSize**, чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="1c72f-134">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="1c72f-135">Задайте для аргумента значение **0,06**, чтобы увеличить текущий размер шрифта 0,04 на 50 %.</span><span class="sxs-lookup"><span data-stu-id="1c72f-135">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="1c72f-136">В разделе события **On Look At Start ()** (При отведении взгляда ())</span><span class="sxs-lookup"><span data-stu-id="1c72f-136">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="1c72f-137">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="1c72f-137">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="1c72f-138">Назначьте объект **TextMeshPro** от кнопки **Hints** (Советы) полю **None (Object)** (Нет (объект)).</span><span class="sxs-lookup"><span data-stu-id="1c72f-138">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="1c72f-139">В раскрывающемся списке **No Function** (Нет функции) выберите **TextMeshPro** > **float fontSize**, чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="1c72f-139">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="1c72f-140">Задайте для аргумента значение **0,04**, чтобы сбросить размер шрифта обратно до значения 0,04.</span><span class="sxs-lookup"><span data-stu-id="1c72f-140">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity с выбранным объектом TextMeshPro для Hints и настроенным компонентом EyeTrackingTarget](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="1c72f-142">**Повторите** этот шаг для объекта кнопки **Explode** (Развернуть) и **Reset** (Сбросить), чтобы настроить отслеживание взгляда для оставшихся кнопок.</span><span class="sxs-lookup"><span data-stu-id="1c72f-142">**Repeat** this step for **Explode** and **Reset** button object to configure eye tracking for remaining buttons.</span></span>

<span data-ttu-id="1c72f-143">Если теперь перейти в режим игры, а затем нажать и удерживать правую кнопку мыши при перемещении указателя мыши до тех пор, пока взгляд не достигнет одной из кнопок, вы увидите, что размер шрифта увеличится на 50 %. При отведении взгляда текст вернется к исходному размеру:</span><span class="sxs-lookup"><span data-stu-id="1c72f-143">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the buttons, you will see the text font size increase by 50% and reset back to its original size when looking away:</span></span>

![Разделенное представление Unity в режиме воспроизведения с взглядом, направленным на метку кнопки Explode с отслеживанием взгляда](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="1c72f-145">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="1c72f-145">Congratulations</span></span>

<span data-ttu-id="1c72f-146">Из этого руководства вы узнали, как включить функцию отслеживания взгляда для HoloLens 2 и добавить ее в объекты, чтобы активировать действия, когда пользователь смотрит на объекты.</span><span class="sxs-lookup"><span data-stu-id="1c72f-146">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c72f-147">Следующее руководство: 9. Использование речевых команд</span><span class="sxs-lookup"><span data-stu-id="1c72f-147">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
