---
title: Голосовой ввод
description: Речевой ввод — это основной ввод для впечатляющих головных телефонов HoloLens и Windows Mixed Reality. Voice можно использовать для команд, диктовки, Кортаны и т. д.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ГГВ, Voice, Кортана, речь, вход, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, HoloLens, МРТК, набор средств смешанной реальности, взгляд
ms.openlocfilehash: 09f99083d769be80d8c15016b3de8713eae76515
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848134"
---
# <a name="voice-input"></a><span data-ttu-id="bbe39-105">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="bbe39-105">Voice input</span></span>

![Голосовой ввод](images/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="bbe39-107">Голос — один из основных типов ввода в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bbe39-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="bbe39-108">Он позволяет напрямую создавать голограммы без использования [жестов руки](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="bbe39-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="bbe39-109">Голосовой ввод позволяет естественным способом сообщить о своих намерениях.</span><span class="sxs-lookup"><span data-stu-id="bbe39-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="bbe39-110">Речь особенно хорошо работает при обходе сложных интерфейсов, поскольку позволяет пользователям перемещаться по вложенным меню с помощью одной команды.</span><span class="sxs-lookup"><span data-stu-id="bbe39-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="bbe39-111">Речевой ввод обеспечивается тем [же механизмом](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) , который поддерживает распознавание речи во всех _универсальных приложениях Windows_.</span><span class="sxs-lookup"><span data-stu-id="bbe39-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all _Universal Windows Apps_.</span></span> <span data-ttu-id="bbe39-112">В HoloLens распознавание речи всегда будет работать на языке интерфейса Windows, настроенном в параметрах устройства.</span><span class="sxs-lookup"><span data-stu-id="bbe39-112">On HoloLens, speech recognition will always function in the Windows display language configured in your device Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="bbe39-113">Речь и взгляд</span><span class="sxs-lookup"><span data-stu-id="bbe39-113">Voice and gaze</span></span>

<span data-ttu-id="bbe39-114">Если вы используете речевые команды, то в качестве стандартного механизма нацеливания используется курсор, который является предметом выбора или для передачи команды в приложение, которое вы ищете.</span><span class="sxs-lookup"><span data-stu-id="bbe39-114">When you're using voice commands, head or eye gaze is the typical targeting mechanism, whether with a cursor to "select" or to channel your command to an application you're looking at.</span></span> <span data-ttu-id="bbe39-115">Может даже не потребоваться отображение курсора «взгляд» _(см. статью «как»)_.</span><span class="sxs-lookup"><span data-stu-id="bbe39-115">It may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="bbe39-116">Некоторым голосовым командам не требуется цель, например "перейти на начало" или "Привет, Кортана".</span><span class="sxs-lookup"><span data-stu-id="bbe39-116">Some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="bbe39-117">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="bbe39-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bbe39-118"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="bbe39-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="bbe39-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="bbe39-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="bbe39-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="bbe39-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="bbe39-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="bbe39-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bbe39-122">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="bbe39-122">Voice input</span></span></td>
        <td><span data-ttu-id="bbe39-123">✔️</span><span class="sxs-lookup"><span data-stu-id="bbe39-123">✔️</span></span></td>
        <td><span data-ttu-id="bbe39-124">✔️</span><span class="sxs-lookup"><span data-stu-id="bbe39-124">✔️</span></span></td>
        <td><span data-ttu-id="bbe39-125">✔️ (с микрофоном)</span><span class="sxs-lookup"><span data-stu-id="bbe39-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="bbe39-126">Команда "Select"</span><span class="sxs-lookup"><span data-stu-id="bbe39-126">The "select" command</span></span>

<span data-ttu-id="bbe39-127">**HoloLens (1-го поколения)**</span><span class="sxs-lookup"><span data-stu-id="bbe39-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="bbe39-128">Даже без специального добавления поддержки голоса в приложение пользователи могут активировать голограммы, просто выполнив команду "Select".</span><span class="sxs-lookup"><span data-stu-id="bbe39-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="bbe39-129">Это ведет себя так же, как [воздушный](gaze-and-commit.md#composite-gestures) вызов в hololens, нажатие кнопки выбрать на кнопке [hololens](https://docs.microsoft.com/hololens/hololens1-clicker)или нажатие триггера на [контроллере движения Windows Mixed Reality](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="bbe39-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](https://docs.microsoft.com/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="bbe39-130">Вы услышите звук и увидите подсказку с сообщением "Select" в качестве подтверждения.</span><span class="sxs-lookup"><span data-stu-id="bbe39-130">You'll hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="bbe39-131">"Select" включается алгоритмом обнаружения ключевых слов низкого уровня, что означает, что вы можете говорить в любое время с минимальным временем жизни аккумулятора.</span><span class="sxs-lookup"><span data-stu-id="bbe39-131">"Select" is enabled by a low-power keyword detection algorithm, which means you can say it anytime with minimal battery life impact.</span></span> <span data-ttu-id="bbe39-132">Вы даже можете сказать «SELECT», используя ваши руки.</span><span class="sxs-lookup"><span data-stu-id="bbe39-132">You can even say "select" with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="bbe39-133">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="bbe39-133">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="bbe39-134">Чтобы использовать команду "Select" в HoloLens 2, сначала необходимо открыть курсор взгляда, чтобы он использовался в качестве указателя.</span><span class="sxs-lookup"><span data-stu-id="bbe39-134">To use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="bbe39-135">Команду для ее упрощения можно запомнить — просто скажите «SELECT».</span><span class="sxs-lookup"><span data-stu-id="bbe39-135">The command to bring it up is easy to remember--just say, "select".</span></span><br><br>
        <span data-ttu-id="bbe39-136">Чтобы выйти из режима, снова используйте руки, нажимая на кнопку с пальцами или используя системный жест.</span><span class="sxs-lookup"><span data-stu-id="bbe39-136">To exit the mode, use your hands again by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br> 
        <span data-ttu-id="bbe39-137">*Изображение: Скажите "выбрать", чтобы использовать голосовую команду для выбора*</span><span class="sxs-lookup"><span data-stu-id="bbe39-137">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![Пользователь может сказать "выбрать", чтобы использовать голосовую команду для выбора.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a><span data-ttu-id="bbe39-139">"Привет, Кортана!"</span><span class="sxs-lookup"><span data-stu-id="bbe39-139">Hey Cortana</span></span>

<span data-ttu-id="bbe39-140">Вы можете сказать "Привет, Кортана!", чтобы открыть Кортану в любое время.</span><span class="sxs-lookup"><span data-stu-id="bbe39-140">You can say "Hey Cortana" to bring up Cortana at any time.</span></span> <span data-ttu-id="bbe39-141">Вам не нужно ждать, пока он пойдет, чтобы продолжить задавать вопрос или дать ему инструкцию.</span><span class="sxs-lookup"><span data-stu-id="bbe39-141">You don't have to wait for her to appear to continue asking her your question or giving her an instruction.</span></span> <span data-ttu-id="bbe39-142">Например, попробуйте сказать "Привет, Кортана, что такое Погода?".</span><span class="sxs-lookup"><span data-stu-id="bbe39-142">For example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="bbe39-143">как одно предложение.</span><span class="sxs-lookup"><span data-stu-id="bbe39-143">as a single sentence.</span></span> <span data-ttu-id="bbe39-144">Чтобы получить дополнительные сведения о Кортане и о том, что вы можете сделать, спросите!</span><span class="sxs-lookup"><span data-stu-id="bbe39-144">For more information about Cortana and what you can do, ask her!</span></span> <span data-ttu-id="bbe39-145">Скажите: "Привет, Кортана, что можно сказать?"</span><span class="sxs-lookup"><span data-stu-id="bbe39-145">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="bbe39-146">и она будет получать список рабочих и рекомендуемых команд.</span><span class="sxs-lookup"><span data-stu-id="bbe39-146">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="bbe39-147">Если вы уже находитесь в приложении Кортаны, выберите **?**</span><span class="sxs-lookup"><span data-stu-id="bbe39-147">If you're already in the Cortana app, select the **?**</span></span> <span data-ttu-id="bbe39-148">значок на боковой панели, чтобы извлечь это же меню.</span><span class="sxs-lookup"><span data-stu-id="bbe39-148">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="bbe39-149">**Команды, относящиеся к HoloLens**</span><span class="sxs-lookup"><span data-stu-id="bbe39-149">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="bbe39-150">"Что можно говорить?"</span><span class="sxs-lookup"><span data-stu-id="bbe39-150">"What can I say?"</span></span>
* <span data-ttu-id="bbe39-151">"Перейти на запуск"-вместо [раскрытия](system-gesture.md#bloom) для перехода в [меню "Пуск](../discover/navigating-the-windows-mixed-reality-home.md#start-menu) "</span><span class="sxs-lookup"><span data-stu-id="bbe39-151">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="bbe39-152">"Запуск <app> "</span><span class="sxs-lookup"><span data-stu-id="bbe39-152">"Launch <app>"</span></span>
* <span data-ttu-id="bbe39-153">"Переместить <app> сюда"</span><span class="sxs-lookup"><span data-stu-id="bbe39-153">"Move <app> here"</span></span>
* <span data-ttu-id="bbe39-154">"Сделать фотографию"</span><span class="sxs-lookup"><span data-stu-id="bbe39-154">"Take a picture"</span></span>
* <span data-ttu-id="bbe39-155">"Начать запись"</span><span class="sxs-lookup"><span data-stu-id="bbe39-155">"Start recording"</span></span>
* <span data-ttu-id="bbe39-156">"Закончить запись"</span><span class="sxs-lookup"><span data-stu-id="bbe39-156">"Stop recording"</span></span>
* <span data-ttu-id="bbe39-157">"Показывать луч"</span><span class="sxs-lookup"><span data-stu-id="bbe39-157">"Show hand ray"</span></span>
* <span data-ttu-id="bbe39-158">"Скрыть руки луча"</span><span class="sxs-lookup"><span data-stu-id="bbe39-158">"Hide hand ray"</span></span>
* <span data-ttu-id="bbe39-159">"Увеличить яркость"</span><span class="sxs-lookup"><span data-stu-id="bbe39-159">"Increase the brightness"</span></span>
* <span data-ttu-id="bbe39-160">"Уменьшить яркость"</span><span class="sxs-lookup"><span data-stu-id="bbe39-160">"Decrease the brightness"</span></span>
* <span data-ttu-id="bbe39-161">"Увеличение объема тома"</span><span class="sxs-lookup"><span data-stu-id="bbe39-161">"Increase the volume"</span></span>
* <span data-ttu-id="bbe39-162">"Уменьшить объем тома"</span><span class="sxs-lookup"><span data-stu-id="bbe39-162">"Decrease the volume"</span></span>
* <span data-ttu-id="bbe39-163">"Отключить" или "включить звук"</span><span class="sxs-lookup"><span data-stu-id="bbe39-163">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="bbe39-164">"Завершение работы устройства"</span><span class="sxs-lookup"><span data-stu-id="bbe39-164">"Shut down the device"</span></span>
* <span data-ttu-id="bbe39-165">"Перезапустить устройство"</span><span class="sxs-lookup"><span data-stu-id="bbe39-165">"Restart the device"</span></span>
* <span data-ttu-id="bbe39-166">"Переход в спящий режим"</span><span class="sxs-lookup"><span data-stu-id="bbe39-166">"Go to sleep"</span></span>
* <span data-ttu-id="bbe39-167">"Что такое время?"</span><span class="sxs-lookup"><span data-stu-id="bbe39-167">"What time is it?"</span></span>
* <span data-ttu-id="bbe39-168">«Сколько аккумулятора осталось?»</span><span class="sxs-lookup"><span data-stu-id="bbe39-168">"How much battery do I have left?"</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="bbe39-169">«Видите, скажите»</span><span class="sxs-lookup"><span data-stu-id="bbe39-169">"See It, Say It"</span></span><br>
        <span data-ttu-id="bbe39-170">HoloLens имеет модель "видите ИТ-IT" для голосового ввода, где метки на кнопках указывают пользователям, какие голосовые команды также могут говорить.</span><span class="sxs-lookup"><span data-stu-id="bbe39-170">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="bbe39-171">Например, при просмотре окна приложения в HoloLens (1-й номер) пользователь может сказать команду "настроить", чтобы настроить расположение приложения в мире.</span><span class="sxs-lookup"><span data-stu-id="bbe39-171">For example, when looking at an app window in HoloLens (1st gen), a user can say "Adjust" command to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="bbe39-172">*Изображение: пользователь может сказать команду "настроить", которая отображается на панели приложений, чтобы настроить расположение приложения.*</span><span class="sxs-lookup"><span data-stu-id="bbe39-172">*Image: A user can say the "Adjust" command, which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="bbe39-173">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="bbe39-173">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="bbe39-174">![При просмотре окна приложения или голограммы пользователь может сказать команду "настроить", которая отображается на панели приложений, чтобы настроить расположение приложения в мире](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="bbe39-174">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="bbe39-175">Когда приложения следуют этому правилу, пользователи могут легко понять, что следует сказать для управления системой.</span><span class="sxs-lookup"><span data-stu-id="bbe39-175">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="bbe39-176">Хотя облаками на кнопке в HoloLens (1-й), вы увидите всплывающую подсказку "Voice вдаваясь", которая появляется после второй, если кнопка включена с помощью голоса и отображает команду "нажать".</span><span class="sxs-lookup"><span data-stu-id="bbe39-176">While gazing at a button in HoloLens (1st gen), you'll see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="bbe39-177">Чтобы показать голосовые подсказки в HoloLens 2, отобразите голосовый курсор, указав "Select" или "что можно сказать" (см. изображение).</span><span class="sxs-lookup"><span data-stu-id="bbe39-177">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="bbe39-178">*Изображение: команды отображаются под кнопками.*</span><span class="sxs-lookup"><span data-stu-id="bbe39-178">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![Видите, что команды отображаются под кнопками](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="bbe39-180">Команды Voice для быстрой обработки с голограммами</span><span class="sxs-lookup"><span data-stu-id="bbe39-180">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="bbe39-181">Существует множество голосовых команд, которые можно сказать, облаками на голограммах, чтобы быстро выполнять задачи манипуляции.</span><span class="sxs-lookup"><span data-stu-id="bbe39-181">There are many voice commands you can say while gazing at a hologram to quickly do manipulation tasks.</span></span> <span data-ttu-id="bbe39-182">Эти команды работают с окнами приложений и трехмерными объектами, помещенными в мир.</span><span class="sxs-lookup"><span data-stu-id="bbe39-182">These voice commands work on app windows and 3D objects you've placed in the world.</span></span>

<span data-ttu-id="bbe39-183">**Команды обработки голограмм**</span><span class="sxs-lookup"><span data-stu-id="bbe39-183">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="bbe39-184">Лицом мне</span><span class="sxs-lookup"><span data-stu-id="bbe39-184">Face me</span></span>
* <span data-ttu-id="bbe39-185">Больше | Улучшение</span><span class="sxs-lookup"><span data-stu-id="bbe39-185">Bigger | Enhance</span></span>
* <span data-ttu-id="bbe39-186">Размеров</span><span class="sxs-lookup"><span data-stu-id="bbe39-186">Smaller</span></span>

<span data-ttu-id="bbe39-187">В HoloLens 2 можно также создавать более естественные взаимодействия в сочетании с глазами-взглядом, который неявно предоставляет контекстные сведения о том, на что вы ссылаетесь.</span><span class="sxs-lookup"><span data-stu-id="bbe39-187">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze, which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="bbe39-188">Например, можно взглянуть на голограмму и сказать, что _это_«поместить», а затем взглянуть на то, где нужно его поместить, и сказать « _сюда_».</span><span class="sxs-lookup"><span data-stu-id="bbe39-188">For example, you could look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="bbe39-189">Вы также можете взглянуть на сложную часть на сложной машине и сказать: "получить дополнительные сведения об _этом_".</span><span class="sxs-lookup"><span data-stu-id="bbe39-189">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>

## <a name="discovering-voice-commands"></a><span data-ttu-id="bbe39-190">Обнаружение команд Voice</span><span class="sxs-lookup"><span data-stu-id="bbe39-190">Discovering voice commands</span></span>

<span data-ttu-id="bbe39-191">Некоторые команды, например команды для быстрой обработки выше, могут быть скрыты.</span><span class="sxs-lookup"><span data-stu-id="bbe39-191">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="bbe39-192">Чтобы узнать, какие команды можно использовать, Взгляните на объект и скажите «что можно сказать?».</span><span class="sxs-lookup"><span data-stu-id="bbe39-192">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="bbe39-193">Откроется список возможных команд.</span><span class="sxs-lookup"><span data-stu-id="bbe39-193">A list of possible commands pops up.</span></span> <span data-ttu-id="bbe39-194">Можно также использовать курсор Head, чтобы найти и раскрывать подсказки голоса для каждой кнопки перед вами.</span><span class="sxs-lookup"><span data-stu-id="bbe39-194">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="bbe39-195">Если вам нужен полный список, просто скажите «показывать все команды» в любое время.</span><span class="sxs-lookup"><span data-stu-id="bbe39-195">If you want a complete list, just say, "Show all commands" anytime.</span></span> 

## <a name="dictation"></a><span data-ttu-id="bbe39-196">Диктовка</span><span class="sxs-lookup"><span data-stu-id="bbe39-196">Dictation</span></span>

<span data-ttu-id="bbe39-197">Вместо ввода с помощью [воздушных](gaze-and-commit.md#composite-gestures)наработок речь может оказаться более эффективной для ввода текста в приложение.</span><span class="sxs-lookup"><span data-stu-id="bbe39-197">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="bbe39-198">Это может значительно ускорить ввод данных с меньшими усилиями для пользователя.</span><span class="sxs-lookup"><span data-stu-id="bbe39-198">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="bbe39-199">![Диктовка речи начинается с нажатия кнопки микрофона](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="bbe39-199">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="bbe39-200">*Диктовка речи начинается с нажатия кнопки микрофона на клавиатуре*</span><span class="sxs-lookup"><span data-stu-id="bbe39-200">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="bbe39-201">В любой момент, когда найдутся неактивные клавиатура, можно переключиться в режим диктовки вместо ввода.</span><span class="sxs-lookup"><span data-stu-id="bbe39-201">Anytime the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="bbe39-202">Чтобы начать работу, выберите микрофон на стороне текстового поля ввода.</span><span class="sxs-lookup"><span data-stu-id="bbe39-202">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="bbe39-203">Добавление в приложение голосовых команд</span><span class="sxs-lookup"><span data-stu-id="bbe39-203">Adding voice commands to your app</span></span>

<span data-ttu-id="bbe39-204">Рассмотрите возможность добавления голосовых команд при создании любого взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="bbe39-204">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="bbe39-205">Voice — это мощный способ управления системой и приложениями.</span><span class="sxs-lookup"><span data-stu-id="bbe39-205">Voice is a powerful way control the system and apps.</span></span> <span data-ttu-id="bbe39-206">Так как пользователи говорят с разными разновидностями диалектов и диакритических знаков, правильное нажатие ключевых слов распознавания речи гарантирует, что команды пользователей будут интерпретироваться неоднозначно.</span><span class="sxs-lookup"><span data-stu-id="bbe39-206">Because users speak with different kinds of dialects and accents, proper choice of speech keywords will make sure your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="bbe39-207">Советы и рекомендации</span><span class="sxs-lookup"><span data-stu-id="bbe39-207">Best practices</span></span>

<span data-ttu-id="bbe39-208">Ниже приведены некоторые рекомендации, которые помогут облегчить распознавание речи.</span><span class="sxs-lookup"><span data-stu-id="bbe39-208">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="bbe39-209">**Используйте краткие команды**. По возможности выбирайте ключевые слова из двух или более слогов.</span><span class="sxs-lookup"><span data-stu-id="bbe39-209">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="bbe39-210">В односложных словах лица с разными акцентами обычно используют разные гласные.</span><span class="sxs-lookup"><span data-stu-id="bbe39-210">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="bbe39-211">Пример: "воспроизведение видео" лучше, чем "Воспроизвести текущее выбранное видео"</span><span class="sxs-lookup"><span data-stu-id="bbe39-211">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="bbe39-212">**Используйте простой словарь** — пример: "показывать Примечание" лучше, чем "Показывать панель"</span><span class="sxs-lookup"><span data-stu-id="bbe39-212">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="bbe39-213">Убедитесь, **что команды не являются обратимыми** . Убедитесь, что все действия голосовых команд являются необратимыми, и их можно легко отменить в случае, если другой человек говорит о том, что пользователь случайно запускает команду.</span><span class="sxs-lookup"><span data-stu-id="bbe39-213">**Make sure commands are non-destructive** - Make sure any speech command actions are non-destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="bbe39-214">**Избегайте аналогичных команд звука** — Избегайте регистрации нескольких голосовых команд, которые похожи на похожие.</span><span class="sxs-lookup"><span data-stu-id="bbe39-214">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound similar.</span></span> <span data-ttu-id="bbe39-215">Пример: "другие" и "показывать магазин" могут быть похожи на звук.</span><span class="sxs-lookup"><span data-stu-id="bbe39-215">Example: "Show more" and "Show store" can be similar sounding.</span></span>
* <span data-ttu-id="bbe39-216">**Отмените регистрацию приложения, если оно не используется** . Если ваше приложение находится не в состоянии, в котором определена допустимая Голосовая команда, рассмотрите возможность отмены регистрации, чтобы другие команды не перепутаться.</span><span class="sxs-lookup"><span data-stu-id="bbe39-216">**Unregister your app when not it uses** - When your app isn't in a state in which a particular speech command is valid, consider unregistering it so that other commands aren't confused for that one.</span></span>
* <span data-ttu-id="bbe39-217">**Протестируйте с разными акцентами.** Протестируйте приложение с пользователями с разными акцентами.</span><span class="sxs-lookup"><span data-stu-id="bbe39-217">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="bbe39-218">**Обеспечьте согласованность голосовых команд.** Если команда "Назад" переводит на предыдущую страницу, поддерживайте это поведение в своих приложениях.</span><span class="sxs-lookup"><span data-stu-id="bbe39-218">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="bbe39-219">**Избегайте использования системных команд** — следующие команды зарезервированы для системы, поэтому не используйте их в приложениях:</span><span class="sxs-lookup"><span data-stu-id="bbe39-219">**Avoid using system commands** - The following voice commands are reserved for the system, so avoid using them in your applications:</span></span>
   * <span data-ttu-id="bbe39-220">"Привет, Кортана!".</span><span class="sxs-lookup"><span data-stu-id="bbe39-220">"Hey Cortana"</span></span>
   * <span data-ttu-id="bbe39-221">"Выбрать"</span><span class="sxs-lookup"><span data-stu-id="bbe39-221">"Select"</span></span>
   * <span data-ttu-id="bbe39-222">"Перейти к запуску"</span><span class="sxs-lookup"><span data-stu-id="bbe39-222">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="bbe39-223">Преимущества речевого ввода</span><span class="sxs-lookup"><span data-stu-id="bbe39-223">Advantages of voice input</span></span>

<span data-ttu-id="bbe39-224">Голосовой ввод — это естественный способ сообщить о наших намерениях.</span><span class="sxs-lookup"><span data-stu-id="bbe39-224">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="bbe39-225">Речь особенно хороша при **обходе** интерфейса, поскольку она может помочь пользователям в устранении нескольких шагов интерфейса.</span><span class="sxs-lookup"><span data-stu-id="bbe39-225">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface.</span></span> <span data-ttu-id="bbe39-226">Пользователь может сказать "вернуться назад" при просмотре веб-страницы вместо того, чтобы приступать к работе и нажать кнопку "назад" в приложении.</span><span class="sxs-lookup"><span data-stu-id="bbe39-226">A user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app.</span></span> <span data-ttu-id="bbe39-227">Это небольшое время сохранения имеет мощный **эмоциональномный результат** на восприятии пользователя и дает им небольшой объем суперсовременные.</span><span class="sxs-lookup"><span data-stu-id="bbe39-227">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="bbe39-228">Использование голосовой связи — это также удобный метод ввода, когда наши руки заняты или когда нам предстоит выполнить **несколько заданий**.</span><span class="sxs-lookup"><span data-stu-id="bbe39-228">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="bbe39-229">На устройствах, где ввод с клавиатуры является сложной возможностью, **Диктовка голоса** может быть эффективным альтернативным способом ввода текста.</span><span class="sxs-lookup"><span data-stu-id="bbe39-229">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="bbe39-230">Наконец, в некоторых случаях, когда **диапазон точности** для взгляда и жеста ограничен, Voice может помочь в неоднозначности намерений пользователя.</span><span class="sxs-lookup"><span data-stu-id="bbe39-230">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="bbe39-231">**Преимущества использования голоса для пользователя**</span><span class="sxs-lookup"><span data-stu-id="bbe39-231">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="bbe39-232">Экономия времени — конечная цель достигается намного эффективнее.</span><span class="sxs-lookup"><span data-stu-id="bbe39-232">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="bbe39-233">Сокращение усилий — задания выполняются намного быстрее и не требуют значительных усилий.</span><span class="sxs-lookup"><span data-stu-id="bbe39-233">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="bbe39-234">Облегчение восприятия информации — это интуитивно понятно, легко выучить и запомнить.</span><span class="sxs-lookup"><span data-stu-id="bbe39-234">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="bbe39-235">Это основе социотехники приемлемое — оно должно попадать в соответствие с социальную нормами поведения.</span><span class="sxs-lookup"><span data-stu-id="bbe39-235">It's socially acceptable - it should fit in with societal norms of behavior.</span></span>
* <span data-ttu-id="bbe39-236">Это установившаяся практика — использование голосовой связи легко может стать привычным поведением.</span><span class="sxs-lookup"><span data-stu-id="bbe39-236">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="bbe39-237">Проблемы с голосовым вводом</span><span class="sxs-lookup"><span data-stu-id="bbe39-237">Challenges for voice input</span></span>

<span data-ttu-id="bbe39-238">Хотя речевой ввод отлично подходит для многих разных приложений, он также сталкивается с несколькими проблемами.</span><span class="sxs-lookup"><span data-stu-id="bbe39-238">While voice input is great for many different applications, it also faces several challenges.</span></span> <span data-ttu-id="bbe39-239">Понимание преимуществ и трудностей, связанных с голосовыми вводами, позволяет разработчикам приложений более разумно выбирать способ и время использования речевого ввода и создавать превосходные возможности для пользователей.</span><span class="sxs-lookup"><span data-stu-id="bbe39-239">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="bbe39-240">**Речевой ввод для непрерывного элемента управления вводом** Один из них является детализированным элементом управления.</span><span class="sxs-lookup"><span data-stu-id="bbe39-240">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="bbe39-241">Например, пользователю может потребоваться изменить свой том в своем музыкальном приложении.</span><span class="sxs-lookup"><span data-stu-id="bbe39-241">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="bbe39-242">Она может сказать «громче», но не ясно, сколько громкости система должна сделать тому.</span><span class="sxs-lookup"><span data-stu-id="bbe39-242">She can say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="bbe39-243">Пользователь может сказать: «сделайте его немного громче», но «немного» — трудность.</span><span class="sxs-lookup"><span data-stu-id="bbe39-243">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="bbe39-244">Перемещение и масштабирование голограмм с помощью голоса также усложняется.</span><span class="sxs-lookup"><span data-stu-id="bbe39-244">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="bbe39-245">**Надежность распознавания речевого ввода** Хотя системы ввода голоса становятся лучше и эффективнее, иногда они могут неправильно слышать и интерпретировать голосовую команду.</span><span class="sxs-lookup"><span data-stu-id="bbe39-245">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="bbe39-246">Ключом является устранение проблемы в приложении.</span><span class="sxs-lookup"><span data-stu-id="bbe39-246">The key is to address the challenge in your application.</span></span> <span data-ttu-id="bbe39-247">Отправляйте свои отзывы пользователям, когда система прослушивается и что понимается системой, что позволяет понять потенциальные проблемы, связанные с распознаванием речи пользователей.</span><span class="sxs-lookup"><span data-stu-id="bbe39-247">Provide feedback to your users when the system is listening and what the system understood clarifies potential issues understanding the users' speech.</span></span>  

<span data-ttu-id="bbe39-248">**Ввод голоса в общих пространствах** Возможно, голоса не основе социотехники в сферах, к которым вы предоставляете доступ другим пользователям.</span><span class="sxs-lookup"><span data-stu-id="bbe39-248">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="bbe39-249">Вот несколько примеров:</span><span class="sxs-lookup"><span data-stu-id="bbe39-249">Here are a few examples:</span></span>
* <span data-ttu-id="bbe39-250">Пользователь может не захотеть беспокоить других пользователей (например, в тихой библиотеке или в общем офисе).</span><span class="sxs-lookup"><span data-stu-id="bbe39-250">The user may not want to disturb others (for example, in a quiet library or shared office)</span></span>
* <span data-ttu-id="bbe39-251">Пользователи могут видеть, что речь идет о себе в общедоступной,</span><span class="sxs-lookup"><span data-stu-id="bbe39-251">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="bbe39-252">Пользователь может неудобно диктовать личное или конфиденциальное сообщение (включая пароли), пока другие прослушивают</span><span class="sxs-lookup"><span data-stu-id="bbe39-252">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="bbe39-253">**Голосовое ввод уникальных или неизвестных слов** Проблемы, возникающие при вводе голоса, также поступают, когда пользователи определяют слова, которые могут быть неизвестны для системы, например псевдонимы, определенные сленговых выражений слова или аббревиатуры.</span><span class="sxs-lookup"><span data-stu-id="bbe39-253">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words, or abbreviations.</span></span> 

<span data-ttu-id="bbe39-254">**Обучение голосовым командам** Хотя конечная цель заключается в естественном противоречии системе, часто приложения по-прежнему используют определенные предварительно определенные команды.</span><span class="sxs-lookup"><span data-stu-id="bbe39-254">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="bbe39-255">Задача, связанная с значительным набором голосовых команд, заключается в том, как научиться выполнять их без перегрузки пользователя и как помочь пользователю в их использовании.</span><span class="sxs-lookup"><span data-stu-id="bbe39-255">A challenge associated with a significant set of voice commands is how to teach them without overloading the user and how to help the user to keep them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="bbe39-256">Состояния обратной связи голосовых команд</span><span class="sxs-lookup"><span data-stu-id="bbe39-256">Voice feedback states</span></span>

<span data-ttu-id="bbe39-257">При правильном применении голосовых команд пользователь понимает, **что он может сказать, и получает обратную связь о том,** что система **услышала его правильно**.</span><span class="sxs-lookup"><span data-stu-id="bbe39-257">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="bbe39-258">Эти два сигнала придают пользователю уверенность в правильности выбора голосовых команд в качестве основного метода ввода.</span><span class="sxs-lookup"><span data-stu-id="bbe39-258">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="bbe39-259">Ниже приведена схема, показывающая, что происходит с курсором после распознавания голосовой команды и как он сообщает это пользователю.</span><span class="sxs-lookup"><span data-stu-id="bbe39-259">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="bbe39-260">![1. состояние обычного курсора](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="bbe39-260">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="bbe39-261">**1. состояние обычного курсора**</span><span class="sxs-lookup"><span data-stu-id="bbe39-261">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="bbe39-262">![2. сообщает о голосовом отзыве, а затем исчезает](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="bbe39-262">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="bbe39-263">**2. сообщает о голосовом отзыве, а затем исчезает**</span><span class="sxs-lookup"><span data-stu-id="bbe39-263">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="bbe39-264">![3-5.</span><span class="sxs-lookup"><span data-stu-id="bbe39-264">![\*3.</span></span> <span data-ttu-id="bbe39-265">Состояние обычного курсора](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="bbe39-265">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="bbe39-266">**3. возвращается к обычному состоянию курсора**</span><span class="sxs-lookup"><span data-stu-id="bbe39-266">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="bbe39-267">Главное, что пользователю следует знать о "речи" в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="bbe39-267">Top things users should know about "speech" in mixed reality</span></span>

* <span data-ttu-id="bbe39-268">Скажите **«SELECT»** при нацеливании на кнопку (это можно использовать в любом месте для выбора кнопки).</span><span class="sxs-lookup"><span data-stu-id="bbe39-268">Say **"Select"** while targeting a button (you can use this anywhere to select a button).</span></span>
* <span data-ttu-id="bbe39-269">Вы можете произнести **имя метки кнопки панели приложения** в некоторых приложениях, чтобы выполнить действие.</span><span class="sxs-lookup"><span data-stu-id="bbe39-269">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="bbe39-270">Например, при просмотре приложения пользователь может сказать команду "Удалить", чтобы удалить приложение из мира (это экономит время от необходимости выбора его вручную).</span><span class="sxs-lookup"><span data-stu-id="bbe39-270">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to select it with your hand).</span></span>
* <span data-ttu-id="bbe39-271">Вы можете начать прослушивание Кортаны, выполнив слово **"Привет, Кортана!".**</span><span class="sxs-lookup"><span data-stu-id="bbe39-271">You can start Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="bbe39-272">Вы можете задавать ей вопросы ("Привет, Кортана, какая высота Эйфелевой башни"), попросить ее открыть приложение ("Привет, Кортана, открой Netflix") или попросить ее открыть меню "Пуск" ("Привет, Кортана, открой домашнюю страницу") и многое другое.</span><span class="sxs-lookup"><span data-stu-id="bbe39-272">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="bbe39-273">Распространенные вопросы пользователей о голосовых командах</span><span class="sxs-lookup"><span data-stu-id="bbe39-273">Common questions and concerns users have about voice</span></span>

* <span data-ttu-id="bbe39-274">Что я могу сказать?</span><span class="sxs-lookup"><span data-stu-id="bbe39-274">What can I say?</span></span>
* <span data-ttu-id="bbe39-275">Как узнать, что система услышала меня правильно?</span><span class="sxs-lookup"><span data-stu-id="bbe39-275">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="bbe39-276">Система продолжает неправильно интерпретировать мои голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="bbe39-276">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="bbe39-277">Она не реагирует, когда я даю ей голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="bbe39-277">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="bbe39-278">Она неправильно реагирует, когда я даю ей голосовые команды.</span><span class="sxs-lookup"><span data-stu-id="bbe39-278">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="bbe39-279">Как нацеливать голос на конкретное приложение или команду приложения?</span><span class="sxs-lookup"><span data-stu-id="bbe39-279">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="bbe39-280">Можно ли использовать голос для различных команд в голографическом кадре в HoloLens?</span><span class="sxs-lookup"><span data-stu-id="bbe39-280">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="bbe39-281">Связь</span><span class="sxs-lookup"><span data-stu-id="bbe39-281">Communication</span></span>

<span data-ttu-id="bbe39-282">Для приложений, которые хотят воспользоваться преимуществами настраиваемых параметров обработки ввода звука, предоставляемых HoloLens, важно понимать различные [категории звуковых потоков](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) , которые может использовать приложение.</span><span class="sxs-lookup"><span data-stu-id="bbe39-282">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it's important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="bbe39-283">Windows 10 поддерживает несколько различных категорий потоков, и HoloLens использует три из них для оптимизации качества звука микрофона, предназначенных для речи, обмена данными и других, которые могут использоваться для воспроизведения звука в окружающей среде (то есть «видеокамер»).</span><span class="sxs-lookup"><span data-stu-id="bbe39-283">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication, and other, which can be used for ambient environment audio capture (that is, "camcorder") scenarios.</span></span>
* <span data-ttu-id="bbe39-284">Категория AudioCategory_Communications Stream настроена для сценариев качества вызова и речевого сопровождения и предоставляет клиенту 24-разрядный моно поток на входе пользователя в 16-кГц.</span><span class="sxs-lookup"><span data-stu-id="bbe39-284">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16-kHz 24-bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="bbe39-285">Категория AudioCategory_Speechного потока настроена для обработчика речи HoloLens (Windows) и предоставляет его 24-битный моно поток от голоса пользователя.</span><span class="sxs-lookup"><span data-stu-id="bbe39-285">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16-kHz 24-bit mono stream of the user's voice.</span></span> <span data-ttu-id="bbe39-286">При необходимости эта категория может использоваться сторонними обработчиками речи.</span><span class="sxs-lookup"><span data-stu-id="bbe39-286">This category can be used by third-party speech engines if needed.</span></span>
* <span data-ttu-id="bbe39-287">Категория AudioCategory_Other Stream настраивается для записи звука в окружающей среде и предоставляет клиенту 24-разрядный стереофонический аудиопоток 48 кГц.</span><span class="sxs-lookup"><span data-stu-id="bbe39-287">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48-kHz 24-bit stereo audio stream.</span></span>

<span data-ttu-id="bbe39-288">Вся эта обработка аудио аппаратного ускорения означает, что функции заменяют гораздо меньше энергии, чем при выполнении такой же обработки на ЦП HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bbe39-288">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="bbe39-289">Избегайте выполнения других системных входных данных на ЦП, чтобы максимально увеличить время работы батареи системы и воспользоваться преимуществами встроенной, развернутой обработки звукового ввода.</span><span class="sxs-lookup"><span data-stu-id="bbe39-289">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built-in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="bbe39-290">Языки</span><span class="sxs-lookup"><span data-stu-id="bbe39-290">Languages</span></span>

<span data-ttu-id="bbe39-291">HoloLens 2 [поддерживает несколько языков](https://docs.microsoft.com/hololens/hololens2-language-support).</span><span class="sxs-lookup"><span data-stu-id="bbe39-291">HoloLens 2 [supports multiple languages](https://docs.microsoft.com/hololens/hololens2-language-support).</span></span> <span data-ttu-id="bbe39-292">Помните, что речевые команды всегда будут выполняться в языке интерфейса системы, даже если установлено несколько клавиатур или если приложения пытаются создать распознаватель речи на другом языке.</span><span class="sxs-lookup"><span data-stu-id="bbe39-292">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="bbe39-293">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="bbe39-293">Troubleshooting</span></span>

<span data-ttu-id="bbe39-294">Если у вас возникли проблемы с помощью команды "выбрать" и "Привет, Кортана", попробуйте переместиться в скрытое место, отключив его от источника шума или нажимая звук.</span><span class="sxs-lookup"><span data-stu-id="bbe39-294">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="bbe39-295">В настоящее время все распознавание речи в HoloLens настраивается и оптимизируется специально для собственных докладчиков США английского.</span><span class="sxs-lookup"><span data-stu-id="bbe39-295">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="bbe39-296">В выпуске Windows Mixed Reality для выпуска 2017 логика управления конечными точками звука будет работать нормально (бессрочно) после выхода и возврата на Рабочий стол компьютера после первоначального подключения ХМД.</span><span class="sxs-lookup"><span data-stu-id="bbe39-296">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="bbe39-297">Перед первым выходом и входом в систему после ВМР OOBE пользователь может столкнуться с различными функциями аудио, начиная с отсутствия звука, в зависимости от того, как система была настроена перед первым подключением к ХМД.</span><span class="sxs-lookup"><span data-stu-id="bbe39-297">Before that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up before connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="bbe39-298">Ввод голоса в МРТК (набор средств для смешанной реальности) для Unity</span><span class="sxs-lookup"><span data-stu-id="bbe39-298">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="bbe39-299">С помощью **[мртк](https://github.com/Microsoft/MixedRealityToolkit-Unity)** можно легко назначить голосовые команды для любых объектов.</span><span class="sxs-lookup"><span data-stu-id="bbe39-299">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="bbe39-300">Используйте **профиль ввода речи** мртк для определения ключевых слов.</span><span class="sxs-lookup"><span data-stu-id="bbe39-300">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="bbe39-301">Назначая сценарий **спичинпусандлер** , можно сделать так, чтобы любой объект отвечал на ключевые слова, определенные в профиле речевого ввода.</span><span class="sxs-lookup"><span data-stu-id="bbe39-301">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="bbe39-302">Спичинпусандлер также предоставляет метку подтверждения речи для улучшения достоверности пользователя.</span><span class="sxs-lookup"><span data-stu-id="bbe39-302">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="bbe39-303">Команда МРТК-Voice</span><span class="sxs-lookup"><span data-stu-id="bbe39-303">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)

---

## <a name="see-also"></a><span data-ttu-id="bbe39-304">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="bbe39-304">See also</span></span>

* [<span data-ttu-id="bbe39-305">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="bbe39-305">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="bbe39-306">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="bbe39-306">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="bbe39-307">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="bbe39-307">Voice input in DirectX</span></span>](../develop/native/voice-input-in-directx.md)
* [<span data-ttu-id="bbe39-308">Голосовой ввод в Unity</span><span class="sxs-lookup"><span data-stu-id="bbe39-308">Voice input in Unity</span></span>](../develop/unity/voice-input-in-unity.md)
