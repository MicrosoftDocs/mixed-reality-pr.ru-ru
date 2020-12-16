---
title: Моделирование восприятия
description: Рекомендации по использованию библиотеки моделирования восприятия для автоматизации имитации входных данных для впечатляющих приложений
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, моделирование, тестирование
ms.openlocfilehash: 64028c3a1ad58cecfebc93aee325b73c3a6a649a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530395"
---
# <a name="perception-simulation"></a><span data-ttu-id="0ff18-104">Моделирование восприятия</span><span class="sxs-lookup"><span data-stu-id="0ff18-104">Perception simulation</span></span>

<span data-ttu-id="0ff18-105">Вы хотите создать автоматический тест для приложения?</span><span class="sxs-lookup"><span data-stu-id="0ff18-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="0ff18-106">Вы хотите, чтобы тесты переходили за пределы модульного тестирования на уровне компонентов и действительно протестировали свое приложение как можно более полное?</span><span class="sxs-lookup"><span data-stu-id="0ff18-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="0ff18-107">Имитация восприятия — это то, что вы ищете.</span><span class="sxs-lookup"><span data-stu-id="0ff18-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="0ff18-108">Библиотека моделирования восприятия отправляет в приложение пользовательские и мировые входные данные, что позволяет автоматизировать тесты.</span><span class="sxs-lookup"><span data-stu-id="0ff18-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="0ff18-109">Например, можно имитировать входные данные человека, который смотрит в конкретную, повторяемую, а затем использовать жест или контроллер движения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then use a gesture or motion controller.</span></span>

