---
title: Серия учебников по началу работы, часть 9 Использование речевых команд
description: Сведения о том, как использовать набор Mixed Reality Toolkit (MRTK) для создания приложений смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d9ddf3d234b68dfe4ce3ab5c9272566479edd71d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91700912"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="aee59-105">9. Использование речевых команд</span><span class="sxs-lookup"><span data-stu-id="aee59-105">9. Using speech commands</span></span>

## <a name="overview"></a><span data-ttu-id="aee59-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="aee59-106">Overview</span></span>

<span data-ttu-id="aee59-107">Из этого учебника вы узнаете, как создавать речевые команды и управлять ими глобально.</span><span class="sxs-lookup"><span data-stu-id="aee59-107">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="aee59-108">Вы также узнаете, как управлять локальными речевыми командами, которые требуют от пользователя просмотра объекта, управляющего речевой командой.</span><span class="sxs-lookup"><span data-stu-id="aee59-108">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="aee59-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="aee59-109">Objectives</span></span>

* <span data-ttu-id="aee59-110">Узнать, как создавать речевые команды.</span><span class="sxs-lookup"><span data-stu-id="aee59-110">Learn how to create speech commands</span></span>
* <span data-ttu-id="aee59-111">Узнать, как управлять речевыми командами на локальном и глобальном уровнях.</span><span class="sxs-lookup"><span data-stu-id="aee59-111">Learn how to control speech commands globally and locally</span></span>

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="aee59-112">Активация функции микрофона</span><span class="sxs-lookup"><span data-stu-id="aee59-112">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="aee59-113">В меню Unity выберите Mixed Reality Toolkit (Набор средств для смешанной реальности) > Utilities (Служебные программы) > **Configure Unity Project** (Настроить проект Unity), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проекта MRTK). Затем в разделе **UWP Capabilities** (Возможности UWP) убедитесь, что параметр **Enable Microphone Capability** (Включить функцию микрофона) выделен серым цветом:</span><span class="sxs-lookup"><span data-stu-id="aee59-113">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Включение поддержки микрофона](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="aee59-115">Во время выполнения инструкций по настройке проекта Unity из раздела [Применение параметров конфигуратора проекта MRTK](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings), приведенного в начале этого учебного курса, должна быть включена функция поддержки микрофона.</span><span class="sxs-lookup"><span data-stu-id="aee59-115">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="aee59-116">Если функция отключена, включите ее сейчас.</span><span class="sxs-lookup"><span data-stu-id="aee59-116">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="creating-speech-commands"></a><span data-ttu-id="aee59-117">Создание речевых команд</span><span class="sxs-lookup"><span data-stu-id="aee59-117">Creating speech commands</span></span>

<span data-ttu-id="aee59-118">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit** , затем в окне Inspector (Инспектор) перейдите на вкладку MixedRealityToolkit > **Input** (Ввод) и выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="aee59-118">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="aee59-119">Разверните раздел **Speech** (Речь).</span><span class="sxs-lookup"><span data-stu-id="aee59-119">Expand the **Speech** section</span></span>
* <span data-ttu-id="aee59-120">Клонируйте **DefaultMixedRealitySpeechCommandsProfile** и присвойте ему подходящее имя, например _GettingStarted_MixedRealitySpeechCommandsProfile_ .</span><span class="sxs-lookup"><span data-stu-id="aee59-120">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="aee59-121">Убедитесь, что параметр **Start Behaviour** (Поведение при запуске) имеет значение **Auto Start** (Автоматический запуск).</span><span class="sxs-lookup"><span data-stu-id="aee59-121">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![Создание речевых команд](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="aee59-123">Сведения о том, как правильно клонировать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="aee59-123">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="aee59-124">В разделе Speech (Речь) > **Speech Commands** (Речевые команды) нажмите кнопку **+ Add a New Speech Command** (Добавить новую речевую команду) четыре раза, чтобы добавить четыре новые речевые команды в список существующих речевых команд, а затем в поле **Keyword** (Ключевое слово) введите такие фразы:</span><span class="sxs-lookup"><span data-stu-id="aee59-124">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="aee59-125">Enable Indicator (Включить индикатор).</span><span class="sxs-lookup"><span data-stu-id="aee59-125">Enable Indicator</span></span>
* <span data-ttu-id="aee59-126">Enable Tap to Place (Включить возможность размещения касанием).</span><span class="sxs-lookup"><span data-stu-id="aee59-126">Enable Tap to Place</span></span>
* <span data-ttu-id="aee59-127">Enable Bounding Box (Включить ограничивающую рамку).</span><span class="sxs-lookup"><span data-stu-id="aee59-127">Enable Bounding Box</span></span>
* <span data-ttu-id="aee59-128">Disable Bounding Box (Отключить ограничивающую рамку).</span><span class="sxs-lookup"><span data-stu-id="aee59-128">Disable Bounding Box</span></span>

![Добавление новых речевых команд](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="aee59-130">Если на компьютере нет микрофона, можно задать для речевых команд код клавиши. Это позволит запускать их нажатием соответствующей клавиши.</span><span class="sxs-lookup"><span data-stu-id="aee59-130">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="aee59-131">Управление речевыми командами</span><span class="sxs-lookup"><span data-stu-id="aee59-131">Controlling speech commands</span></span>

<span data-ttu-id="aee59-132">В окне Project (Проект) перейдите в папку **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** , чтобы найти заготовки подсказок:</span><span class="sxs-lookup"><span data-stu-id="aee59-132">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Открытие папки с подсказками](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="aee59-134">Щелкните правой кнопкой мыши пустое место в окне Hierarchy (Иерархия) и выберите **Create Empty** (Создать пустой), чтобы добавить к сцене пустой объект.</span><span class="sxs-lookup"><span data-stu-id="aee59-134">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="aee59-135">Присвойте объекту имя **SpeechInputHandler_Global** , затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **SpeechInputHandler** , и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="aee59-135">Name the object **SpeechInputHandler_Global** , then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="aee59-136">**Снимите флажок** в окне **Is Focus Required** (Требуется фокус), чтобы пользователь не видел объект с компонентом SpeechInputHandler для активации речевой команды.</span><span class="sxs-lookup"><span data-stu-id="aee59-136">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="aee59-137">В окне Project (Проект) добавьте заготовку **SpeechConfirmation Tooltip** в поле **Speech Confirmation Tooltip Prefab** (Заготовка подсказки подтверждения голосом), чтобы эта заготовка отображалась при распознавании речевой команды.</span><span class="sxs-lookup"><span data-stu-id="aee59-137">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Настройка компонента обработчика речевого ввода](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="aee59-139">В компоненте SpeechInputHandler щелкните маленький значок **+** три раза, чтобы добавить три элемента ключевого слова:</span><span class="sxs-lookup"><span data-stu-id="aee59-139">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![Добавление элементов ключевых слов в обработчик речевого ввода](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="aee59-141">Разверните пункт **Element 0** (Элемент 0) и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="aee59-141">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="aee59-142">В поле **Keyword** (Ключевое слово) введите **Enable Indicator** (Включить индикатор) для ссылки на речевую команду Enable Indicator (Включить индикатор), созданную в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="aee59-142">In the **Keyword** field, enter **Enable Indicator** , to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="aee59-143">Щелкните маленький значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="aee59-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="aee59-144">В окне Hierarchy (Иерархия) укажите объект **Indicator** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="aee59-144">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="aee59-145">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **GameObject** > **SetActive (bool)** , чтобы задать эту функцию как действие, выполняемое при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="aee59-145">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="aee59-146">Убедитесь, что **установлен** флажок аргумента.</span><span class="sxs-lookup"><span data-stu-id="aee59-146">Check the argument checkbox, so it is **checked**</span></span>

![Настройка элемента ключевого слова 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="aee59-148">Разверните пункт **Element 1** (Элемент 1) и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="aee59-148">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="aee59-149">В поле **Keyword** (Ключевое слово) введите **Enable Bounding Box** (Включить ограничивающую рамку) для ссылки на команду Enable Bounding Box (Включить ограничивающую рамку), созданную в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="aee59-149">In the **Keyword** field, enter **Enable Bounding Box** , to reference the Enable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="aee59-150">Щелкните маленький значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="aee59-150">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="aee59-151">В окне Hierarchy (Иерархия) укажите объект **RoverExplorer** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="aee59-151">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="aee59-152">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **BoundingBox** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="aee59-152">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="aee59-153">Убедитесь, что **установлен** флажок аргумента.</span><span class="sxs-lookup"><span data-stu-id="aee59-153">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="aee59-154">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="aee59-154">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="aee59-155">В окне Hierarchy (Иерархия) укажите объект **RoverExplorer** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="aee59-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="aee59-156">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ObjectManipulator** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="aee59-156">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="aee59-157">Убедитесь, что **установлен** флажок аргумента.</span><span class="sxs-lookup"><span data-stu-id="aee59-157">Check the argument checkbox, so it is **checked**</span></span>

![Настройка элемента ключевого слова 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="aee59-159">Разверните пункт **Element 2** (Элемент 2) и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="aee59-159">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="aee59-160">В поле **Keyword** (Ключевое слово) введите **Disable Bounding Box** (Отключить ограничивающую рамку) для ссылки на команду Disable Bounding Box (Отключить ограничивающую рамку), созданную в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="aee59-160">In the **Keyword** field, enter **Disable Bounding Box** , to reference the Disable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="aee59-161">Щелкните маленький значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="aee59-161">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="aee59-162">В окне Hierarchy (Иерархия) укажите объект **RoverExplorer** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="aee59-162">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="aee59-163">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **BoundingBox** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="aee59-163">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="aee59-164">Убедитесь, что флажок аргумента **снят** .</span><span class="sxs-lookup"><span data-stu-id="aee59-164">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="aee59-165">Щелкните небольшой значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="aee59-165">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="aee59-166">В окне Hierarchy (Иерархия) укажите объект **RoverExplorer** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="aee59-166">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="aee59-167">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **ObjectManipulator** > **bool enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="aee59-167">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="aee59-168">Убедитесь, что флажок аргумента **снят** .</span><span class="sxs-lookup"><span data-stu-id="aee59-168">Verify that the argument checkbox is **unchecked**</span></span>

![Настройка элемента ключевого слова 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="aee59-170">В окне Hierarchy (Иерархия) выберите объект RoverExplorer > **RoverAssembly** , затем в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **SpeechInputHandler** , и настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="aee59-170">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="aee59-171">Убедитесь, что флажок **Is Focus Required** (Требуется фокус) **установлен** , чтобы пользователь видел объект с компонентом SpeechInputHandler, например RoverAssembly, для активации речевой команды.</span><span class="sxs-lookup"><span data-stu-id="aee59-171">Verify that the **Is Focus Required** checkbox is **check** , so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="aee59-172">В окне Project (Проект) добавьте заготовку **SpeechConfirmation Tooltip** в поле **Speech Confirmation Tooltip Prefab** (Заготовка подсказки подтверждения голосом), чтобы эта заготовка отображалась при распознавании речевой команды.</span><span class="sxs-lookup"><span data-stu-id="aee59-172">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Добавление обработчика речевого ввода в Rover Assembly](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="aee59-174">В компоненте SpeechInputHandler щелкните маленький значок **+** , чтобы добавить элемент ключевого слова, разверните только что созданный элемент, а затем настройте его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="aee59-174">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="aee59-175">В поле **Keyword** (Ключевое слово) введите **Enable Tap to Place** (Включить возможность размещения касанием) для ссылки на команду Enable Tap to Place (Включить возможность размещения касанием), созданную в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="aee59-175">In the **Keyword** field, enter **Enable Tap to Place** , to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="aee59-176">Щелкните маленький значок **+** , чтобы добавить событие.</span><span class="sxs-lookup"><span data-stu-id="aee59-176">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="aee59-177">В окне Hierarchy (Иерархия) укажите сам объект, т. е. тот же объект **RoverAssembly** в поле **None (Object)** (Отсутствует (Объект)).</span><span class="sxs-lookup"><span data-stu-id="aee59-177">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="aee59-178">В раскрывающемся списке **No Function** (Функция отсутствует) выберите **TapToPlace** > **bool Enabled** (Активация по логическому значению), чтобы обновлять это значение свойства при срабатывании события.</span><span class="sxs-lookup"><span data-stu-id="aee59-178">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="aee59-179">Убедитесь, что **установлен** флажок аргумента.</span><span class="sxs-lookup"><span data-stu-id="aee59-179">Check the argument checkbox, so it is **checked**</span></span>

![Настройка обработчика речевого ввода в Rover Assembly](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="aee59-181">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="aee59-181">Congratulations</span></span>

<span data-ttu-id="aee59-182">Из этого учебника вы узнали, как создавать речевые команды и управлять ими глобально.</span><span class="sxs-lookup"><span data-stu-id="aee59-182">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="aee59-183">Вы также узнали, как управлять локальными речевыми командами, требующими от пользователя просмотра объекта, управляющего речевой командой.</span><span class="sxs-lookup"><span data-stu-id="aee59-183">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="aee59-184">На этом работа с серией [учебников по началу работы](mr-learning-base-01.md) завершена.</span><span class="sxs-lookup"><span data-stu-id="aee59-184">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="aee59-185">С помощью этих учебников вы успешно создали полную среду смешанной реальности с нуля, используя MRTK.</span><span class="sxs-lookup"><span data-stu-id="aee59-185">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="aee59-186">В следующих двух сериях учебников по [Пространственным привязкам Azure](mr-learning-asa-01.md) и [многопользовательским возможностям](mr-learning-sharing-01.md) вы узнаете, как интегрировать Пространственные привязки Azure в проект, чтобы использовать опыт работы с обозревателем лунохода в реальных условиях.</span><span class="sxs-lookup"><span data-stu-id="aee59-186">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="aee59-187">Затем вы узнаете, как добавлять в проект многопользовательские возможности, чтобы предоставить общий доступ к сведениям о перемещении пользователя и объекта в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="aee59-187">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="aee59-188">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="aee59-188">Next Development Checkpoint</span></span>

<span data-ttu-id="aee59-189">Если вы следуете изложенным нами этапам разработки для Unity, вашей следующей задачей будет ознакомление с основными стандартными блоками приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="aee59-189">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aee59-190">Базовые взаимодействия</span><span class="sxs-lookup"><span data-stu-id="aee59-190">Basic interactions</span></span>](../mrtk-101.md)

<span data-ttu-id="aee59-191">Вы можете в любой момент вернуться к [этапам разработки для Unity](../unity-development-overview.md#1-getting-started).</span><span class="sxs-lookup"><span data-stu-id="aee59-191">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>
