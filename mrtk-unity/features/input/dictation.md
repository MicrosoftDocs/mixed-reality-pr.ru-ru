---
title: Диктовка
description: Докумментатион о записи аудиоклипов и получении транскрипции в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 520a667cc4b41f5e8f4373a7c901eb2458cd2d17
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176470"
---
# <a name="dictation"></a><span data-ttu-id="5984d-104">Диктовка</span><span class="sxs-lookup"><span data-stu-id="5984d-104">Dictation</span></span>

<span data-ttu-id="5984d-105">Диктовка позволяет пользователям записывать аудиоклипы и получать транскрипцию.</span><span class="sxs-lookup"><span data-stu-id="5984d-105">Dictation allows users to record audio clips and obtain a transcription.</span></span> <span data-ttu-id="5984d-106">Чтобы использовать его, убедитесь, что система диктовки зарегистрирована во *входном системном профиле*.</span><span class="sxs-lookup"><span data-stu-id="5984d-106">To use it make sure that a dictation system is registered in the *Input System Profile*.</span></span> <span data-ttu-id="5984d-107">**Windowsный поставщик входных данных диктофона** — это система диктовки, предоставляемая из комплекта, но для реализации можно создать альтернативные системы диктовки [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .</span><span class="sxs-lookup"><span data-stu-id="5984d-107">**Windows Dictation Input Provider** is the dictation system provided out of the box but alternative dictation systems can be created implementing [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem).</span></span>

## <a name="requirements"></a><span data-ttu-id="5984d-108">Требования</span><span class="sxs-lookup"><span data-stu-id="5984d-108">Requirements</span></span>

<span data-ttu-id="5984d-109">система диктовки использует [диктатионрекогнизер](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) Unity, который сам использует базовые интерфейсы api распознавания Windows для обработки диктовки.</span><span class="sxs-lookup"><span data-stu-id="5984d-109">The dictation system uses Unity's [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) which itself uses the underlying Windows speech APIs for handling dictation.</span></span> <span data-ttu-id="5984d-110">обратите внимание, что это означает, что эта функция имеется только на платформах на основе Windows.</span><span class="sxs-lookup"><span data-stu-id="5984d-110">Note that this implies that this feature is only present on Windows-based platforms.</span></span>

<span data-ttu-id="5984d-111">Для использования системы диктовки требуются возможности приложения "Интернет-клиент" и "микрофон" в [разделе плайерсеттингс-capabilities](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span><span class="sxs-lookup"><span data-stu-id="5984d-111">Usage of the Dictation system requires both the "Internet Client" and "Microphone" application capabilities in the [PlayerSettings - Capabilities section](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span></span>
<span data-ttu-id="5984d-112">дополнительные сведения о голосовом вводе в Unity см. в [Windows Mixed Reality документации](/windows/mixed-reality/voice-input-in-unity#dictation) .</span><span class="sxs-lookup"><span data-stu-id="5984d-112">See [Windows Mixed Reality Documentation](/windows/mixed-reality/voice-input-in-unity#dictation) for more details on voice input in Unity.</span></span>

## <a name="configuration"></a><span data-ttu-id="5984d-113">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="5984d-113">Configuration</span></span>

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

<span data-ttu-id="5984d-114">После настройки службы диктовки можно использовать [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) сценарий для запуска и завершения записи сеансов, а также получения результатов транскрипции через унитевентс.</span><span class="sxs-lookup"><span data-stu-id="5984d-114">Once you have a dictation service set up, you can use the [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script to start and stop recording sessions and obtain the transcription results via UnityEvents.</span></span>

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- <span data-ttu-id="5984d-115">**Гипотеза диктовки** создается по мере того, как пользователь сразу же говорит о том, что проводятся предварительные записи звука, полученные на данный момент.</span><span class="sxs-lookup"><span data-stu-id="5984d-115">**Dictation Hypothesis** is raised as the user speaks with early, rough transcriptions of the audio captured so far.</span></span>
- <span data-ttu-id="5984d-116">**Результат диктовки** создается в конце каждого предложения (т. е. когда пользователь приостанавливает работу) с завершающим обработкой звука, записываемого на данный момент.</span><span class="sxs-lookup"><span data-stu-id="5984d-116">**Dictation Result** is raised at the end of each sentence (i.e. when the user pauses) with the final transcription of the audio captured so far.</span></span>
- <span data-ttu-id="5984d-117">**Диктовка по завершении** создается в конце сеанса записи с полной и окончательной обработкой звука.</span><span class="sxs-lookup"><span data-stu-id="5984d-117">**Dictation Complete** is raised at the end of the recording session with the full, final transcription of the audio.</span></span>
- <span data-ttu-id="5984d-118">**Ошибка диктовки** возникает, чтобы сообщить об ошибках в службе диктофона.</span><span class="sxs-lookup"><span data-stu-id="5984d-118">**Dictation Error** is raised to inform of errors in the dictation service.</span></span> <span data-ttu-id="5984d-119">Транскрипция в этом случае содержит описание ошибки.</span><span class="sxs-lookup"><span data-stu-id="5984d-119">The transcription in this case contains a description of the error.</span></span>

## <a name="example-scene"></a><span data-ttu-id="5984d-120">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="5984d-120">Example scene</span></span>

<span data-ttu-id="5984d-121">В сцене **диктовки** в `MRTK/Examples/Demos/Input/Scenes/Dictation` показывает, какой `DictationHandler` сценарий используется.</span><span class="sxs-lookup"><span data-stu-id="5984d-121">**Dictation** scene in `MRTK/Examples/Demos/Input/Scenes/Dictation` shows the `DictationHandler` script in use.</span></span> <span data-ttu-id="5984d-122">Если требуется больший контроль, можно либо расширить этот скрипт, либо создать собственную реализацию [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) для получения событий диктовки напрямую.</span><span class="sxs-lookup"><span data-stu-id="5984d-122">If you need more control, you can either extend this script or create your own implementing [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) to receive dictation events directly.</span></span>

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