<span data-ttu-id="0ff18-110">Имитация восприятия может отправить смоделированные входные данные на физический HoloLens, эмулятор HoloLens (первый общий), эмулятор HoloLens 2 или компьютер с установленным порталом смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="0ff18-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (first gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="0ff18-111">Имитация восприятия обходит активные датчики на устройстве смешанной реальности и отправляет смоделированные входные данные приложениям, работающим на устройстве.</span><span class="sxs-lookup"><span data-stu-id="0ff18-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="0ff18-112">Приложения получают эти события ввода с помощью тех же API-интерфейсов, которые они всегда используют, и не могут сообщать о различиях между запуском с реальными датчиками и имитацией</span><span class="sxs-lookup"><span data-stu-id="0ff18-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus Perception Simulation.</span></span> <span data-ttu-id="0ff18-113">Имитация восприятия — это та же технология, которая используется эмуляторами HoloLens для отправки смоделированных входных данных на виртуальную машину HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ff18-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="0ff18-114">Чтобы приступить к использованию моделирования в коде, начните с создания объекта Иперцептионсимулатионманажер.</span><span class="sxs-lookup"><span data-stu-id="0ff18-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="0ff18-115">Из этого объекта можно выдавать команды для управления свойствами имитации "человека", включая позиционирование головной части, расположение руки и жесты.</span><span class="sxs-lookup"><span data-stu-id="0ff18-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span> <span data-ttu-id="0ff18-116">Можно также включить и управлять контроллерами движения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-116">You can also enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="0ff18-117">Настройка проекта Visual Studio для имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="0ff18-117">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="0ff18-118">[Установите эмулятор HoloLens](../install-the-tools.md) на компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="0ff18-118">[Install the HoloLens emulator](../install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="0ff18-119">Эмулятор включает библиотеки, используемые для имитации восприятия.</span><span class="sxs-lookup"><span data-stu-id="0ff18-119">The emulator includes the libraries you' use for Perception Simulation.</span></span>
2. <span data-ttu-id="0ff18-120">Создайте проект Visual Studio C# для настольных систем (проект консоли прекрасно работает, чтобы начать работу).</span><span class="sxs-lookup"><span data-stu-id="0ff18-120">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="0ff18-121">Добавьте в проект следующие двоичные файлы в виде ссылок (проект->добавить >ссылку...). Их можно найти в% ProgramFiles (x86)% \ Microsoft XDE \\ (версия), например **% ProgramFiles (x86)% \ Microsoft XDE \\ 10.0.18362.0** для эмулятора HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0ff18-121">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="0ff18-122">(Примечание. Хотя двоичные файлы являются частью эмулятора HoloLens 2, они также работают для Windows Mixed Reality на настольном компьютере.) конкретного.</span><span class="sxs-lookup"><span data-stu-id="0ff18-122">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="0ff18-123">Управляемая PerceptionSimulationManager.Interop.dll оболочка C# для имитации восприятия.</span><span class="sxs-lookup"><span data-stu-id="0ff18-123">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="0ff18-124">b.</span><span class="sxs-lookup"><span data-stu-id="0ff18-124">b.</span></span> <span data-ttu-id="0ff18-125">PerceptionSimulationRest.dll-Library для настройки канала связи веб-сокета с HoloLens или эмулятором.</span><span class="sxs-lookup"><span data-stu-id="0ff18-125">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="0ff18-126">c.</span><span class="sxs-lookup"><span data-stu-id="0ff18-126">c.</span></span> <span data-ttu-id="0ff18-127">SimulationStream.Interop.dll — общие типы для моделирования.</span><span class="sxs-lookup"><span data-stu-id="0ff18-127">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="0ff18-128">Добавьте в проект a двоичный PerceptionSimulationManager.dll реализации.</span><span class="sxs-lookup"><span data-stu-id="0ff18-128">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="0ff18-129">Сначала добавьте его в качестве двоичного файла в проект (проект->добавить->существующий элемент...). Сохраните его как ссылку, чтобы он не скопировал его в исходную папку проекта.</span><span class="sxs-lookup"><span data-stu-id="0ff18-129">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="0ff18-130">![Добавьте PerceptionSimulationManager.dll в проект как ссылку ](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="0ff18-130">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="0ff18-131">Затем убедитесь, что он скопирован в выходную папку при сборке.</span><span class="sxs-lookup"><span data-stu-id="0ff18-131">Then make sure that it gets copied to your output folder on build.</span></span> <span data-ttu-id="0ff18-132">Он находится на странице свойств двоичного файла.</span><span class="sxs-lookup"><span data-stu-id="0ff18-132">This is in the property sheet for the binary.</span></span> <span data-ttu-id="0ff18-133">![Пометьте PerceptionSimulationManager.dll для копирования в выходной каталог](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="0ff18-133">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="0ff18-134">Задайте для активной платформы решения x64.</span><span class="sxs-lookup"><span data-stu-id="0ff18-134">Set your active solution platform to x64.</span></span>  <span data-ttu-id="0ff18-135">(Используйте Configuration Manager, чтобы создать запись платформы для x64, если она еще не создана.)</span><span class="sxs-lookup"><span data-stu-id="0ff18-135">(Use the Configuration Manager to create a Platform entry for x64 if one doesn't already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="0ff18-136">Создание объекта Иперцептионсимулатион Manager</span><span class="sxs-lookup"><span data-stu-id="0ff18-136">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="0ff18-137">Для управления имитацией вы получаете обновления объектов, полученных из объекта Иперцептионсимулатионманажер.</span><span class="sxs-lookup"><span data-stu-id="0ff18-137">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="0ff18-138">Первым шагом является получение этого объекта и его подключение к целевому устройству или эмулятору.</span><span class="sxs-lookup"><span data-stu-id="0ff18-138">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="0ff18-139">Вы можете получить IP-адрес эмулятора, нажав кнопку на портале устройства на [панели инструментов](using-the-hololens-emulator.md) .</span><span class="sxs-lookup"><span data-stu-id="0ff18-139">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="0ff18-140">![Значок "открыть портал устройств" ](images/emulator-deviceportal.png) **откройте портал** устройств. Откройте портал устройств Windows для ОС HoloLens в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="0ff18-140">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="0ff18-141">Для Windows Mixed Reality это можно получить в приложении "Параметры" в разделе "обновление & безопасность", а затем "для разработчиков" в разделе "подключение с помощью:" раздела "Включение портала устройств".</span><span class="sxs-lookup"><span data-stu-id="0ff18-141">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="0ff18-142">Обязательно запишите IP-адрес и порт.</span><span class="sxs-lookup"><span data-stu-id="0ff18-142">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="0ff18-143">Во-первых, вы вызываете Рестсимулатионстреамсинк. Create для получения объекта Рестсимулатионстреамсинк.</span><span class="sxs-lookup"><span data-stu-id="0ff18-143">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="0ff18-144">Это целевое устройство или эмулятор, которым вы управляете HTTP-соединением.</span><span class="sxs-lookup"><span data-stu-id="0ff18-144">This is the target device or emulator that you'll control over an http connection.</span></span> <span data-ttu-id="0ff18-145">Команды будут переданы и обработаны на [портале устройств Windows](using-the-windows-device-portal.md) , работающем на устройстве или в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="0ff18-145">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="0ff18-146">Ниже приведены четыре параметра, которые необходимо создать для объекта.</span><span class="sxs-lookup"><span data-stu-id="0ff18-146">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="0ff18-147">URI URI — IP-адрес целевого устройства (например, " https://123.123.123.123 " или " https://123.123.123.123:50080 ").</span><span class="sxs-lookup"><span data-stu-id="0ff18-147">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="0ff18-148">System .NET. NetworkCredential Credentials — имя пользователя и пароль для подключения к [порталу устройств Windows](using-the-windows-device-portal.md) на целевом устройстве или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="0ff18-148">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="0ff18-149">Если вы подключаетесь к эмулятору через свой локальный адрес (например, 168.*.*. \*) на том же компьютере будут приниматься любые учетные данные.</span><span class="sxs-lookup"><span data-stu-id="0ff18-149">If you're connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="0ff18-150">bool обычная — true для обычного приоритета, false для низкого приоритета.</span><span class="sxs-lookup"><span data-stu-id="0ff18-150">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="0ff18-151">Обычно необходимо задать для этого параметра значение *true* для тестовых сценариев, что позволяет вашему тесту осуществлять управление.</span><span class="sxs-lookup"><span data-stu-id="0ff18-151">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="0ff18-152">Эмулятор и имитация Windows Mixed Reality используют соединения с низким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="0ff18-152">The emulator and Windows Mixed Reality simulation use low-priority connections.</span></span>  <span data-ttu-id="0ff18-153">Если в тесте также используется подключение с низким приоритетом, то последнее установленное соединение будет управляться.</span><span class="sxs-lookup"><span data-stu-id="0ff18-153">If your test also uses a low-priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="0ff18-154">Для отмены асинхронной операции маркера токена System. Threading. CancellationToken.</span><span class="sxs-lookup"><span data-stu-id="0ff18-154">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="0ff18-155">Во вторых, вы создадите Иперцептионсимулатионманажер.</span><span class="sxs-lookup"><span data-stu-id="0ff18-155">Second, you'll create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="0ff18-156">Это объект, используемый для управления имитацией.</span><span class="sxs-lookup"><span data-stu-id="0ff18-156">This is the object you use to control simulation.</span></span> <span data-ttu-id="0ff18-157">Это также необходимо сделать в асинхронном методе.</span><span class="sxs-lookup"><span data-stu-id="0ff18-157">This must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="0ff18-158">Управление имитируемым человеком</span><span class="sxs-lookup"><span data-stu-id="0ff18-158">Control the simulated Human</span></span>

<span data-ttu-id="0ff18-159">Иперцептионсимулатионманажер имеет свойство человеческого, которое возвращает объект Исимулатедхуман.</span><span class="sxs-lookup"><span data-stu-id="0ff18-159">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="0ff18-160">Для управления имитируемым человеком выполните операции с этим объектом.</span><span class="sxs-lookup"><span data-stu-id="0ff18-160">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="0ff18-161">Пример:</span><span class="sxs-lookup"><span data-stu-id="0ff18-161">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="0ff18-162">Простой пример консольного приложения C#</span><span class="sxs-lookup"><span data-stu-id="0ff18-162">Basic Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="0ff18-163">Расширенный пример консольного приложения C#</span><span class="sxs-lookup"><span data-stu-id="0ff18-163">Extended Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="0ff18-164">Примечание о 6-ДОФ контроллерах</span><span class="sxs-lookup"><span data-stu-id="0ff18-164">Note on 6-DOF controllers</span></span>

<span data-ttu-id="0ff18-165">Перед вызовом каких-либо свойств для методов смоделированного 6-ДОФ контроллера необходимо активировать контроллер.</span><span class="sxs-lookup"><span data-stu-id="0ff18-165">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="0ff18-166">Это приведет к исключению.</span><span class="sxs-lookup"><span data-stu-id="0ff18-166">Not doing so will result in an exception.</span></span>  <span data-ttu-id="0ff18-167">Начиная с Windows 10 Can 2019 обновление, смоделированные 6-ДОФ контроллеры можно установить и активировать, задав для свойства Status объекта Исимулатедсиксдофконтроллер значение Симулатедсиксдофконтроллерстатус. Active.</span><span class="sxs-lookup"><span data-stu-id="0ff18-167">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="0ff18-168">В обновлении Windows 10 октября 2018 и более ранних версиях необходимо отдельно установить смоделированный 6-ДОФ контроллер, вызвав средство Перцептионсимулатиондевице, расположенное в папке \Windows\System32..</span><span class="sxs-lookup"><span data-stu-id="0ff18-168">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="0ff18-169">Использование этого средства выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0ff18-169">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="0ff18-170">Например.</span><span class="sxs-lookup"><span data-stu-id="0ff18-170">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="0ff18-171">Поддерживаются следующие действия:</span><span class="sxs-lookup"><span data-stu-id="0ff18-171">Supported actions are:</span></span>
* <span data-ttu-id="0ff18-172">i = установить</span><span class="sxs-lookup"><span data-stu-id="0ff18-172">i = install</span></span>
* <span data-ttu-id="0ff18-173">q = запрос</span><span class="sxs-lookup"><span data-stu-id="0ff18-173">q = query</span></span>
* <span data-ttu-id="0ff18-174">r = удалить</span><span class="sxs-lookup"><span data-stu-id="0ff18-174">r = remove</span></span>

<span data-ttu-id="0ff18-175">Поддерживаются следующие экземпляры:</span><span class="sxs-lookup"><span data-stu-id="0ff18-175">Supported instances are:</span></span>
* <span data-ttu-id="0ff18-176">1 = левый 6-ДОФ контроллер</span><span class="sxs-lookup"><span data-stu-id="0ff18-176">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="0ff18-177">2 = правильный 6-ДОФ контроллер</span><span class="sxs-lookup"><span data-stu-id="0ff18-177">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="0ff18-178">Код выхода процесса будет указывать на успех (нулевое возвращаемое значение) или ошибку (ненулевое возвращаемое значение).</span><span class="sxs-lookup"><span data-stu-id="0ff18-178">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="0ff18-179">При использовании действия "q" для запроса того, установлен ли контроллер, возвращаемое значение будет равно нулю (0), если контроллер еще не установлен, или один (1), если контроллер установлен.</span><span class="sxs-lookup"><span data-stu-id="0ff18-179">When using the 'q' action to query whether a controller is installed, the return value will be zero (0) if the controller isn't already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="0ff18-180">При удалении контроллера в Windows 10 октября с обновлением 2018 или более ранней версии установите его состояние в OFF через API, а затем вызовите средство Перцептионсимулатиондевице.</span><span class="sxs-lookup"><span data-stu-id="0ff18-180">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="0ff18-181">Это средство необходимо запускать от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="0ff18-181">This tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="0ff18-182">Справочник по API</span><span class="sxs-lookup"><span data-stu-id="0ff18-182">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="0ff18-183">Microsoft. Перцептионсимулатион. Симулатеддевицетипе</span><span class="sxs-lookup"><span data-stu-id="0ff18-183">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="0ff18-184">Описывает тип имитации устройства</span><span class="sxs-lookup"><span data-stu-id="0ff18-184">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="0ff18-185">**Microsoft. Перцептионсимулатион. Симулатеддевицетипе. Reference**</span><span class="sxs-lookup"><span data-stu-id="0ff18-185">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="0ff18-186">Фиктивное эталонное устройство, используемое по умолчанию для Перцептионсимулатионманажер</span><span class="sxs-lookup"><span data-stu-id="0ff18-186">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="0ff18-187">Microsoft. Перцептионсимулатион. Хеадтраккермоде</span><span class="sxs-lookup"><span data-stu-id="0ff18-187">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="0ff18-188">Описывает режим «головной транспортер»</span><span class="sxs-lookup"><span data-stu-id="0ff18-188">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="0ff18-189">**Microsoft. Перцептионсимулатион. Хеадтраккермоде. Default**</span><span class="sxs-lookup"><span data-stu-id="0ff18-189">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="0ff18-190">Отслеживание головок по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0ff18-190">Default Head Tracking.</span></span> <span data-ttu-id="0ff18-191">Это означает, что система может выбрать оптимальный режим отслеживания головной системы на основе условий среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-191">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="0ff18-192">**Microsoft. Перцептионсимулатион. Хеадтраккермоде. Orientation**</span><span class="sxs-lookup"><span data-stu-id="0ff18-192">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="0ff18-193">Только отслеживание головной страницы.</span><span class="sxs-lookup"><span data-stu-id="0ff18-193">Orientation Only Head Tracking.</span></span> <span data-ttu-id="0ff18-194">Это означает, что отслеживающее расположение может быть ненадежным, а некоторые функциональные возможности, зависящие от головного расположения, могут быть недоступны.</span><span class="sxs-lookup"><span data-stu-id="0ff18-194">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="0ff18-195">**Microsoft. Перцептионсимулатион. Хеадтраккермоде. положением**</span><span class="sxs-lookup"><span data-stu-id="0ff18-195">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="0ff18-196">Отслеживание позиционированных головок.</span><span class="sxs-lookup"><span data-stu-id="0ff18-196">Positional Head Tracking.</span></span> <span data-ttu-id="0ff18-197">Это означает, что положение и ориентация отслеживающей головки надежны</span><span class="sxs-lookup"><span data-stu-id="0ff18-197">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="0ff18-198">Microsoft. Перцептионсимулатион. Симулатеджестуре</span><span class="sxs-lookup"><span data-stu-id="0ff18-198">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="0ff18-199">Описывает имитацию жеста</span><span class="sxs-lookup"><span data-stu-id="0ff18-199">Describes a simulated gesture</span></span>

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

<span data-ttu-id="0ff18-200">**Microsoft. Перцептионсимулатион. Симулатеджестуре. None**</span><span class="sxs-lookup"><span data-stu-id="0ff18-200">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="0ff18-201">Значение Sentinel, используемое для обозначения отсутствия жестов.</span><span class="sxs-lookup"><span data-stu-id="0ff18-201">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="0ff18-202">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Финжерпрессед**</span><span class="sxs-lookup"><span data-stu-id="0ff18-202">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="0ff18-203">Жест нажатия пальца.</span><span class="sxs-lookup"><span data-stu-id="0ff18-203">A finger pressed gesture.</span></span>

<span data-ttu-id="0ff18-204">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Финжеррелеасед**</span><span class="sxs-lookup"><span data-stu-id="0ff18-204">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="0ff18-205">Жест отпуска пальца.</span><span class="sxs-lookup"><span data-stu-id="0ff18-205">A finger released gesture.</span></span>

<span data-ttu-id="0ff18-206">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Home**</span><span class="sxs-lookup"><span data-stu-id="0ff18-206">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="0ff18-207">Жест домашнего или системного.</span><span class="sxs-lookup"><span data-stu-id="0ff18-207">The home/system gesture.</span></span>

<span data-ttu-id="0ff18-208">**Microsoft. Перцептионсимулатион. Симулатеджестуре. Max**</span><span class="sxs-lookup"><span data-stu-id="0ff18-208">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="0ff18-209">Максимально допустимый жест.</span><span class="sxs-lookup"><span data-stu-id="0ff18-209">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="0ff18-210">Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус</span><span class="sxs-lookup"><span data-stu-id="0ff18-210">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="0ff18-211">Возможные состояния имитации 6-ДОФ контроллера.</span><span class="sxs-lookup"><span data-stu-id="0ff18-211">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="0ff18-212">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Off**</span><span class="sxs-lookup"><span data-stu-id="0ff18-212">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="0ff18-213">6-ДОФ контроллер отключен.</span><span class="sxs-lookup"><span data-stu-id="0ff18-213">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="0ff18-214">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Active**</span><span class="sxs-lookup"><span data-stu-id="0ff18-214">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="0ff18-215">Контроллер ДОФ включается и отключается.</span><span class="sxs-lookup"><span data-stu-id="0ff18-215">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="0ff18-216">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Траккинглост**</span><span class="sxs-lookup"><span data-stu-id="0ff18-216">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="0ff18-217">6-ДОФ контроллер включен, но не может быть записан.</span><span class="sxs-lookup"><span data-stu-id="0ff18-217">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="0ff18-218">Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон</span><span class="sxs-lookup"><span data-stu-id="0ff18-218">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="0ff18-219">Поддерживаемые кнопки на имитации 6-ДОФ контроллера.</span><span class="sxs-lookup"><span data-stu-id="0ff18-219">The supported buttons on a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

<span data-ttu-id="0ff18-220">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. None**</span><span class="sxs-lookup"><span data-stu-id="0ff18-220">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="0ff18-221">Значение Sentinel, используемое для отсутствия кнопок.</span><span class="sxs-lookup"><span data-stu-id="0ff18-221">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="0ff18-222">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Home**</span><span class="sxs-lookup"><span data-stu-id="0ff18-222">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="0ff18-223">Нажата кнопка Главная.</span><span class="sxs-lookup"><span data-stu-id="0ff18-223">The Home button is pressed.</span></span>

<span data-ttu-id="0ff18-224">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Menu**</span><span class="sxs-lookup"><span data-stu-id="0ff18-224">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="0ff18-225">Нажата кнопка меню.</span><span class="sxs-lookup"><span data-stu-id="0ff18-225">The Menu button is pressed.</span></span>

<span data-ttu-id="0ff18-226">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. захват**</span><span class="sxs-lookup"><span data-stu-id="0ff18-226">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="0ff18-227">Нажата кнопка захвата.</span><span class="sxs-lookup"><span data-stu-id="0ff18-227">The Grip button is pressed.</span></span>

<span data-ttu-id="0ff18-228">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Таучпадпресс**</span><span class="sxs-lookup"><span data-stu-id="0ff18-228">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="0ff18-229">Сенсорная панель нажата.</span><span class="sxs-lookup"><span data-stu-id="0ff18-229">The TouchPad is pressed.</span></span>

<span data-ttu-id="0ff18-230">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Select**</span><span class="sxs-lookup"><span data-stu-id="0ff18-230">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="0ff18-231">Нажата кнопка выбрать.</span><span class="sxs-lookup"><span data-stu-id="0ff18-231">The Select button is pressed.</span></span>

<span data-ttu-id="0ff18-232">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Таучпадтауч**</span><span class="sxs-lookup"><span data-stu-id="0ff18-232">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="0ff18-233">Сенсорная панель затронута.</span><span class="sxs-lookup"><span data-stu-id="0ff18-233">The TouchPad is touched.</span></span>

<span data-ttu-id="0ff18-234">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. аналоговый стик**</span><span class="sxs-lookup"><span data-stu-id="0ff18-234">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="0ff18-235">Аналоговый стик нажат.</span><span class="sxs-lookup"><span data-stu-id="0ff18-235">The Thumbstick is pressed.</span></span>

<span data-ttu-id="0ff18-236">**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Max**</span><span class="sxs-lookup"><span data-stu-id="0ff18-236">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="0ff18-237">Максимальная допустимая кнопка.</span><span class="sxs-lookup"><span data-stu-id="0ff18-237">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="0ff18-238">Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате</span><span class="sxs-lookup"><span data-stu-id="0ff18-238">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="0ff18-239">Состояние калибровки имитации глаз</span><span class="sxs-lookup"><span data-stu-id="0ff18-239">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="0ff18-240">**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. недоступно**</span><span class="sxs-lookup"><span data-stu-id="0ff18-240">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="0ff18-241">Калибровка глаз недоступна.</span><span class="sxs-lookup"><span data-stu-id="0ff18-241">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="0ff18-242">**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. ready**</span><span class="sxs-lookup"><span data-stu-id="0ff18-242">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="0ff18-243">Эти глаза были откалиброваны.</span><span class="sxs-lookup"><span data-stu-id="0ff18-243">The eyes have been calibrated.</span></span>  <span data-ttu-id="0ff18-244">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0ff18-244">This is the default value.</span></span>

<span data-ttu-id="0ff18-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configиспользуем**</span><span class="sxs-lookup"><span data-stu-id="0ff18-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="0ff18-246">Эти глаза откалиброваны.</span><span class="sxs-lookup"><span data-stu-id="0ff18-246">The eyes are being calibrated.</span></span>

<span data-ttu-id="0ff18-247">**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. Усеркалибратионнидед**</span><span class="sxs-lookup"><span data-stu-id="0ff18-247">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="0ff18-248">Необходимо откалибровать глаза.</span><span class="sxs-lookup"><span data-stu-id="0ff18-248">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="0ff18-249">Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци</span><span class="sxs-lookup"><span data-stu-id="0ff18-249">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="0ff18-250">Точность отслеживания соединения руки.</span><span class="sxs-lookup"><span data-stu-id="0ff18-250">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="0ff18-251">**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. недоступно**</span><span class="sxs-lookup"><span data-stu-id="0ff18-251">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="0ff18-252">Соединение не было отслеживанием.</span><span class="sxs-lookup"><span data-stu-id="0ff18-252">The joint isn't tracked.</span></span>

<span data-ttu-id="0ff18-253">**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. приблизительный**</span><span class="sxs-lookup"><span data-stu-id="0ff18-253">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="0ff18-254">Совместное размещение выводится.</span><span class="sxs-lookup"><span data-stu-id="0ff18-254">The joint position is inferred.</span></span>

<span data-ttu-id="0ff18-255">**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. Visible**</span><span class="sxs-lookup"><span data-stu-id="0ff18-255">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="0ff18-256">Совместное соединение полностью отслеживание.</span><span class="sxs-lookup"><span data-stu-id="0ff18-256">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="0ff18-257">Microsoft. Перцептионсимулатион. Симулатедхандпосе</span><span class="sxs-lookup"><span data-stu-id="0ff18-257">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="0ff18-258">Точность отслеживания соединения руки.</span><span class="sxs-lookup"><span data-stu-id="0ff18-258">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

<span data-ttu-id="0ff18-259">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Closed**</span><span class="sxs-lookup"><span data-stu-id="0ff18-259">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="0ff18-260">Соединения пальца руки настраиваются для отражения закрытого объекта.</span><span class="sxs-lookup"><span data-stu-id="0ff18-260">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="0ff18-261">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Open**</span><span class="sxs-lookup"><span data-stu-id="0ff18-261">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="0ff18-262">Соединения пальца руки настраиваются для отражения открытой части.</span><span class="sxs-lookup"><span data-stu-id="0ff18-262">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="0ff18-263">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Point**</span><span class="sxs-lookup"><span data-stu-id="0ff18-263">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="0ff18-264">Соединения пальца руки настраиваются в соответствии с указывающим на себя.</span><span class="sxs-lookup"><span data-stu-id="0ff18-264">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="0ff18-265">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. сжатие**</span><span class="sxs-lookup"><span data-stu-id="0ff18-265">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="0ff18-266">Соединения пальца руки настраиваются в соответствии с набором сжатия.</span><span class="sxs-lookup"><span data-stu-id="0ff18-266">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="0ff18-267">**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Max**</span><span class="sxs-lookup"><span data-stu-id="0ff18-267">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="0ff18-268">Максимальное допустимое значение для Симулатедхандпосе.</span><span class="sxs-lookup"><span data-stu-id="0ff18-268">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="0ff18-269">Microsoft. Перцептионсимулатион. Плайбаккстате</span><span class="sxs-lookup"><span data-stu-id="0ff18-269">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="0ff18-270">Описывает состояние воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-270">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="0ff18-271">**Microsoft. Перцептионсимулатион. Плайбаккстате. Stopped**</span><span class="sxs-lookup"><span data-stu-id="0ff18-271">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="0ff18-272">Запись сейчас остановлена и готова к воспроизведению.</span><span class="sxs-lookup"><span data-stu-id="0ff18-272">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="0ff18-273">**Microsoft. Перцептионсимулатион. Плайбаккстате. Play**</span><span class="sxs-lookup"><span data-stu-id="0ff18-273">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="0ff18-274">Сейчас запись воспроизводится.</span><span class="sxs-lookup"><span data-stu-id="0ff18-274">The recording is currently playing.</span></span>

<span data-ttu-id="0ff18-275">**Microsoft. Перцептионсимулатион. Плайбаккстате. приостановлено**</span><span class="sxs-lookup"><span data-stu-id="0ff18-275">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="0ff18-276">Запись в данный момент приостановлена.</span><span class="sxs-lookup"><span data-stu-id="0ff18-276">The recording is currently paused.</span></span>

<span data-ttu-id="0ff18-277">**Microsoft. Перцептионсимулатион. Плайбаккстате. end**</span><span class="sxs-lookup"><span data-stu-id="0ff18-277">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="0ff18-278">Запись достигла конца.</span><span class="sxs-lookup"><span data-stu-id="0ff18-278">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="0ff18-279">Microsoft. Перцептионсимулатион. Vector3</span><span class="sxs-lookup"><span data-stu-id="0ff18-279">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="0ff18-280">Описывает вектор с тремя компонентами, который может описывать точку или вектор в трехмерном пространстве.</span><span class="sxs-lookup"><span data-stu-id="0ff18-280">Describes a three components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="0ff18-281">**Microsoft. Перцептионсимулатион. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="0ff18-281">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="0ff18-282">Координата X вектора.</span><span class="sxs-lookup"><span data-stu-id="0ff18-282">The X component of the vector.</span></span>

<span data-ttu-id="0ff18-283">**Microsoft. Перцептионсимулатион. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="0ff18-283">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="0ff18-284">Координата Y вектора.</span><span class="sxs-lookup"><span data-stu-id="0ff18-284">The Y component of the vector.</span></span>

<span data-ttu-id="0ff18-285">**Microsoft. Перцептионсимулатион. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="0ff18-285">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="0ff18-286">Координата Z вектора.</span><span class="sxs-lookup"><span data-stu-id="0ff18-286">The Z component of the vector.</span></span>

<span data-ttu-id="0ff18-287">**Microsoft. Перцептионсимулатион. Vector3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-287">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="0ff18-288">Создайте новый Vector3.</span><span class="sxs-lookup"><span data-stu-id="0ff18-288">Construct a new Vector3.</span></span>

<span data-ttu-id="0ff18-289">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-289">Parameters</span></span>
* <span data-ttu-id="0ff18-290">x — компонент x вектора.</span><span class="sxs-lookup"><span data-stu-id="0ff18-290">x - The x component of the vector.</span></span>
* <span data-ttu-id="0ff18-291">y — компонент y вектора.</span><span class="sxs-lookup"><span data-stu-id="0ff18-291">y - The y component of the vector.</span></span>
* <span data-ttu-id="0ff18-292">z — компонент z вектора.</span><span class="sxs-lookup"><span data-stu-id="0ff18-292">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="0ff18-293">Microsoft. Перцептионсимулатион. Rotation3</span><span class="sxs-lookup"><span data-stu-id="0ff18-293">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="0ff18-294">Описывает поворот трех компонентов.</span><span class="sxs-lookup"><span data-stu-id="0ff18-294">Describes a three components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="0ff18-295">**Microsoft. Перцептионсимулатион. Rotation3. шаг**</span><span class="sxs-lookup"><span data-stu-id="0ff18-295">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="0ff18-296">Компонент шаг поворота вокруг оси X.</span><span class="sxs-lookup"><span data-stu-id="0ff18-296">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="0ff18-297">**Microsoft. Перцептионсимулатион. Rotation3. значения нутации**</span><span class="sxs-lookup"><span data-stu-id="0ff18-297">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="0ff18-298">Компонент значения нутации вращения, который находится справа вокруг оси Y.</span><span class="sxs-lookup"><span data-stu-id="0ff18-298">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="0ff18-299">**Microsoft. Перцептионсимулатион. Rotation3. рулон**</span><span class="sxs-lookup"><span data-stu-id="0ff18-299">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="0ff18-300">Компонент рулона поворота, который находится справа вокруг оси Z.</span><span class="sxs-lookup"><span data-stu-id="0ff18-300">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="0ff18-301">**Microsoft. Перцептионсимулатион. Rotation3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-301">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="0ff18-302">Создайте новый Rotation3.</span><span class="sxs-lookup"><span data-stu-id="0ff18-302">Construct a new Rotation3.</span></span>

<span data-ttu-id="0ff18-303">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-303">Parameters</span></span>
* <span data-ttu-id="0ff18-304">шаг — компонент шага поворота.</span><span class="sxs-lookup"><span data-stu-id="0ff18-304">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="0ff18-305">значения нутации — компонент значения нутации вращения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-305">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="0ff18-306">рулон — компонент рулона поворота.</span><span class="sxs-lookup"><span data-stu-id="0ff18-306">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="0ff18-307">Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион</span><span class="sxs-lookup"><span data-stu-id="0ff18-307">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="0ff18-308">Описывает конфигурацию соединения с имитацией руки.</span><span class="sxs-lookup"><span data-stu-id="0ff18-308">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="0ff18-309">**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. положением**</span><span class="sxs-lookup"><span data-stu-id="0ff18-309">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="0ff18-310">Расположение соединения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-310">The position of the joint.</span></span>

<span data-ttu-id="0ff18-311">**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. вращение**</span><span class="sxs-lookup"><span data-stu-id="0ff18-311">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="0ff18-312">Поворот соединения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-312">The rotation of the joint.</span></span>

<span data-ttu-id="0ff18-313">**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. Траккингаккураци**</span><span class="sxs-lookup"><span data-stu-id="0ff18-313">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="0ff18-314">Точность отслеживания соединения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-314">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="0ff18-315">Microsoft. Перцептионсимулатион. Фрустум</span><span class="sxs-lookup"><span data-stu-id="0ff18-315">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="0ff18-316">Описывает представление фрустум, как обычно используется камерой.</span><span class="sxs-lookup"><span data-stu-id="0ff18-316">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="0ff18-317">**Microsoft. Перцептионсимулатион. Фрустум. Near**</span><span class="sxs-lookup"><span data-stu-id="0ff18-317">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="0ff18-318">Минимальное расстояние, которое содержится в фрустум.</span><span class="sxs-lookup"><span data-stu-id="0ff18-318">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="0ff18-319">**Microsoft. Перцептионсимулатион. Фрустум. FAR**</span><span class="sxs-lookup"><span data-stu-id="0ff18-319">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="0ff18-320">Максимальное расстояние, которое содержится в фрустум.</span><span class="sxs-lookup"><span data-stu-id="0ff18-320">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="0ff18-321">**Microsoft. Перцептионсимулатион. Фрустум. Фиелдофвиев**</span><span class="sxs-lookup"><span data-stu-id="0ff18-321">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="0ff18-322">Горизонтальное поле представления фрустум в радианах (меньше PI).</span><span class="sxs-lookup"><span data-stu-id="0ff18-322">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="0ff18-323">**Microsoft. Перцептионсимулатион. Фрустум. Аспектратио**</span><span class="sxs-lookup"><span data-stu-id="0ff18-323">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="0ff18-324">Отношение горизонтального поля представления к вертикальному полю представления.</span><span class="sxs-lookup"><span data-stu-id="0ff18-324">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="0ff18-325">Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион</span><span class="sxs-lookup"><span data-stu-id="0ff18-325">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="0ff18-326">Описывает конфигурацию экрана имитации гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="0ff18-326">Describes the configuration of the simulated headset's display.</span></span>

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

<span data-ttu-id="0ff18-327">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Лефтэйепоситион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-327">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="0ff18-328">Преобразование из центра заголовка к левому глазу в целях отрисовки стерео.</span><span class="sxs-lookup"><span data-stu-id="0ff18-328">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="0ff18-329">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Лефтэйеротатион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-329">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="0ff18-330">Поворот левого глаза в целях отрисовки стерео.</span><span class="sxs-lookup"><span data-stu-id="0ff18-330">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="0ff18-331">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Ригхтэйепоситион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-331">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="0ff18-332">Преобразование из центра заголовка к нужному глазу в целях отрисовки стерео.</span><span class="sxs-lookup"><span data-stu-id="0ff18-332">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="0ff18-333">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Ригхтэйеротатион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-333">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="0ff18-334">Поворот правильного глаза в целях отрисовки стерео.</span><span class="sxs-lookup"><span data-stu-id="0ff18-334">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="0ff18-335">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. IPD**</span><span class="sxs-lookup"><span data-stu-id="0ff18-335">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="0ff18-336">Значение IPD, сообщаемое системой в целях отрисовки стерео.</span><span class="sxs-lookup"><span data-stu-id="0ff18-336">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="0ff18-337">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Апплеетрансформс**</span><span class="sxs-lookup"><span data-stu-id="0ff18-337">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="0ff18-338">Должны ли значения, предоставленные для преобразования влево и вправо, считаться допустимыми и примененными к работающей системе.</span><span class="sxs-lookup"><span data-stu-id="0ff18-338">Whether the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="0ff18-339">**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Апплипд**</span><span class="sxs-lookup"><span data-stu-id="0ff18-339">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="0ff18-340">Должно ли значение, указанное для IPD, считаться допустимым и примененным к работающей системе.</span><span class="sxs-lookup"><span data-stu-id="0ff18-340">Whether the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="0ff18-341">Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер</span><span class="sxs-lookup"><span data-stu-id="0ff18-341">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="0ff18-342">Корень для создания пакетов, используемых для управления устройством.</span><span class="sxs-lookup"><span data-stu-id="0ff18-342">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="0ff18-343">**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. Device**</span><span class="sxs-lookup"><span data-stu-id="0ff18-343">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="0ff18-344">Извлеките объект имитации устройства, который интерпретирует имитацию человека и имитации мира.</span><span class="sxs-lookup"><span data-stu-id="0ff18-344">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="0ff18-345">**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. человеческий**</span><span class="sxs-lookup"><span data-stu-id="0ff18-345">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="0ff18-346">Извлеките объект, управляющий имитацией человека.</span><span class="sxs-lookup"><span data-stu-id="0ff18-346">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="0ff18-347">**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. Reset**</span><span class="sxs-lookup"><span data-stu-id="0ff18-347">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="0ff18-348">Сбрасывает состояние имитации до состояния по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0ff18-348">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="0ff18-349">Microsoft. Перцептионсимулатион. Исимулатеддевице</span><span class="sxs-lookup"><span data-stu-id="0ff18-349">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="0ff18-350">Интерфейс, описывающий устройство, которое интерпретирует имитацию мира и имитацию человека</span><span class="sxs-lookup"><span data-stu-id="0ff18-350">Interface describing the device, which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="0ff18-351">**Microsoft. Перцептионсимулатион. Исимулатеддевице. Хеадтраккер**</span><span class="sxs-lookup"><span data-stu-id="0ff18-351">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="0ff18-352">Извлеките головной датчик из имитации устройства.</span><span class="sxs-lookup"><span data-stu-id="0ff18-352">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="0ff18-353">**Microsoft. Перцептионсимулатион. Исимулатеддевице. Хандтраккер**</span><span class="sxs-lookup"><span data-stu-id="0ff18-353">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="0ff18-354">Получите датчик руки от имитации устройства.</span><span class="sxs-lookup"><span data-stu-id="0ff18-354">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="0ff18-355">**Microsoft. Перцептионсимулатион. Исимулатеддевице. Сетсимулатеддевицетипе (Microsoft. Перцептионсимулатион. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-355">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="0ff18-356">Задайте свойства виртуального устройства в соответствии с указанным типом устройства.</span><span class="sxs-lookup"><span data-stu-id="0ff18-356">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="0ff18-357">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-357">Parameters</span></span>
* <span data-ttu-id="0ff18-358">тип — новый тип имитации устройства.</span><span class="sxs-lookup"><span data-stu-id="0ff18-358">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="0ff18-359">Microsoft. Перцептионсимулатион. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="0ff18-359">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="0ff18-360">Дополнительные свойства доступны путем приведения Исимулатеддевице к ISimulatedDevice2.</span><span class="sxs-lookup"><span data-stu-id="0ff18-360">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="0ff18-361">**Microsoft. Перцептионсимулатион. ISimulatedDevice2. Исусерпресент**</span><span class="sxs-lookup"><span data-stu-id="0ff18-361">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="0ff18-362">Получение или задание того, активно ли имитация людьмиа на гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="0ff18-362">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="0ff18-363">**Microsoft. Перцептионсимулатион. ISimulatedDevice2. Дисплайконфигуратион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-363">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="0ff18-364">Получение или установка свойств имитации дисплея.</span><span class="sxs-lookup"><span data-stu-id="0ff18-364">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="0ff18-365">Microsoft. Перцептионсимулатион. Исимулатедхеадтраккер</span><span class="sxs-lookup"><span data-stu-id="0ff18-365">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="0ff18-366">Интерфейс, описывающий часть имитации устройства, которая отслеживает заголовку имитации человека.</span><span class="sxs-lookup"><span data-stu-id="0ff18-366">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="0ff18-367">**Microsoft. Перцептионсимулатион. Исимулатедхеадтраккер. Хеадтраккермоде**</span><span class="sxs-lookup"><span data-stu-id="0ff18-367">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="0ff18-368">Извлекает и устанавливает текущий режим трассировки головного подразделения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-368">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="0ff18-369">Microsoft. Перцептионсимулатион. Исимулатедхандтраккер</span><span class="sxs-lookup"><span data-stu-id="0ff18-369">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="0ff18-370">Интерфейс, описывающий часть имитации устройства, которая отслеживает руки имитации человека</span><span class="sxs-lookup"><span data-stu-id="0ff18-370">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

<span data-ttu-id="0ff18-371">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-371">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="0ff18-372">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-372">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="0ff18-373">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. положением**</span><span class="sxs-lookup"><span data-stu-id="0ff18-373">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="0ff18-374">Извлечение и задание положения объекта Tracker для имитации относительно центра головки.</span><span class="sxs-lookup"><span data-stu-id="0ff18-374">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="0ff18-375">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. шаг**</span><span class="sxs-lookup"><span data-stu-id="0ff18-375">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="0ff18-376">Извлеките и задайте шаг вниз для смоделированного средства записи.</span><span class="sxs-lookup"><span data-stu-id="0ff18-376">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="0ff18-377">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Фрустумигноред**</span><span class="sxs-lookup"><span data-stu-id="0ff18-377">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="0ff18-378">Получите и задайте значение, определяющее, пропускается ли фрустум транспортера для имитации.</span><span class="sxs-lookup"><span data-stu-id="0ff18-378">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="0ff18-379">Если игнорируется, обе руки всегда видимы.</span><span class="sxs-lookup"><span data-stu-id="0ff18-379">When ignored, both hands are always visible.</span></span> <span data-ttu-id="0ff18-380">Если параметр не пропускается (по умолчанию), руки отображаются только в том случае, если они находятся в фрустуме средства записи.</span><span class="sxs-lookup"><span data-stu-id="0ff18-380">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="0ff18-381">**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Фрустум**</span><span class="sxs-lookup"><span data-stu-id="0ff18-381">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="0ff18-382">Получите и задайте свойства фрустум, используемые для определения, видны ли руки для имитации средства записи.</span><span class="sxs-lookup"><span data-stu-id="0ff18-382">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="0ff18-383">Microsoft. Перцептионсимулатион. Исимулатедхуман</span><span class="sxs-lookup"><span data-stu-id="0ff18-383">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="0ff18-384">Интерфейс верхнего уровня для управления имитацией человека.</span><span class="sxs-lookup"><span data-stu-id="0ff18-384">Top-level interface for controlling the simulated human.</span></span>

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }s
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

