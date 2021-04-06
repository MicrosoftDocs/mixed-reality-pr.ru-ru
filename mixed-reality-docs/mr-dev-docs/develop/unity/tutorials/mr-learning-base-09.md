---
title: Использование речевых команд
description: Из этого курса вы узнаете, как создать, настроить и использовать речевые команды в приложениях смешанной реальности с помощью Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, речевые команды, голосовой ввод
ms.localizationpriority: high
ms.openlocfilehash: 3aea23d5a259e555f47ca9ea41d77f345c977aeb
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982951"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="d1753-104">9. Использование речевых команд</span><span class="sxs-lookup"><span data-stu-id="d1753-104">9. Using speech commands</span></span>

<span data-ttu-id="d1753-105">Из этого учебника вы узнаете, как создавать речевые команды и управлять ими глобально.</span><span class="sxs-lookup"><span data-stu-id="d1753-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="d1753-106">Вы также узнаете, как управлять локальными речевыми командами, которые требуют от пользователя просмотра объекта, управляющего речевой командой.</span><span class="sxs-lookup"><span data-stu-id="d1753-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="d1753-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="d1753-107">Objectives</span></span>

* <span data-ttu-id="d1753-108">Узнать, как создавать речевые команды.</span><span class="sxs-lookup"><span data-stu-id="d1753-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="d1753-109">Узнать, как управлять речевыми командами на локальном и глобальном уровнях.</span><span class="sxs-lookup"><span data-stu-id="d1753-109">Learn how to control speech commands globally and locally</span></span>

[!INCLUDE[](includes/ensuring-microphone-capabality.md)]

## <a name="creating-speech-commands"></a><span data-ttu-id="d1753-110">Создание речевых команд</span><span class="sxs-lookup"><span data-stu-id="d1753-110">Creating speech commands</span></span>

