---
title: Использование функции отслеживания взгляда
description: Из этого курса вы узнаете, как использовать отслеживание глаз в приложениях смешанной реальности в Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, отслеживание глаз
ms.localizationpriority: high
ms.openlocfilehash: a5b93b9e66ffb1e4e9f60251cdc146f48005ae8b
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2021
ms.locfileid: "110713795"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="d179a-104">8. Использование функции отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="d179a-104">8. Using eye-tracking</span></span>

<span data-ttu-id="d179a-105">Из этого руководства вы узнаете, как включить функцию отслеживания взгляда для HoloLens 2 и добавить ее в объекты, чтобы активировать действия, когда пользователь смотрит на объекты.</span><span class="sxs-lookup"><span data-stu-id="d179a-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="d179a-106">Если вы также развертываете этот проект в HoloLens (1-е поколение), обратите внимание, что функция отслеживания взгляда поддерживается только в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d179a-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="d179a-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="d179a-107">Objectives</span></span>

* <span data-ttu-id="d179a-108">Узнайте, как включить функцию отслеживания взгляда для HoleLens 2</span><span class="sxs-lookup"><span data-stu-id="d179a-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="d179a-109">Узнайте, как с помощью функции отслеживания взгляда активировать действие</span><span class="sxs-lookup"><span data-stu-id="d179a-109">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="d179a-110">Проверка того, включена ли функция ввода с использованием взгляда</span><span class="sxs-lookup"><span data-stu-id="d179a-110">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="d179a-111">В меню Unity последовательно выберите элементы Mixed Reality (Смешанная реальность) > Toolkit (Набор средств) > Utilities (Служебные программы) > **Configure Project for MRTK** (Настроить проект для MRTK), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Затем перейдите в раздел **UWP Capabilities** (Возможности UWP) и убедитесь, что раздел **Enable Eye Gaze Input Capability** (Включить ввод с использованием взгляда) выделен серым цветом.</span><span class="sxs-lookup"><span data-stu-id="d179a-111">In the Unity menu, select Mixed Reality > Toolkit > Utilities > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Окно конфигурации проекта MRTK в Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d179a-113">Функция ввода с использованием взгляда должна была быть включена в ходе выполнения инструкций, приведенных в разделе [Применение параметров конфигуратора проекта MRTK](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk), при настройке проекта Unity в начале работы с этой серией руководств.</span><span class="sxs-lookup"><span data-stu-id="d179a-113">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="d179a-114">Если функция отключена, включите ее сейчас.</span><span class="sxs-lookup"><span data-stu-id="d179a-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="d179a-115">Включение отслеживания взгляда в поставщике данных о направлении взгляда</span><span class="sxs-lookup"><span data-stu-id="d179a-115">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="d179a-116">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, затем в окне Inspector (Инспектор) перейдите на вкладку MixedRealityToolkit > **Input** (Ввод) и выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="d179a-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="d179a-117">Клонируйте профиль **DefaultHoloLens2InputSystemProfile** и присвойте ему понятное имя, например _GettingStarted_HoloLens2InputSystemProfile_.</span><span class="sxs-lookup"><span data-stu-id="d179a-117">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="d179a-118">Разверните раздел **Pointers** (Указатели).</span><span class="sxs-lookup"><span data-stu-id="d179a-118">Expand the **Pointers** section</span></span>
* <span data-ttu-id="d179a-119">Клонируйте профиль **DefaultMixedRealityPointerProfile** и присвойте ему понятное имя, например _GettingStarted_MixedRealityPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="d179a-119">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="d179a-120">В разделе **Gaze Settings** (Параметры взгляда) установите флажок **Is Eye Tracking Enabled** (Включено отслеживание взгляда).</span><span class="sxs-lookup"><span data-stu-id="d179a-120">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Компонент MixedRealityToolkit в Unity с примененными созданными профилями и включенным отслеживанием глаз](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="d179a-122">Сведения о том, как правильно клонировать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="d179a-122">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="d179a-123">Включение имитации отслеживания взгляда для редактора Unity</span><span class="sxs-lookup"><span data-stu-id="d179a-123">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="d179a-124">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, в окне инспектора откройте вкладку **Input** (Ввод) и сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="d179a-124">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="d179a-125">Разверните раздел **Input Data Providers**  > **Input Simulation Service** (Поставщики входных данных > Служба имитации ввода).</span><span class="sxs-lookup"><span data-stu-id="d179a-125">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="d179a-126">Клонируйте профиль **DefaultMixedRealityInputSimulationProfile** и присвойте ему понятное имя, например _GettingStarted_MixedRealityInputSimulationProfile_.</span><span class="sxs-lookup"><span data-stu-id="d179a-126">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="d179a-127">Найдите раздел **Eye Gaze Simulation** (Имитация направления взгляда) и задайте для параметра **Default Eye Gaze Simulation Mode** (Режим имитации направления взгляда по умолчанию) значение **Camera Forward Axis** (Ось камеры, направленная вперед).</span><span class="sxs-lookup"><span data-stu-id="d179a-127">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![Unity с выбранным объектом TextMeshPro](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="d179a-129">Добавление функции отслеживания взгляда в объекты</span><span class="sxs-lookup"><span data-stu-id="d179a-129">Adding eye-tracking to objects</span></span>

<span data-ttu-id="d179a-130">В окне Hierarchy (Иерархия) разверните **RoverExplorer** > **Buttons (Кнопки)** и выберите все три дочерних объекта кнопки:</span><span class="sxs-lookup"><span data-stu-id="d179a-130">In the Hierarchy window, expand the **RoverExplorer** > **Buttons**, then select all three of the child button objects:</span></span>

![Unity с выбранным объектом Button](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="d179a-132">Выбрав три объекта Button, в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **EyeTrackingTarget** ко всем выбранным объектам:</span><span class="sxs-lookup"><span data-stu-id="d179a-132">With all three Button objects still selected, in the Inspector window use the **Add Component** button to add the **EyeTrackingTarget** component to all the selected objects:</span></span>

![Unity с выбранным объектом TextMeshPro и добавленными компонентами](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="d179a-134">В окне Hierarchy (Иерархия) разверните **RoverExplorer** > **Buttons (Кнопки)**  > **Hints (Подсказки)**  > **SeeItSayItLabel** > **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="d179a-134">In the Hierarchy window, expand **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro**</span></span>

<span data-ttu-id="d179a-135">Затем в окне Hierarchy (Иерархия) выберите объект кнопки **Hints** (Советы) и настройте компонент **EyeTrackingTarget** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d179a-135">Then in the Hierarchy window, select the **Hints** button object , and configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="d179a-136">В разделе события **On Look At Start ()** (При взгляде на начало ())</span><span class="sxs-lookup"><span data-stu-id="d179a-136">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="d179a-137">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="d179a-137">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="d179a-138">Назначьте объект **TextMeshPro** от кнопки **Hints** (Советы) полю **None (Object)** (Нет (объект)).</span><span class="sxs-lookup"><span data-stu-id="d179a-138">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="d179a-139">В раскрывающемся списке **No Function** (Нет функции) выберите **TextMeshPro** > **float fontSize**, чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="d179a-139">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="d179a-140">Задайте для аргумента значение **0,06**, чтобы увеличить текущий размер шрифта 0,04 на 50 %.</span><span class="sxs-lookup"><span data-stu-id="d179a-140">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="d179a-141">В разделе события **On Look At Start ()** (При отведении взгляда ())</span><span class="sxs-lookup"><span data-stu-id="d179a-141">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="d179a-142">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="d179a-142">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="d179a-143">Назначьте объект **TextMeshPro** от кнопки **Hints** (Советы) полю **None (Object)** (Нет (объект)).</span><span class="sxs-lookup"><span data-stu-id="d179a-143">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="d179a-144">В раскрывающемся списке **No Function** (Нет функции) выберите **TextMeshPro** > **float fontSize**, чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="d179a-144">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="d179a-145">Задайте для аргумента значение **0,04**, чтобы сбросить размер шрифта обратно до значения 0,04.</span><span class="sxs-lookup"><span data-stu-id="d179a-145">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity с выбранным объектом TextMeshPro для Hints и настроенным компонентом EyeTrackingTarget](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="d179a-147">**Повторите** этот шаг для объекта кнопки **Explode** (Развернуть) и **Reset** (Сбросить), чтобы настроить отслеживание взгляда для оставшихся кнопок.</span><span class="sxs-lookup"><span data-stu-id="d179a-147">**Repeat** this step for **Explode** and **Reset** button object to configure eye tracking for remaining buttons.</span></span>

<span data-ttu-id="d179a-148">Если теперь перейти в режим игры, а затем нажать и удерживать правую кнопку мыши при перемещении указателя мыши до тех пор, пока взгляд не достигнет одной из кнопок, вы увидите, что размер шрифта увеличится на 50 %. При отведении взгляда текст вернется к исходному размеру:</span><span class="sxs-lookup"><span data-stu-id="d179a-148">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the buttons, you will see the text font size increase by 50% and reset back to its original size when looking away:</span></span>

![Разделенное представление Unity в режиме воспроизведения с взглядом, направленным на метку кнопки Explode с отслеживанием взгляда](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="d179a-150">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d179a-150">Congratulations</span></span>

<span data-ttu-id="d179a-151">Из этого руководства вы узнали, как включить функцию отслеживания взгляда для HoloLens 2 и добавить ее в объекты, чтобы активировать действия, когда пользователь смотрит на объекты.</span><span class="sxs-lookup"><span data-stu-id="d179a-151">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d179a-152">Следующее руководство: 9. Использование речевых команд</span><span class="sxs-lookup"><span data-stu-id="d179a-152">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