<span data-ttu-id="0ff18-385">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-385">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="0ff18-386">Извлечение и Установка расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-386">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="0ff18-387">Это расположение соответствует точке в центре метров человека.</span><span class="sxs-lookup"><span data-stu-id="0ff18-387">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="0ff18-388">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Direction**</span><span class="sxs-lookup"><span data-stu-id="0ff18-388">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="0ff18-389">Извлеките и задайте направление имитации человеческих лиц в мире.</span><span class="sxs-lookup"><span data-stu-id="0ff18-389">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="0ff18-390">0 радианы отменяют отрицательную ось Z.</span><span class="sxs-lookup"><span data-stu-id="0ff18-390">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="0ff18-391">Положительные радианы поворачиваются по часовой стрелке относительно оси Y.</span><span class="sxs-lookup"><span data-stu-id="0ff18-391">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="0ff18-392">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Height**</span><span class="sxs-lookup"><span data-stu-id="0ff18-392">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="0ff18-393">Получение и задание высоты имитации человека в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-393">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="0ff18-394">**Microsoft. Перцептионсимулатион. Исимулатедхуман. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="0ff18-394">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="0ff18-395">Получите левую руку имитации человека.</span><span class="sxs-lookup"><span data-stu-id="0ff18-395">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="0ff18-396">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Ригхсанд**</span><span class="sxs-lookup"><span data-stu-id="0ff18-396">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="0ff18-397">Получите правую руку имитации человека.</span><span class="sxs-lookup"><span data-stu-id="0ff18-397">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="0ff18-398">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Head**</span><span class="sxs-lookup"><span data-stu-id="0ff18-398">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="0ff18-399">Получите заголовок имитации человека.</span><span class="sxs-lookup"><span data-stu-id="0ff18-399">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="0ff18-400">**Microsoft. Перцептионсимулатион. Исимулатедхуман. Move (Microsoft. Перцептионсимулатион. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-400">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="0ff18-401">Перемещение имитации человека относительно его текущего положения в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-401">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="0ff18-402">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-402">Parameters</span></span>
* <span data-ttu-id="0ff18-403">перевод — перевод, который необходимо переместить, относительно текущего положения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-403">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="0ff18-404">**Microsoft. Перцептионсимулатион. Исимулатедхуман. вращение (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-404">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="0ff18-405">Поворот имитации человека относительно текущего направления по часовой стрелке по оси Y</span><span class="sxs-lookup"><span data-stu-id="0ff18-405">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="0ff18-406">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-406">Parameters</span></span>
* <span data-ttu-id="0ff18-407">радианы — величина поворота вокруг оси Y.</span><span class="sxs-lookup"><span data-stu-id="0ff18-407">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="0ff18-408">Microsoft. Перцептионсимулатион. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="0ff18-408">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="0ff18-409">Дополнительные свойства доступны путем приведения Исимулатедхуман к ISimulatedHuman2.</span><span class="sxs-lookup"><span data-stu-id="0ff18-409">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="0ff18-410">**Microsoft. Перцептионсимулатион. ISimulatedHuman2. Лефтконтроллер**</span><span class="sxs-lookup"><span data-stu-id="0ff18-410">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="0ff18-411">Получите левый 6-ДОФ контроллер.</span><span class="sxs-lookup"><span data-stu-id="0ff18-411">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="0ff18-412">**Microsoft. Перцептионсимулатион. ISimulatedHuman2. Ригхтконтроллер**</span><span class="sxs-lookup"><span data-stu-id="0ff18-412">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="0ff18-413">Получите подходящий 6-ДОФ контроллер.</span><span class="sxs-lookup"><span data-stu-id="0ff18-413">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="0ff18-414">Microsoft. Перцептионсимулатион. Исимулатедханд</span><span class="sxs-lookup"><span data-stu-id="0ff18-414">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="0ff18-415">Интерфейс, описывающий руки имитации человека</span><span class="sxs-lookup"><span data-stu-id="0ff18-415">Interface describing a hand of the simulated human</span></span>

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

