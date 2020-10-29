---
title: Голосовой ввод в DirectX
description: В этой статье объясняется, как реализовать голосовые команды и небольшие фразы и распознавание предложений в приложении DirectX для Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Пошаговое руководство, голосовая команда, фраза, распознавание, речь, DirectX, платформа, Кортана, Windows Mixed Reality
ms.openlocfilehash: bdd92f79b3dd9677ac5c2c64e532978477ac5bca
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691465"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="29eea-104">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="29eea-104">Voice input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="29eea-105">Эта статья связана с устаревшими собственными API-интерфейсами WinRT.</span><span class="sxs-lookup"><span data-stu-id="29eea-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="29eea-106">Для новых проектов собственных приложений рекомендуется использовать **[API опенкср](openxr-getting-started.md)** .</span><span class="sxs-lookup"><span data-stu-id="29eea-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)** .</span></span>

<span data-ttu-id="29eea-107">В этой статье объясняется, как реализовать [голосовые команды](../../design/voice-input.md) , а также распознавание строчных фраз и предложений в приложении DirectX для Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="29eea-107">This article explains how to implement [voice commands](../../design/voice-input.md) plus small-phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="29eea-108">В фрагментах кода в этой статье используется C++/CX вместо C + +17, совместимого с C++/WinRT, который используется в [шаблоне проекта C++ holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="29eea-108">The code snippets in this article use C++/CX rather than C++17-compliant C++/WinRT, which is used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="29eea-109">Понятия эквивалентны для проекта C++/WinRT, но необходимо преобразовать код.</span><span class="sxs-lookup"><span data-stu-id="29eea-109">The concepts are equivalent for a C++/WinRT project, but you need to translate the code.</span></span>

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a><span data-ttu-id="29eea-110">Использование Спичрекогнизер для непрерывного распознавания речи</span><span class="sxs-lookup"><span data-stu-id="29eea-110">Use SpeechRecognizer for continuous speech recognition</span></span>

<span data-ttu-id="29eea-111">В этом разделе описывается использование непрерывного распознавания речи для включения голосовых команд в приложении.</span><span class="sxs-lookup"><span data-stu-id="29eea-111">This section describes how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="29eea-112">В этом пошаговом руководстве используется код из примера [холографиквоицеинпут](https://go.microsoft.com/fwlink/p/?LinkId=844964) .</span><span class="sxs-lookup"><span data-stu-id="29eea-112">This walk-through uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) sample.</span></span> <span data-ttu-id="29eea-113">При запуске образца говорите с именем одной из команд зарегистрированного цвета, чтобы изменить цвет вращающегося куба.</span><span class="sxs-lookup"><span data-stu-id="29eea-113">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="29eea-114">Сначала создайте новый экземпляр *Windows:: Media:: спичрекогнитион:: спичрекогнизер* .</span><span class="sxs-lookup"><span data-stu-id="29eea-114">First, create a new *Windows::Media::SpeechRecognition::SpeechRecognizer* instance.</span></span>

<span data-ttu-id="29eea-115">Из *холографиквоицеинпутсамплемаин:: креатеспичконстраинтсфоркуррентстате* :</span><span class="sxs-lookup"><span data-stu-id="29eea-115">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState* :</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="29eea-116">Создайте список речевых команд для распознавателя для прослушивания.</span><span class="sxs-lookup"><span data-stu-id="29eea-116">Create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="29eea-117">Здесь мы создаем набор команд для изменения цвета голограммы.</span><span class="sxs-lookup"><span data-stu-id="29eea-117">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="29eea-118">Для удобства мы также создадим данные, которые будут использоваться для команд позже.</span><span class="sxs-lookup"><span data-stu-id="29eea-118">For convenience, we also create the data that we'll use for the commands later.</span></span>

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

<span data-ttu-id="29eea-119">Для указания команд можно использовать фонетические слова, которые могут отсутствовать в словаре.</span><span class="sxs-lookup"><span data-stu-id="29eea-119">You can use phonetic words that might not be in a dictionary to specify commands.</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="29eea-120">Чтобы загрузить список команд в список ограничений для распознавателя речи, используйте объект [спичрекогнитионлистконстраинт](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) .</span><span class="sxs-lookup"><span data-stu-id="29eea-120">To load the commands list into the list of constraints for the speech recognizer use a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

<span data-ttu-id="29eea-121">Подпишитесь на событие [ресултженератед](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) в [спичконтинуаусрекогнитионсессион](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)распознавателя речи.</span><span class="sxs-lookup"><span data-stu-id="29eea-121">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="29eea-122">Это событие уведомляет ваше приложение о том, что одна из команд распознана.</span><span class="sxs-lookup"><span data-stu-id="29eea-122">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="29eea-123">Обработчик событий *онресултженератед* получает данные события в экземпляре [спичконтинуаусрекогнитионресултженератедевентаргс](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) .</span><span class="sxs-lookup"><span data-stu-id="29eea-123">Your *OnResultGenerated* event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="29eea-124">Если достоверность превышает заданное пороговое значение, приложение должно отметить, что событие произошло.</span><span class="sxs-lookup"><span data-stu-id="29eea-124">If the confidence is greater than the threshold that you defined, your app should note that the event happened.</span></span> <span data-ttu-id="29eea-125">Сохраните данные события, чтобы их можно было использовать в последующем цикле обновления.</span><span class="sxs-lookup"><span data-stu-id="29eea-125">Save the event data so that you can use it in a subsequent update loop.</span></span>

<span data-ttu-id="29eea-126">Из *холографиквоицеинпутсамплемаин. cpp* :</span><span class="sxs-lookup"><span data-stu-id="29eea-126">From *HolographicVoiceInputSampleMain.cpp* :</span></span>

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

<span data-ttu-id="29eea-127">В нашем примере кода мы изменим цвет для кубика с голограммой в соответствии с пользовательской командой.</span><span class="sxs-lookup"><span data-stu-id="29eea-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="29eea-128">Из *холографиквоицеинпутсамплемаин:: Update* :</span><span class="sxs-lookup"><span data-stu-id="29eea-128">From *HolographicVoiceInputSampleMain::Update* :</span></span>

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-one-shot-recognition"></a><span data-ttu-id="29eea-129">Использовать распознавание "один раз"</span><span class="sxs-lookup"><span data-stu-id="29eea-129">Use "one-shot" recognition</span></span>

<span data-ttu-id="29eea-130">Можно настроить распознавание речи для прослушивания фраз или предложений, которые говорит пользователь.</span><span class="sxs-lookup"><span data-stu-id="29eea-130">You can configure a speech recognizer to listen for phrases or sentences that the user speaks.</span></span> <span data-ttu-id="29eea-131">В этом случае мы применяем *спичрекогнитионтопикконстраинт* , который сообщает распознавателю распознавания речи, какой тип входных данных следует рассчитывать.</span><span class="sxs-lookup"><span data-stu-id="29eea-131">In this case, we apply a *SpeechRecognitionTopicConstraint* that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="29eea-132">Ниже приведен рабочий процесс приложения для этого сценария.</span><span class="sxs-lookup"><span data-stu-id="29eea-132">Here's an app workflow for this scenario:</span></span>
1. <span data-ttu-id="29eea-133">Приложение создает Спичрекогнизер, предоставляет запросы пользовательского интерфейса и начинает прослушивание произнесенной команды.</span><span class="sxs-lookup"><span data-stu-id="29eea-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a spoken command.</span></span>
2. <span data-ttu-id="29eea-134">Пользователь говорит о фразе или предложении.</span><span class="sxs-lookup"><span data-stu-id="29eea-134">The user speaks a phrase or sentence.</span></span>
3. <span data-ttu-id="29eea-135">Выполняется распознавание речи пользователя, и результат возвращается в приложение.</span><span class="sxs-lookup"><span data-stu-id="29eea-135">Recognition of the user's speech occurs, and a result is returned to the app.</span></span> <span data-ttu-id="29eea-136">На этом этапе приложение должно предоставить запрос пользовательского интерфейса, чтобы указать, что произошло распознавание.</span><span class="sxs-lookup"><span data-stu-id="29eea-136">At this point, your app should provide a UI prompt to indicate that recognition has occurred.</span></span>
4. <span data-ttu-id="29eea-137">В зависимости от уровня достоверности, на который вы хотите ответить, и уровня достоверности результатов распознавания речи, приложение может обработать результат и ответить соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="29eea-137">Depending on the confidence level that you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="29eea-138">В этом разделе описывается создание Спичрекогнизер, компиляция ограничения и прослушивание речевого ввода.</span><span class="sxs-lookup"><span data-stu-id="29eea-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="29eea-139">Следующий код компилирует ограничение раздела, которое в этом случае оптимизировано для поиска в Интернете.</span><span class="sxs-lookup"><span data-stu-id="29eea-139">The following code compiles the topic constraint, which in this case is optimized for web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="29eea-140">Если компиляция выполнена, можно продолжить распознавание речи.</span><span class="sxs-lookup"><span data-stu-id="29eea-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

<span data-ttu-id="29eea-141">Затем результат возвращается приложению.</span><span class="sxs-lookup"><span data-stu-id="29eea-141">The result is then returned to the app.</span></span> <span data-ttu-id="29eea-142">Если у нас есть достаточная уверенность в результатах, мы можем обработать команду.</span><span class="sxs-lookup"><span data-stu-id="29eea-142">If we're confident enough in the result, we can process the command.</span></span> <span data-ttu-id="29eea-143">Этот пример кода обрабатывает результаты по крайней мере средней достоверности.</span><span class="sxs-lookup"><span data-stu-id="29eea-143">This code example processes results with at least medium confidence.</span></span>

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

<span data-ttu-id="29eea-144">При использовании распознавания речи Следите за исключениями, которые могут означать, что пользователь отключил микрофон в настройках конфиденциальности системы.</span><span class="sxs-lookup"><span data-stu-id="29eea-144">Whenever you use speech recognition, watch for exceptions that could indicate that the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="29eea-145">Это может произойти во время инициализации или распознавания.</span><span class="sxs-lookup"><span data-stu-id="29eea-145">This can happen during initialization or recognition.</span></span>

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

> [!NOTE]
> <span data-ttu-id="29eea-146">Существует несколько предопределенных [спичрекогнитионсценариос](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) , которые можно использовать для оптимизации распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="29eea-146">There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) that you can use to optimize speech recognition.</span></span>

* <span data-ttu-id="29eea-147">Чтобы оптимизировать для диктовки, используйте сценарий диктовки.</span><span class="sxs-lookup"><span data-stu-id="29eea-147">To optimize for dictation, use the dictation scenario.</span></span><br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* <span data-ttu-id="29eea-148">Для поиска в Интернете через речь используйте следующее ограничение для конкретного веб-сценария.</span><span class="sxs-lookup"><span data-stu-id="29eea-148">For speech web searches, use the following web-specific scenario constraint.</span></span>

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* <span data-ttu-id="29eea-149">Используйте ограничение формы для заполнения форм.</span><span class="sxs-lookup"><span data-stu-id="29eea-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="29eea-150">В этом случае лучше применить собственную грамматику, оптимизированную для заполнения формы.</span><span class="sxs-lookup"><span data-stu-id="29eea-150">In this case, it's best to apply your own grammar that's optimized for filling out the form.</span></span>

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* <span data-ttu-id="29eea-151">Вы можете предоставить собственную грамматику в формате SRGS.</span><span class="sxs-lookup"><span data-stu-id="29eea-151">You can provide your own grammar in the SRGS format.</span></span>

## <a name="use-continuous-recognition"></a><span data-ttu-id="29eea-152">Использовать непрерывное распознавание</span><span class="sxs-lookup"><span data-stu-id="29eea-152">Use continuous recognition</span></span>

<span data-ttu-id="29eea-153">Сведения о сценарии непрерывной диктовки см. в [примере кода речи Windows 10 UWP](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span><span class="sxs-lookup"><span data-stu-id="29eea-153">For the continuous-dictation scenario, see the [Windows 10 UWP speech code sample](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span></span>

## <a name="handle-quality-degradation"></a><span data-ttu-id="29eea-154">Обработано снижение качества</span><span class="sxs-lookup"><span data-stu-id="29eea-154">Handle quality degradation</span></span>

<span data-ttu-id="29eea-155">Условия среды иногда мешают распознаванию речи.</span><span class="sxs-lookup"><span data-stu-id="29eea-155">Environmental conditions sometimes interfere with speech recognition.</span></span> <span data-ttu-id="29eea-156">Например, комната может быть слишком шумным, или пользователь может говорить слишком громко.</span><span class="sxs-lookup"><span data-stu-id="29eea-156">For example, the room might be too noisy, or the user might speak too loudly.</span></span> <span data-ttu-id="29eea-157">Когда это возможно, API распознавания речи предоставляет сведения об условиях снижения качества.</span><span class="sxs-lookup"><span data-stu-id="29eea-157">Whenever possible, the speech recognition API provides information about the conditions that caused the quality degradation.</span></span> <span data-ttu-id="29eea-158">Эти сведения передаются в приложение с помощью события WinRT.</span><span class="sxs-lookup"><span data-stu-id="29eea-158">This information is pushed to your app through a WinRT event.</span></span> <span data-ttu-id="29eea-159">В следующем примере показано, как подписываться на это событие.</span><span class="sxs-lookup"><span data-stu-id="29eea-159">The following example shows  how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="29eea-160">В нашем примере кода данные условий записываются в консоль отладки.</span><span class="sxs-lookup"><span data-stu-id="29eea-160">In our code sample, we write the conditions information to the debug console.</span></span> <span data-ttu-id="29eea-161">Приложение может захотеть предоставить отзыв пользователю с помощью пользовательского интерфейса, синтеза речи и другого метода.</span><span class="sxs-lookup"><span data-stu-id="29eea-161">An app might want to provide feedback to the user through the UI, speech synthesis, and another method.</span></span> <span data-ttu-id="29eea-162">Или может потребоваться поведение по-разному, если речь прерывается за счет временного снижения качества.</span><span class="sxs-lookup"><span data-stu-id="29eea-162">Or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

<span data-ttu-id="29eea-163">Если вы не используете классы ссылок для создания приложения DirectX, необходимо отказаться от подписки на событие до выпуска или повторного создания распознавателя речи.</span><span class="sxs-lookup"><span data-stu-id="29eea-163">If you're not using ref classes to create your DirectX app, you must unsubscribe from the event before you release or recreate your speech recognizer.</span></span> <span data-ttu-id="29eea-164">В Холографикспичпромптсампле есть подпрограммы для прекращения распознавания и отмены подписки на события.</span><span class="sxs-lookup"><span data-stu-id="29eea-164">The HolographicSpeechPromptSample has a routine to stop recognition and unsubscribe from events.</span></span>

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a><span data-ttu-id="29eea-165">Использование синтеза речи для ввода звуковых запросов</span><span class="sxs-lookup"><span data-stu-id="29eea-165">Use speech synthesis to provide audible prompts</span></span>

<span data-ttu-id="29eea-166">В пошаговых примерах holographic речь используется синтез речи для предоставления пользователю инструкций.</span><span class="sxs-lookup"><span data-stu-id="29eea-166">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="29eea-167">В этом разделе показано, как создать пример синтезированного голоса, а затем воспроизвести его с помощью API аудио ХРТФ.</span><span class="sxs-lookup"><span data-stu-id="29eea-167">This section shows how to create a synthesized voice sample  and then play it back through the HRTF audio APIs.</span></span>

<span data-ttu-id="29eea-168">При запросе ввода фраз необходимо указать собственные голосовые запросы.</span><span class="sxs-lookup"><span data-stu-id="29eea-168">You should provide your own speech prompts when you request phrase input.</span></span> <span data-ttu-id="29eea-169">Кроме того, в запросах можно указать, когда голосовые команды могут быть полезны для сценария непрерывного распознавания.</span><span class="sxs-lookup"><span data-stu-id="29eea-169">Prompts can also help indicate when speech commands can be spoken for a continuous-recognition scenario.</span></span> <span data-ttu-id="29eea-170">В следующем примере показано, как использовать синтезатор речи для этого.</span><span class="sxs-lookup"><span data-stu-id="29eea-170">The following example demonstrates how to use a speech synthesizer to do this.</span></span> <span data-ttu-id="29eea-171">Можно также использовать предварительно записанный голосовый ролик, визуальный пользовательский интерфейс или другой индикатор того, что следует сказать, например в сценариях, где запрос не является динамическим.</span><span class="sxs-lookup"><span data-stu-id="29eea-171">You could also use a pre-recorded voice clip, a visual UI, or another indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="29eea-172">Сначала создайте объект Спичсинсесизер.</span><span class="sxs-lookup"><span data-stu-id="29eea-172">First, create the SpeechSynthesizer object.</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="29eea-173">Кроме того, требуется строка, содержащая текст для синтезирования.</span><span class="sxs-lookup"><span data-stu-id="29eea-173">You also need a string that includes the text to  synthesize.</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="29eea-174">Речь создается асинхронно через Синсесизетексттостреамасинк.</span><span class="sxs-lookup"><span data-stu-id="29eea-174">Speech is synthesized asynchronously through SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="29eea-175">Здесь мы начнем асинхронную задачу для синтезирования речи.</span><span class="sxs-lookup"><span data-stu-id="29eea-175">Here, we start an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="29eea-176">Синтез речи отправляется в виде потока байтов.</span><span class="sxs-lookup"><span data-stu-id="29eea-176">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="29eea-177">Мы можем использовать этот поток байтов для инициализации голоса XAudio2.</span><span class="sxs-lookup"><span data-stu-id="29eea-177">We can use that byte stream to initialize an XAudio2 voice.</span></span> <span data-ttu-id="29eea-178">Для наших примеров кода мы воспроизводим его как ХРТФ Audio.</span><span class="sxs-lookup"><span data-stu-id="29eea-178">For our holographic code samples, we play it back as an HRTF audio effect.</span></span>

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

<span data-ttu-id="29eea-179">Как и при распознавании речи, синтез речи создает исключение, если что-то пойдет не так.</span><span class="sxs-lookup"><span data-stu-id="29eea-179">As with speech recognition, speech synthesis throws an exception if something goes wrong.</span></span>

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a><span data-ttu-id="29eea-180">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="29eea-180">See also</span></span>
* [<span data-ttu-id="29eea-181">Разработка речевых приложений</span><span class="sxs-lookup"><span data-stu-id="29eea-181">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="29eea-182">Пример Спичрекогнитионандсинсесис</span><span class="sxs-lookup"><span data-stu-id="29eea-182">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