<span data-ttu-id="d1753-111">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, затем в окне Inspector (Инспектор) перейдите на вкладку MixedRealityToolkit > **Input** (Ввод) и выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="d1753-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="d1753-112">Разверните раздел **Speech** (Речь).</span><span class="sxs-lookup"><span data-stu-id="d1753-112">Expand the **Speech** section</span></span>
* <span data-ttu-id="d1753-113">Клонируйте **DefaultMixedRealitySpeechCommandsProfile** и присвойте ему подходящее имя, например _GettingStarted_MixedRealitySpeechCommandsProfile_.</span><span class="sxs-lookup"><span data-stu-id="d1753-113">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="d1753-114">Убедитесь, что параметр **Start Behaviour** (Поведение при запуске) имеет значение **Auto Start** (Автоматический запуск).</span><span class="sxs-lookup"><span data-stu-id="d1753-114">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![Создание речевых команд](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="d1753-116">Сведения о том, как правильно клонировать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="d1753-116">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="d1753-117">В разделе Speech (Речь) > **Speech Commands** (Речевые команды) нажмите кнопку **+ Add a New Speech Command** (Добавить новую речевую команду) четыре раза, чтобы добавить четыре новые речевые команды в список существующих речевых команд, а затем в поле **Keyword** (Ключевое слово) введите такие фразы:</span><span class="sxs-lookup"><span data-stu-id="d1753-117">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="d1753-118">Enable Indicator (Включить индикатор).</span><span class="sxs-lookup"><span data-stu-id="d1753-118">Enable Indicator</span></span>
* <span data-ttu-id="d1753-119">Enable Tap to Place (Включить возможность размещения касанием).</span><span class="sxs-lookup"><span data-stu-id="d1753-119">Enable Tap to Place</span></span>
* <span data-ttu-id="d1753-120">Включение управления границами</span><span class="sxs-lookup"><span data-stu-id="d1753-120">Enable Bounds Control</span></span>
* <span data-ttu-id="d1753-121">Отключение управления границами</span><span class="sxs-lookup"><span data-stu-id="d1753-121">Disable Bounds Control</span></span>

![Добавление новых речевых команд](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="d1753-123">Если на компьютере нет микрофона, можно задать для речевых команд код клавиши. Это позволит запускать их нажатием соответствующей клавиши.</span><span class="sxs-lookup"><span data-stu-id="d1753-123">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="d1753-124">Управление речевыми командами</span><span class="sxs-lookup"><span data-stu-id="d1753-124">Controlling speech commands</span></span>

<span data-ttu-id="d1753-125">В окне Project (Проект) перейдите к папке **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip**, чтобы найти заготовки подсказок:</span><span class="sxs-lookup"><span data-stu-id="d1753-125">In the Project window, navigate to the **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Открытие папки с подсказками](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="d1753-127">Щелкните правой кнопкой мыши пустое место в окне Hierarchy (Иерархия) и выберите **Create Empty** (Создать пустой), чтобы добавить к сцене пустой объект.</span><span class="sxs-lookup"><span data-stu-id="d1753-127">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="d1753-128">Присвойте объекту имя **SpeechInputHandler_Global**, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **SpeechInputHandler**, и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1753-128">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="d1753-129">**Снимите флажок** в окне **Is Focus Required** (Требуется фокус), чтобы пользователь не видел объект с компонентом SpeechInputHandler для активации речевой команды.</span><span class="sxs-lookup"><span data-stu-id="d1753-129">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="d1753-130">В окне Project (Проект) добавьте заготовку **SpeechConfirmation Tooltip** в поле **Speech Confirmation Tooltip Prefab** (Заготовка подсказки подтверждения голосом), чтобы эта заготовка отображалась при распознавании речевой команды.</span><span class="sxs-lookup"><span data-stu-id="d1753-130">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Настройка компонента обработчика речевого ввода](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="d1753-132">В компоненте SpeechInputHandler щелкните маленький значок **+** три раза, чтобы добавить три элемента ключевого слова:</span><span class="sxs-lookup"><span data-stu-id="d1753-132">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![Добавление элементов ключевых слов в обработчик речевого ввода](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="d1753-134">Разверните пункт **Element 0** (Элемент 0) и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1753-134">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="d1753-135">В поле **Keyword** (Ключевое слово) введите **Enable Indicator** (Включить индикатор) для ссылки на речевую команду Enable Indicator (Включить индикатор), созданную в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="d1753-135">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="d1753-136">Щелкните маленький значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="d1753-136">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="d1753-137">В окне Hierarchy (Иерархия) укажите объект **Indicator** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="d1753-137">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d1753-138">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **GameObject** > **SetActive (bool)** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="d1753-138">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="d1753-139">Убедитесь, что **установлен** флажок аргумента.</span><span class="sxs-lookup"><span data-stu-id="d1753-139">Check the argument checkbox, so it is **checked**</span></span>

![Настройка элемента ключевого слова 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="d1753-141">Разверните пункт **Element 1** (Элемент 1) и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1753-141">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="d1753-142">В поле **Keyword** (Ключевое слово) введите **Enable Bounds Control** (Включить управление границами) для ссылки на команду Enable Bounds Control, созданную в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="d1753-142">In the **Keyword** field, enter **Enable Bounds Control**, to reference the Enable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="d1753-143">Щелкните маленький значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="d1753-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="d1753-144">В окне Hierarchy (Иерархия) укажите объект **RoverExplorer** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="d1753-144">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d1753-145">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **BoundsControl** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="d1753-145">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="d1753-146">Убедитесь, что **установлен** флажок аргумента.</span><span class="sxs-lookup"><span data-stu-id="d1753-146">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="d1753-147">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="d1753-147">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="d1753-148">В окне Hierarchy (Иерархия) укажите объект **RoverExplorer** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="d1753-148">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d1753-149">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ObjectManipulator** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="d1753-149">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="d1753-150">Убедитесь, что **установлен** флажок аргумента.</span><span class="sxs-lookup"><span data-stu-id="d1753-150">Check the argument checkbox, so it is **checked**</span></span>

![Настройка элемента ключевого слова 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="d1753-152">Разверните пункт **Element 2** (Элемент 2) и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1753-152">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="d1753-153">В поле **Keyword** (Ключевое слово) введите **Disable Bounds Control** (Отключить управление границами) для ссылки на команду Disable Bounds Control, созданную в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="d1753-153">In the **Keyword** field, enter **Disable Bounds Control**, to reference the Disable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="d1753-154">Щелкните маленький значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="d1753-154">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="d1753-155">В окне Hierarchy (Иерархия) укажите объект **RoverExplorer** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="d1753-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d1753-156">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **BoundsControl** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="d1753-156">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="d1753-157">Убедитесь, что флажок аргумента **снят**.</span><span class="sxs-lookup"><span data-stu-id="d1753-157">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="d1753-158">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="d1753-158">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="d1753-159">В окне Hierarchy (Иерархия) укажите объект **RoverExplorer** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="d1753-159">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d1753-160">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ObjectManipulator** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="d1753-160">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="d1753-161">Убедитесь, что флажок аргумента **снят**.</span><span class="sxs-lookup"><span data-stu-id="d1753-161">Verify that the argument checkbox is **unchecked**</span></span>

![Настройка элемента ключевого слова 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="d1753-163">В окне Hierarchy (Иерархия) выберите объект RoverExplorer > **RoverAssembly**, затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **SpeechInputHandler**, и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1753-163">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="d1753-164">Убедитесь, что флажок **Is Focus Required** (Требуется фокус) **установлен**, чтобы пользователь видел объект с компонентом SpeechInputHandler, например RoverAssembly, для активации речевой команды.</span><span class="sxs-lookup"><span data-stu-id="d1753-164">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="d1753-165">В окне Project (Проект) добавьте заготовку **SpeechConfirmation Tooltip** в поле **Speech Confirmation Tooltip Prefab** (Заготовка подсказки подтверждения голосом), чтобы эта заготовка отображалась при распознавании речевой команды.</span><span class="sxs-lookup"><span data-stu-id="d1753-165">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Добавление обработчика речевого ввода в Rover Assembly](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="d1753-167">В компоненте SpeechInputHandler щелкните маленький значок **+** , чтобы добавить элемент ключевого слова, разверните только что созданный элемент, а затем настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d1753-167">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="d1753-168">В поле **Keyword** (Ключевое слово) введите **Enable Tap to Place** (Включить возможность размещения касанием) для ссылки на команду Enable Tap to Place (Включить возможность размещения касанием), созданную в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="d1753-168">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="d1753-169">Щелкните маленький значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="d1753-169">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="d1753-170">В окне Hierarchy (Иерархия) укажите сам объект, т. е. тот же объект **RoverAssembly** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="d1753-170">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="d1753-171">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **TapToPlace** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="d1753-171">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="d1753-172">Убедитесь, что **установлен** флажок аргумента.</span><span class="sxs-lookup"><span data-stu-id="d1753-172">Check the argument checkbox, so it is **checked**</span></span>

![Настройка обработчика речевого ввода в Rover Assembly](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="d1753-174">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d1753-174">Congratulations</span></span>

<span data-ttu-id="d1753-175">Из этого учебника вы узнали, как создавать речевые команды и управлять ими глобально.</span><span class="sxs-lookup"><span data-stu-id="d1753-175">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="d1753-176">Вы также узнали, как управлять локальными речевыми командами, требующими от пользователя просмотра объекта, управляющего речевой командой.</span><span class="sxs-lookup"><span data-stu-id="d1753-176">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="d1753-177">На этом работа с серией [учебников по началу работы](mr-learning-base-01.md) завершена.</span><span class="sxs-lookup"><span data-stu-id="d1753-177">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="d1753-178">С помощью этих учебников вы успешно создали полную среду смешанной реальности с нуля, используя MRTK.</span><span class="sxs-lookup"><span data-stu-id="d1753-178">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="d1753-179">В следующих двух сериях учебников по [Пространственным привязкам Azure](mr-learning-asa-01.md) и [многопользовательским возможностям](mr-learning-sharing-01.md) вы узнаете, как интегрировать Пространственные привязки Azure в проект, чтобы использовать опыт работы с обозревателем лунохода в реальных условиях.</span><span class="sxs-lookup"><span data-stu-id="d1753-179">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="d1753-180">Затем вы узнаете, как добавлять в проект многопользовательские возможности, чтобы предоставить общий доступ к сведениям о перемещении пользователя и объекта в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="d1753-180">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="d1753-181">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="d1753-181">Next Development Checkpoint</span></span>

<span data-ttu-id="d1753-182">Если вы следуете изложенным нами этапам разработки для Unity, вашей следующей задачей будет ознакомление с основными стандартными блоками приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="d1753-182">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d1753-183">Базовые взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d1753-183">Basic interactions</span></span>](../../../out-of-scope/mrtk-101.md)

<span data-ttu-id="d1753-184">Вы можете в любой момент вернуться к [этапам разработки для Unity](../unity-development-overview.md#1-getting-started).</span><span class="sxs-lookup"><span data-stu-id="d1753-184">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>