<span data-ttu-id="0ff18-416">**Microsoft. Перцептионсимулатион. Исимулатедханд. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-416">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="0ff18-417">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-417">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="0ff18-418">**Microsoft. Перцептионсимулатион. Исимулатедханд. положением**</span><span class="sxs-lookup"><span data-stu-id="0ff18-418">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="0ff18-419">Получение и установка положения смоделированной руки относительно человека в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-419">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="0ff18-420">**Microsoft. Перцептионсимулатион. Исимулатедханд. Activated**</span><span class="sxs-lookup"><span data-stu-id="0ff18-420">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="0ff18-421">Извлечение и задание того, активирована ли рука в настоящий момент.</span><span class="sxs-lookup"><span data-stu-id="0ff18-421">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="0ff18-422">**Microsoft. Перцептионсимулатион. Исимулатедханд. Visible**</span><span class="sxs-lookup"><span data-stu-id="0ff18-422">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="0ff18-423">Извлеките, является ли рука в настоящий момент видимой для SimulatedDevice (т. е. находится ли оно в положении, которое должно быть обнаружено Хандтраккер).</span><span class="sxs-lookup"><span data-stu-id="0ff18-423">Retrieve whether the hand is currently visible to the SimulatedDevice (that is, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="0ff18-424">**Microsoft. Перцептионсимулатион. Исимулатедханд. Енсуревисибле**</span><span class="sxs-lookup"><span data-stu-id="0ff18-424">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="0ff18-425">Переместите руку так, чтобы она была видна SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="0ff18-425">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="0ff18-426">**Microsoft. Перцептионсимулатион. Исимулатедханд. Move (Microsoft. Перцептионсимулатион. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-426">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="0ff18-427">Переместить положение моделируемой руки относительно ее текущей должности в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-427">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="0ff18-428">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-428">Parameters</span></span>
* <span data-ttu-id="0ff18-429">перевод — величина, на которую переводятся смоделированные руки.</span><span class="sxs-lookup"><span data-stu-id="0ff18-429">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="0ff18-430">**Microsoft. Перцептионсимулатион. Исимулатедханд. Перформжестуре (Microsoft. Перцептионсимулатион. Симулатеджестуре)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-430">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="0ff18-431">Выполните жест, используя имитацию руки.</span><span class="sxs-lookup"><span data-stu-id="0ff18-431">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="0ff18-432">Она будет обнаружена системой только в том случае, если она включена.</span><span class="sxs-lookup"><span data-stu-id="0ff18-432">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="0ff18-433">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-433">Parameters</span></span>
* <span data-ttu-id="0ff18-434">жест — жест, который необходимо выполнить.</span><span class="sxs-lookup"><span data-stu-id="0ff18-434">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="0ff18-435">Microsoft. Перцептионсимулатион. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="0ff18-435">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="0ff18-436">Дополнительные свойства доступны путем приведения Исимулатедханд к ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="0ff18-436">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="0ff18-437">**Microsoft. Перцептионсимулатион. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="0ff18-437">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="0ff18-438">Возвращает или задает поворот моделируемой руки.</span><span class="sxs-lookup"><span data-stu-id="0ff18-438">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="0ff18-439">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="0ff18-439">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="0ff18-440">Microsoft. Перцептионсимулатион. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="0ff18-440">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="0ff18-441">Дополнительные свойства доступны путем приведения Исимулатедханд к ISimulatedHand3.</span><span class="sxs-lookup"><span data-stu-id="0ff18-441">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="0ff18-442">**Microsoft. Перцептионсимулатион. ISimulatedHand3. Жетжоинтконфигуратион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-442">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="0ff18-443">Получение конфигурации соединения для указанного соединения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-443">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="0ff18-444">**Microsoft. Перцептионсимулатион. ISimulatedHand3. Сетжоинтконфигуратион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-444">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="0ff18-445">Задает конфигурацию соединения для указанного соединения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-445">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="0ff18-446">**Microsoft. Перцептионсимулатион. ISimulatedHand3. Сесандпосе**</span><span class="sxs-lookup"><span data-stu-id="0ff18-446">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="0ff18-447">Задайте для параметра "рука" известное значение с необязательным флагом для анимации.</span><span class="sxs-lookup"><span data-stu-id="0ff18-447">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="0ff18-448">Примечание. анимация не приведет к тому, что присоединения будут немедленно отражены в своих окончательно Объединенных конфигурациях.</span><span class="sxs-lookup"><span data-stu-id="0ff18-448">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="0ff18-449">Microsoft. Перцептионсимулатион. Исимулатедхеад</span><span class="sxs-lookup"><span data-stu-id="0ff18-449">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="0ff18-450">Интерфейс, описывающий заголовок имитации человека.</span><span class="sxs-lookup"><span data-stu-id="0ff18-450">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="0ff18-451">**Microsoft. Перцептионсимулатион. Исимулатедхеад. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-451">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="0ff18-452">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-452">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="0ff18-453">**Microsoft. Перцептионсимулатион. Исимулатедхеад. вращение**</span><span class="sxs-lookup"><span data-stu-id="0ff18-453">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="0ff18-454">Извлеките поворот моделируемой головки.</span><span class="sxs-lookup"><span data-stu-id="0ff18-454">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="0ff18-455">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="0ff18-455">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="0ff18-456">**Microsoft. Перцептионсимулатион. Исимулатедхеад. диаметр**</span><span class="sxs-lookup"><span data-stu-id="0ff18-456">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="0ff18-457">Получение диаметра смоделированного головного элемента.</span><span class="sxs-lookup"><span data-stu-id="0ff18-457">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="0ff18-458">Это значение используется для определения центра заголовка (точки вращения).</span><span class="sxs-lookup"><span data-stu-id="0ff18-458">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="0ff18-459">**Microsoft. Перцептионсимулатион. Исимулатедхеад. вращение (Microsoft. Перцептионсимулатион. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-459">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="0ff18-460">Поворот смоделированной головки относительно текущего поворота.</span><span class="sxs-lookup"><span data-stu-id="0ff18-460">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="0ff18-461">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="0ff18-461">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="0ff18-462">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-462">Parameters</span></span>
* <span data-ttu-id="0ff18-463">вращение — величина поворота.</span><span class="sxs-lookup"><span data-stu-id="0ff18-463">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="0ff18-464">Microsoft. Перцептионсимулатион. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="0ff18-464">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="0ff18-465">Дополнительные свойства доступны путем приведения Исимулатедхеад к ISimulatedHead2.</span><span class="sxs-lookup"><span data-stu-id="0ff18-465">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="0ff18-466">**Microsoft. Перцептионсимулатион. ISimulatedHead2. глаза**</span><span class="sxs-lookup"><span data-stu-id="0ff18-466">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="0ff18-467">Извлеките глаза имитации человека.</span><span class="sxs-lookup"><span data-stu-id="0ff18-467">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="0ff18-468">Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер</span><span class="sxs-lookup"><span data-stu-id="0ff18-468">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="0ff18-469">Интерфейс, описывающий ДОФ контроллер, связанный с имитируемым человеком.</span><span class="sxs-lookup"><span data-stu-id="0ff18-469">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

<span data-ttu-id="0ff18-470">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="0ff18-471">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-471">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="0ff18-472">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. status**</span><span class="sxs-lookup"><span data-stu-id="0ff18-472">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="0ff18-473">Возвращает или задает текущее состояние контроллера.</span><span class="sxs-lookup"><span data-stu-id="0ff18-473">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="0ff18-474">Для состояния контроллера должно быть задано значение, отличное от OFF, прежде чем все вызовы для перемещения, вращения или нажатия кнопки будут выполнены.</span><span class="sxs-lookup"><span data-stu-id="0ff18-474">The controller status must be set to a value other than Off before any calls to move, rotate, or press buttons will succeed.</span></span>

<span data-ttu-id="0ff18-475">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. положением**</span><span class="sxs-lookup"><span data-stu-id="0ff18-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="0ff18-476">Получение или установка положения имитации контроллера относительно человека в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-476">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="0ff18-477">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Orientation**</span><span class="sxs-lookup"><span data-stu-id="0ff18-477">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="0ff18-478">Получение или установка ориентации имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="0ff18-478">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="0ff18-479">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Move (Microsoft. Перцептионсимулатион. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-479">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="0ff18-480">Переместить положение имитации контроллера относительно его текущего положения в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-480">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="0ff18-481">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-481">Parameters</span></span>
* <span data-ttu-id="0ff18-482">перевод — это величина, на которую нужно перевести имитируемый контроллер.</span><span class="sxs-lookup"><span data-stu-id="0ff18-482">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="0ff18-483">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Прессбуттон (Симулатедсиксдофконтроллербуттон)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-483">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="0ff18-484">Нажмите кнопку на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="0ff18-484">Press a button on the simulated controller.</span></span>  <span data-ttu-id="0ff18-485">Она будет обнаружена системой только в том случае, если контроллер включен.</span><span class="sxs-lookup"><span data-stu-id="0ff18-485">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="0ff18-486">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-486">Parameters</span></span>
* <span data-ttu-id="0ff18-487">Кнопка для нажатия кнопки.</span><span class="sxs-lookup"><span data-stu-id="0ff18-487">button - The button to press.</span></span>

<span data-ttu-id="0ff18-488">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Релеасебуттон (Симулатедсиксдофконтроллербуттон)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-488">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="0ff18-489">Выпустите кнопку на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="0ff18-489">Release a button on the simulated controller.</span></span>  <span data-ttu-id="0ff18-490">Она будет обнаружена системой только в том случае, если контроллер включен.</span><span class="sxs-lookup"><span data-stu-id="0ff18-490">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="0ff18-491">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-491">Parameters</span></span>
* <span data-ttu-id="0ff18-492">Кнопка для выпуска.</span><span class="sxs-lookup"><span data-stu-id="0ff18-492">button - The button to release.</span></span>

<span data-ttu-id="0ff18-493">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Жеттаучпадпоситион (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-493">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="0ff18-494">Получить расположение имитации пальца на сенсорной панели имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="0ff18-494">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="0ff18-495">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-495">Parameters</span></span>
* <span data-ttu-id="0ff18-496">x — горизонтальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="0ff18-496">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="0ff18-497">y — вертикальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="0ff18-497">y - The vertical position of the finger.</span></span>

<span data-ttu-id="0ff18-498">**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Сеттаучпадпоситион (float, float)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-498">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="0ff18-499">Установите расположение имитации пальца на сенсорной панели имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="0ff18-499">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="0ff18-500">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-500">Parameters</span></span>
* <span data-ttu-id="0ff18-501">x — горизонтальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="0ff18-501">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="0ff18-502">y — вертикальное расположение пальца.</span><span class="sxs-lookup"><span data-stu-id="0ff18-502">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="0ff18-503">Microsoft. Перцептионсимулатион. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="0ff18-503">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="0ff18-504">Дополнительные свойства и методы доступны путем приведения Исимулатедсиксдофконтроллер к ISimulatedSixDofController2.</span><span class="sxs-lookup"><span data-stu-id="0ff18-504">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="0ff18-505">**Microsoft. Перцептионсимулатион. ISimulatedSixDofController2. Жетсумбстиккпоситион (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-505">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="0ff18-506">Получение расположения имитации аналогового стика на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="0ff18-506">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="0ff18-507">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-507">Parameters</span></span>
* <span data-ttu-id="0ff18-508">x — горизонтальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="0ff18-508">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="0ff18-509">y — вертикальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="0ff18-509">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="0ff18-510">**Microsoft. Перцептионсимулатион. ISimulatedSixDofController2. Сетсумбстиккпоситион (float, float)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-510">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="0ff18-511">Задайте расположение имитации аналогового стика на имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="0ff18-511">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="0ff18-512">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-512">Parameters</span></span>
* <span data-ttu-id="0ff18-513">x — горизонтальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="0ff18-513">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="0ff18-514">y — вертикальное расположение стика.</span><span class="sxs-lookup"><span data-stu-id="0ff18-514">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="0ff18-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatТерилевел**</span><span class="sxs-lookup"><span data-stu-id="0ff18-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="0ff18-516">Получение или установка уровня заряда батареи для имитации контроллера.</span><span class="sxs-lookup"><span data-stu-id="0ff18-516">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="0ff18-517">Значение должно быть больше 0,0 и меньше или равно 100,0.</span><span class="sxs-lookup"><span data-stu-id="0ff18-517">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="0ff18-518">Microsoft. Перцептионсимулатион. Исимулатедэйес</span><span class="sxs-lookup"><span data-stu-id="0ff18-518">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="0ff18-519">Интерфейс, описывающий глаза имитации человека.</span><span class="sxs-lookup"><span data-stu-id="0ff18-519">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="0ff18-520">**Microsoft. Перцептионсимулатион. Исимулатедэйес. вращение**</span><span class="sxs-lookup"><span data-stu-id="0ff18-520">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="0ff18-521">Извлеките поворот имитации глаз.</span><span class="sxs-lookup"><span data-stu-id="0ff18-521">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="0ff18-522">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="0ff18-522">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="0ff18-523">**Microsoft. Перцептионсимулатион. Исимулатедэйес. вращение (Microsoft. Перцептионсимулатион. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-523">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="0ff18-524">Поворот имитации глаз относительно текущего вращения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-524">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="0ff18-525">Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="0ff18-525">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="0ff18-526">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-526">Parameters</span></span>
* <span data-ttu-id="0ff18-527">вращение — величина поворота.</span><span class="sxs-lookup"><span data-stu-id="0ff18-527">rotation - The amount to rotate.</span></span>

<span data-ttu-id="0ff18-528">**Microsoft. Перцептионсимулатион. Исимулатедэйес. Калибратионстате**</span><span class="sxs-lookup"><span data-stu-id="0ff18-528">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="0ff18-529">Возвращает или задает состояние калибровки для имитации глаз.</span><span class="sxs-lookup"><span data-stu-id="0ff18-529">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="0ff18-530">**Microsoft. Перцептионсимулатион. Исимулатедэйес. Ворлдпоситион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-530">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="0ff18-531">Получение расположения узла относительно мира в метрах.</span><span class="sxs-lookup"><span data-stu-id="0ff18-531">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="0ff18-532">Microsoft. Перцептионсимулатион. Исимулатионрекординг</span><span class="sxs-lookup"><span data-stu-id="0ff18-532">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="0ff18-533">Интерфейс для взаимодействия с одной записью, загруженной для воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-533">Interface for interacting with a single recording loaded for playback.</span></span>

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

<span data-ttu-id="0ff18-534">**Типы Microsoft. Перцептионсимулатион. Исимулатионрекординг.**</span><span class="sxs-lookup"><span data-stu-id="0ff18-534">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="0ff18-535">Возвращает список типов данных в записи.</span><span class="sxs-lookup"><span data-stu-id="0ff18-535">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="0ff18-536">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. State**</span><span class="sxs-lookup"><span data-stu-id="0ff18-536">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="0ff18-537">Извлекает текущее состояние записи.</span><span class="sxs-lookup"><span data-stu-id="0ff18-537">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="0ff18-538">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Play**</span><span class="sxs-lookup"><span data-stu-id="0ff18-538">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="0ff18-539">Запустите воспроизведение.</span><span class="sxs-lookup"><span data-stu-id="0ff18-539">Start the playback.</span></span> <span data-ttu-id="0ff18-540">Если запись приостановлена, воспроизведение будет возобновлено из приостановленного расположения. При остановке воспроизведение начнется с самого начала.</span><span class="sxs-lookup"><span data-stu-id="0ff18-540">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="0ff18-541">Если воспроизведение уже проигрывается, этот вызов игнорируется.</span><span class="sxs-lookup"><span data-stu-id="0ff18-541">If already playing, this call is ignored.</span></span>

<span data-ttu-id="0ff18-542">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Pause**</span><span class="sxs-lookup"><span data-stu-id="0ff18-542">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="0ff18-543">Приостанавливает воспроизведение в текущем расположении.</span><span class="sxs-lookup"><span data-stu-id="0ff18-543">Pauses the playback at its current location.</span></span> <span data-ttu-id="0ff18-544">Если запись остановлена, вызов игнорируется.</span><span class="sxs-lookup"><span data-stu-id="0ff18-544">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="0ff18-545">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-545">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="0ff18-546">Выполняет поиск записи в указанное время (в 100-наносекундах секунд с начала) и приостанавливается в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="0ff18-546">Seeks the recording to the specified time (in 100-nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="0ff18-547">Если время превышает окончание записи, оно приостанавливается на последнем кадре.</span><span class="sxs-lookup"><span data-stu-id="0ff18-547">If the time is beyond the end of the recording, it's paused at the last frame.</span></span>

<span data-ttu-id="0ff18-548">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-548">Parameters</span></span>
* <span data-ttu-id="0ff18-549">такты — время поиска.</span><span class="sxs-lookup"><span data-stu-id="0ff18-549">ticks - The time to which to seek.</span></span>

<span data-ttu-id="0ff18-550">**Microsoft. Перцептионсимулатион. Исимулатионрекординг. останавливаться**</span><span class="sxs-lookup"><span data-stu-id="0ff18-550">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="0ff18-551">Останавливает воспроизведение и сбрасывает текущую точку в начало.</span><span class="sxs-lookup"><span data-stu-id="0ff18-551">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="0ff18-552">Microsoft. Перцептионсимулатион. Исимулатионрекордингкаллбакк</span><span class="sxs-lookup"><span data-stu-id="0ff18-552">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="0ff18-553">Интерфейс для получения изменений состояния во время воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-553">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="0ff18-554">**Microsoft. Перцептионсимулатион. Исимулатионрекордингкаллбакк. Плайбаккстатечанжед (Microsoft. Перцептионсимулатион. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-554">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="0ff18-555">Вызывается при изменении состояния воспроизведения Исимулатионрекординг.</span><span class="sxs-lookup"><span data-stu-id="0ff18-555">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="0ff18-556">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-556">Parameters</span></span>
* <span data-ttu-id="0ff18-557">newState — новое состояние записи.</span><span class="sxs-lookup"><span data-stu-id="0ff18-557">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="0ff18-558">Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер</span><span class="sxs-lookup"><span data-stu-id="0ff18-558">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="0ff18-559">Корневой объект для создания объектов имитации восприятия.</span><span class="sxs-lookup"><span data-stu-id="0ff18-559">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="0ff18-560">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Креатеперцептионсимулатионманажер (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-560">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="0ff18-561">Создать на объекте для создания смоделированных пакетов и доставки их в предоставленный приемник.</span><span class="sxs-lookup"><span data-stu-id="0ff18-561">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="0ff18-562">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-562">Parameters</span></span>
* <span data-ttu-id="0ff18-563">приемник — приемник, который будет принимать все созданные пакеты.</span><span class="sxs-lookup"><span data-stu-id="0ff18-563">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="0ff18-564">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0ff18-564">Return value</span></span>

<span data-ttu-id="0ff18-565">Созданный диспетчер.</span><span class="sxs-lookup"><span data-stu-id="0ff18-565">The created Manager.</span></span>

<span data-ttu-id="0ff18-566">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Креатеперцептионсимулатионрекординг (System. String)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-566">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="0ff18-567">Создание приемника, в котором хранятся все полученные пакеты в файле по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="0ff18-567">Create a sink, which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="0ff18-568">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-568">Parameters</span></span>
* <span data-ttu-id="0ff18-569">путь — путь к создаваемому файлу.</span><span class="sxs-lookup"><span data-stu-id="0ff18-569">path - The path of the file to create.</span></span>

<span data-ttu-id="0ff18-570">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0ff18-570">Return value</span></span>

<span data-ttu-id="0ff18-571">Созданный приемник.</span><span class="sxs-lookup"><span data-stu-id="0ff18-571">The created sink.</span></span>

<span data-ttu-id="0ff18-572">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Лоадперцептионсимулатионрекординг (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-572">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="0ff18-573">Загрузка записи из указанного файла.</span><span class="sxs-lookup"><span data-stu-id="0ff18-573">Load a recording from the specified file.</span></span>

<span data-ttu-id="0ff18-574">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-574">Parameters</span></span>
* <span data-ttu-id="0ff18-575">путь — путь к загружаемому файлу.</span><span class="sxs-lookup"><span data-stu-id="0ff18-575">path - The path of the file to load.</span></span>
* <span data-ttu-id="0ff18-576">Factory — фабрика, используемая записью для создания Исимулатионстреамсинк при необходимости.</span><span class="sxs-lookup"><span data-stu-id="0ff18-576">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="0ff18-577">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0ff18-577">Return value</span></span>

<span data-ttu-id="0ff18-578">Загруженная запись.</span><span class="sxs-lookup"><span data-stu-id="0ff18-578">The loaded recording.</span></span>

<span data-ttu-id="0ff18-579">**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Лоадперцептионсимулатионрекординг (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-579">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="0ff18-580">Загрузка записи из указанного файла.</span><span class="sxs-lookup"><span data-stu-id="0ff18-580">Load a recording from the specified file.</span></span>

<span data-ttu-id="0ff18-581">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-581">Parameters</span></span>
* <span data-ttu-id="0ff18-582">путь — путь к загружаемому файлу.</span><span class="sxs-lookup"><span data-stu-id="0ff18-582">path - The path of the file to load.</span></span>
* <span data-ttu-id="0ff18-583">Factory — фабрика, используемая записью для создания Исимулатионстреамсинк при необходимости.</span><span class="sxs-lookup"><span data-stu-id="0ff18-583">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="0ff18-584">обратный вызов — обратный вызов, который получает обновления, которые обновляют состояние записи.</span><span class="sxs-lookup"><span data-stu-id="0ff18-584">callback - A callback, which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="0ff18-585">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0ff18-585">Return value</span></span>

<span data-ttu-id="0ff18-586">Загруженная запись.</span><span class="sxs-lookup"><span data-stu-id="0ff18-586">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="0ff18-587">Microsoft. Перцептионсимулатион. Стреамдататипес</span><span class="sxs-lookup"><span data-stu-id="0ff18-587">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="0ff18-588">Описывает различные типы потоковых данных.</span><span class="sxs-lookup"><span data-stu-id="0ff18-588">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

<span data-ttu-id="0ff18-589">**Microsoft. Перцептионсимулатион. Стреамдататипес. None**</span><span class="sxs-lookup"><span data-stu-id="0ff18-589">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="0ff18-590">Значение Sentinel, используемое для обозначения отсутствия типов данных потока.</span><span class="sxs-lookup"><span data-stu-id="0ff18-590">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="0ff18-591">**Microsoft. Перцептионсимулатион. Стреамдататипес. Head**</span><span class="sxs-lookup"><span data-stu-id="0ff18-591">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="0ff18-592">Поток данных для положения и ориентации головного элемента.</span><span class="sxs-lookup"><span data-stu-id="0ff18-592">Stream of data for the position and orientation of the head.</span></span>

<span data-ttu-id="0ff18-593">**Microsoft. Перцептионсимулатион. Стреамдататипес. руки**</span><span class="sxs-lookup"><span data-stu-id="0ff18-593">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="0ff18-594">Поток данных для расположения и жестов стрелок.</span><span class="sxs-lookup"><span data-stu-id="0ff18-594">Stream of data for the position and gestures of hands.</span></span>

<span data-ttu-id="0ff18-595">**Microsoft. Перцептионсимулатион. Стреамдататипес. Спатиалмаппинг**</span><span class="sxs-lookup"><span data-stu-id="0ff18-595">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="0ff18-596">Поток данных для пространственного сопоставления среды.</span><span class="sxs-lookup"><span data-stu-id="0ff18-596">Stream of data for spatial mapping of the environment.</span></span>

<span data-ttu-id="0ff18-597">**Microsoft. Перцептионсимулатион. Стреамдататипес. Калибровка**</span><span class="sxs-lookup"><span data-stu-id="0ff18-597">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="0ff18-598">Поток данных для калибровки устройства.</span><span class="sxs-lookup"><span data-stu-id="0ff18-598">Stream of data for calibration of the device.</span></span> <span data-ttu-id="0ff18-599">Пакеты калибровки принимаются только системой в удаленном режиме.</span><span class="sxs-lookup"><span data-stu-id="0ff18-599">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="0ff18-600">**Microsoft. Перцептионсимулатион. Стреамдататипес. Environment**</span><span class="sxs-lookup"><span data-stu-id="0ff18-600">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="0ff18-601">Поток данных для среды устройства.</span><span class="sxs-lookup"><span data-stu-id="0ff18-601">Stream of data for the environment of the device.</span></span>

<span data-ttu-id="0ff18-602">**Microsoft. Перцептионсимулатион. Стреамдататипес. Сиксдофконтроллерс**</span><span class="sxs-lookup"><span data-stu-id="0ff18-602">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="0ff18-603">Поток данных для контроллеров движения.</span><span class="sxs-lookup"><span data-stu-id="0ff18-603">Stream of data for motion controllers.</span></span>

<span data-ttu-id="0ff18-604">**Microsoft. Перцептионсимулатион. Стреамдататипес. глаза**</span><span class="sxs-lookup"><span data-stu-id="0ff18-604">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="0ff18-605">Поток данных с глазами имитации человека.</span><span class="sxs-lookup"><span data-stu-id="0ff18-605">Stream of data with the eyes of the simulated human.</span></span>

<span data-ttu-id="0ff18-606">**Microsoft. Перцептионсимулатион. Стреамдататипес. Дисплайконфигуратион**</span><span class="sxs-lookup"><span data-stu-id="0ff18-606">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="0ff18-607">Поток данных с конфигурацией экрана устройства.</span><span class="sxs-lookup"><span data-stu-id="0ff18-607">Stream of data with the display configuration of the device.</span></span>

<span data-ttu-id="0ff18-608">**Microsoft. Перцептионсимулатион. Стреамдататипес. ALL**</span><span class="sxs-lookup"><span data-stu-id="0ff18-608">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="0ff18-609">Значение Sentinel, используемое для указания всех записанных типов данных.</span><span class="sxs-lookup"><span data-stu-id="0ff18-609">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="0ff18-610">Microsoft. Перцептионсимулатион. Исимулатионстреамсинк</span><span class="sxs-lookup"><span data-stu-id="0ff18-610">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="0ff18-611">Объект, получающий пакеты данных из потока имитации.</span><span class="sxs-lookup"><span data-stu-id="0ff18-611">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="0ff18-612">**Microsoft. Перцептионсимулатион. Исимулатионстреамсинк. Онпаккетрецеивед (длина uint, Byte [], пакет)**</span><span class="sxs-lookup"><span data-stu-id="0ff18-612">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="0ff18-613">Получает один пакет, который внутренне типизирован и имеет версию.</span><span class="sxs-lookup"><span data-stu-id="0ff18-613">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="0ff18-614">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ff18-614">Parameters</span></span>
* <span data-ttu-id="0ff18-615">Длина — Длина пакета.</span><span class="sxs-lookup"><span data-stu-id="0ff18-615">length - The length of the packet.</span></span>
* <span data-ttu-id="0ff18-616">пакет — данные пакета.</span><span class="sxs-lookup"><span data-stu-id="0ff18-616">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="0ff18-617">Microsoft. Перцептионсимулатион. Исимулатионстреамсинкфактори</span><span class="sxs-lookup"><span data-stu-id="0ff18-617">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="0ff18-618">Объект, создающий Исимулатионстреамсинк.</span><span class="sxs-lookup"><span data-stu-id="0ff18-618">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="0ff18-619">**Microsoft. Перцептионсимулатион. Исимулатионстреамсинкфактори. Креатесимулатионстреамсинк ()**</span><span class="sxs-lookup"><span data-stu-id="0ff18-619">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="0ff18-620">Создает единственный экземпляр Исимулатионстреамсинк.</span><span class="sxs-lookup"><span data-stu-id="0ff18-620">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="0ff18-621">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0ff18-621">Return value</span></span>

<span data-ttu-id="0ff18-622">Созданный приемник.</span><span class="sxs-lookup"><span data-stu-id="0ff18-622">The created sink.</span></span>
