---
title: Написание и выполнение тестов
description: Модульные тесты для проверки надежности МРТК.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, UnitTest,
ms.openlocfilehash: c8efb192982a1cb9ca07e91d29a69b11aaffc290
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177116"
---
# <a name="writing-and-running-tests"></a><span data-ttu-id="d4e48-104">Написание и выполнение тестов</span><span class="sxs-lookup"><span data-stu-id="d4e48-104">Writing and running tests</span></span>

<span data-ttu-id="d4e48-105">Чтобы обеспечить надежность МРТК, МРТК имеет набор тестов, которые гарантируют, что изменения в коде не порегрессируют существующее поведение.</span><span class="sxs-lookup"><span data-stu-id="d4e48-105">To ensure MRTK is reliable, MRTK has a set of tests to ensure that changes to the code does not regress existing behavior.</span></span> <span data-ttu-id="d4e48-106">Наличие хорошего объема тестирования в больших базах кода, таких как МРТК, крайне важно для обеспечения стабильности и уверенности при внесении изменений.</span><span class="sxs-lookup"><span data-stu-id="d4e48-106">Having good test coverage in a big codebase like MRTK is crucial for stability and having confidence when making changes.</span></span>

<span data-ttu-id="d4e48-107">МРТК использует средство выполнения [тестов Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) , которое использует интеграцию Unity в [NUnit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="d4e48-107">MRTK uses the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) which uses a Unity integration of [NUnit](https://nunit.org/).</span></span> <span data-ttu-id="d4e48-108">В этом руководство будет представлена отправная точка для добавления тестов в МРТК.</span><span class="sxs-lookup"><span data-stu-id="d4e48-108">This guide will provide a starting point on how to add tests to MRTK.</span></span> <span data-ttu-id="d4e48-109">Не будет объяснено средство выполнения [тестов Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) и [NUnit](https://nunit.org/) , которые можно искать в предоставленных ссылках.</span><span class="sxs-lookup"><span data-stu-id="d4e48-109">It will not explain the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) and [NUnit](https://nunit.org/) which can be looked up in the links provided.</span></span>

<span data-ttu-id="d4e48-110">Перед отправкой запроса на вытягивание необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="d4e48-110">Before submitting a pull request, make sure to:</span></span>

1. <span data-ttu-id="d4e48-111">Выполните тесты локально, чтобы изменения не проверяли существующее поведение (завершение вытягивание не будет разрешено, если какие-либо тесты завершаются сбоем).</span><span class="sxs-lookup"><span data-stu-id="d4e48-111">Run the tests locally so your changes don't regress existing behavior (completing PRs won't be allowed if any tests fail).</span></span>

1. <span data-ttu-id="d4e48-112">При исправлении ошибки напишите тест для тестирования исправления и убедитесь, что будущие изменения кода не нарушат его.</span><span class="sxs-lookup"><span data-stu-id="d4e48-112">If fixing a bug, write a test to test the fix and ensure that future code modifications won't break it again.</span></span>

1. <span data-ttu-id="d4e48-113">Если вы записываете функцию, напишите новые тесты, чтобы предотвратить внесение изменений в код, нарушающих эту функцию.</span><span class="sxs-lookup"><span data-stu-id="d4e48-113">If writing a feature, write new tests to prevent upcoming code changes breaking this feature.</span></span>

<span data-ttu-id="d4e48-114">В настоящее время плаймоде тесты предназначены для выполнения в Unity 2018,4 и могут завершаться ошибкой в других версиях Unity</span><span class="sxs-lookup"><span data-stu-id="d4e48-114">Currently playmode tests are meant to be run in Unity 2018.4 and may fail in other versions of Unity</span></span>

## <a name="running-tests"></a><span data-ttu-id="d4e48-115">Выполнение тестов</span><span class="sxs-lookup"><span data-stu-id="d4e48-115">Running tests</span></span>

### <a name="unity-editor"></a><span data-ttu-id="d4e48-116">Редактор Unity</span><span class="sxs-lookup"><span data-stu-id="d4e48-116">Unity editor</span></span>

<span data-ttu-id="d4e48-117">Средство выполнения [тестов Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) можно найти в **окне**"Общее средство выполнения  >    >  **тестов** " и отобразит все доступные тесты мртк Play и Edit Mode.</span><span class="sxs-lookup"><span data-stu-id="d4e48-117">The [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) can be found under **Window** > **General** > **Test Runner** and will show all available MRTK play and edit mode tests.</span></span>

### <a name="command-line"></a><span data-ttu-id="d4e48-118">Командная строка</span><span class="sxs-lookup"><span data-stu-id="d4e48-118">Command line</span></span>

<span data-ttu-id="d4e48-119">Тесты также можно выполнять с помощью сценария [PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) , расположенного по адресу `Scripts\test\run_playmode_tests.ps1` .</span><span class="sxs-lookup"><span data-stu-id="d4e48-119">Tests can also be run by a [powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) script located at `Scripts\test\run_playmode_tests.ps1`.</span></span> <span data-ttu-id="d4e48-120">Тесты плаймоде будут выполняться точно так же, как они выполняются в GitHub/CI (см. ниже), и результаты выводятся на печать.</span><span class="sxs-lookup"><span data-stu-id="d4e48-120">This will run the playmode tests exactly as they are executed on github / CI (see below), and print results.</span></span> <span data-ttu-id="d4e48-121">Ниже приведены некоторые примеры выполнения сценария.</span><span class="sxs-lookup"><span data-stu-id="d4e48-121">Here are some examples of how to run the script</span></span>

<span data-ttu-id="d4e48-122">Выполнение тестов в проекте, расположенном по адресу Х:\мртк.Дев, с Unity 2018,4 (например, Unity 2018.4.26 F1)</span><span class="sxs-lookup"><span data-stu-id="d4e48-122">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4 (for example Unity 2018.4.26f1)</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

<span data-ttu-id="d4e48-123">Выполнение тестов в проекте, расположенном по адресу Х:\мртк.Дев, с Unity 2018,4, вывод результатов в C:\ playmode_test_out</span><span class="sxs-lookup"><span data-stu-id="d4e48-123">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4, output results to C:\playmode_test_out</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

<span data-ttu-id="d4e48-124">Можно также выполнять тесты плаймоде несколько раз с помощью `run_repeat_tests.ps1` скрипта.</span><span class="sxs-lookup"><span data-stu-id="d4e48-124">It's also possible to run the playmode tests multiple times via the `run_repeat_tests.ps1` script.</span></span> <span data-ttu-id="d4e48-125">Все параметры, используемые в `run_playmode_tests.ps1` , могут использоваться.</span><span class="sxs-lookup"><span data-stu-id="d4e48-125">All parameters used in `run_playmode_tests.ps1` may be used.</span></span>

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a><span data-ttu-id="d4e48-126">Проверка запроса на вытягивание</span><span class="sxs-lookup"><span data-stu-id="d4e48-126">Pull request validation</span></span>

<span data-ttu-id="d4e48-127">МРТК CI будет создавать МРТК во всех конфигурациях и выполнять все тесты режима редактирования и воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="d4e48-127">MRTK's CI will build MRTK in all configurations and run all edit and play mode tests.</span></span> <span data-ttu-id="d4e48-128">CI можно активировать, публикуя комментарий на GitHub, `/azp run mrtk_pr` Если у пользователя есть необходимые права.</span><span class="sxs-lookup"><span data-stu-id="d4e48-128">CI can be triggered by posting a comment on the github PR `/azp run mrtk_pr` if the user has sufficient rights.</span></span> <span data-ttu-id="d4e48-129">Запуски CI можно увидеть на вкладке "проверки" запроса на вытягивание.</span><span class="sxs-lookup"><span data-stu-id="d4e48-129">CI runs can be seen in the 'checks' tab of the PR.</span></span>

<span data-ttu-id="d4e48-130">Только после успешного прохождения всех тестов запрос на включение внесенных изменений можно объединить в Main.</span><span class="sxs-lookup"><span data-stu-id="d4e48-130">Only after all of the tests have passed successfully can the PR be merged into main.</span></span>

### <a name="stress-tests--bulk-tests"></a><span data-ttu-id="d4e48-131">Нагрузочные тесты и групповые тесты</span><span class="sxs-lookup"><span data-stu-id="d4e48-131">Stress tests / bulk tests</span></span>

<span data-ttu-id="d4e48-132">Иногда тесты будут завершаться сбоем только в то время, что может быть непростой для отладки.</span><span class="sxs-lookup"><span data-stu-id="d4e48-132">Sometimes tests will only fail occasionally which can be frustrating to debug.</span></span>

<span data-ttu-id="d4e48-133">Чтобы несколько тестовых запусков выполнялись локально, измените их в соответствии с тестовыми скриптами.</span><span class="sxs-lookup"><span data-stu-id="d4e48-133">To have multiple test runs locally, modify the according test scripts.</span></span> <span data-ttu-id="d4e48-134">Следующий сценарий Python должен сделать этот сценарий более удобным.</span><span class="sxs-lookup"><span data-stu-id="d4e48-134">The following python script should make this scenario more convenient.</span></span>

<span data-ttu-id="d4e48-135">Для выполнения скрипта Python необходимо [установить Python 3. X](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="d4e48-135">Prerequisite for running the python script is having [Python 3.X installed](https://www.python.org/downloads/).</span></span>

<span data-ttu-id="d4e48-136">Для одного теста, который должен выполняться несколько раз:</span><span class="sxs-lookup"><span data-stu-id="d4e48-136">For a single test that needs to be executed multiple times:</span></span>

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="d4e48-137">Выполните следующую команду из командной строки (рекомендуется использовать[PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) ).</span><span class="sxs-lookup"><span data-stu-id="d4e48-137">Run the following from a command line ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) is recommended)</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

<span data-ttu-id="d4e48-138">Скопируйте и вставьте выходные данные в файл теста.</span><span class="sxs-lookup"><span data-stu-id="d4e48-138">Copy and paste the output into your test file.</span></span> <span data-ttu-id="d4e48-139">Следующий скрипт предназначен для выполнения нескольких тестов последовательно:</span><span class="sxs-lookup"><span data-stu-id="d4e48-139">The following script is for running multiple tests in sequence:</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

<span data-ttu-id="d4e48-140">Теперь новый файл теста должен содержать</span><span class="sxs-lookup"><span data-stu-id="d4e48-140">The new test file should now contain</span></span>

```c#
[UnityTest]
public IEnumerator A1MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A2MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A3MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A4MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="d4e48-141">Откройте средство выполнения тестов и просмотрите новые тесты, которые теперь можно вызывать многократно.</span><span class="sxs-lookup"><span data-stu-id="d4e48-141">Open the test runner and observe the new tests that can now be called repeatedly.</span></span>

## <a name="writing-tests"></a><span data-ttu-id="d4e48-142">Написание тестов</span><span class="sxs-lookup"><span data-stu-id="d4e48-142">Writing tests</span></span>

<span data-ttu-id="d4e48-143">Существует два типа тестов, которые можно добавить в новый код.</span><span class="sxs-lookup"><span data-stu-id="d4e48-143">There are two types of tests that can be added for new code</span></span>

* <span data-ttu-id="d4e48-144">Тесты режима воспроизведения</span><span class="sxs-lookup"><span data-stu-id="d4e48-144">Play mode tests</span></span>
* <span data-ttu-id="d4e48-145">Проверка режима редактирования</span><span class="sxs-lookup"><span data-stu-id="d4e48-145">Edit mode tests</span></span>

### <a name="play-mode-tests"></a><span data-ttu-id="d4e48-146">Тесты режима воспроизведения</span><span class="sxs-lookup"><span data-stu-id="d4e48-146">Play mode tests</span></span>

<span data-ttu-id="d4e48-147">Тесты режима воспроизведения МРТК позволяют протестировать реакцию новой функции на различные источники входных данных, такие как руки или глаза.</span><span class="sxs-lookup"><span data-stu-id="d4e48-147">MRTK play mode tests have the ability to test how your new feature responds to different input sources such as hands or eyes.</span></span>

<span data-ttu-id="d4e48-148">Новые тесты режима воспроизведения могут наследовать [басеплаймодетестс](xref:Microsoft.MixedReality.Toolkit.Tests) или можно использовать приведенную ниже схему.</span><span class="sxs-lookup"><span data-stu-id="d4e48-148">New play mode tests can inherit [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) or the skeleton below can be used.</span></span>

<span data-ttu-id="d4e48-149">Чтобы создать новый тест режима воспроизведения, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="d4e48-149">To create a new play mode test:</span></span>

* <span data-ttu-id="d4e48-150">Перейдите к разделу активы > МРТК > Tests > Плаймодетестс</span><span class="sxs-lookup"><span data-stu-id="d4e48-150">Navigate to Assets > MRTK > Tests > PlayModeTests</span></span>
* <span data-ttu-id="d4e48-151">Щелкните правой кнопкой мыши, создайте > тестирование > скрипт теста C#</span><span class="sxs-lookup"><span data-stu-id="d4e48-151">Right click, Create > Testing > C# Test Script</span></span>
* <span data-ttu-id="d4e48-152">Замените шаблон по умолчанию на показанную ниже схему.</span><span class="sxs-lookup"><span data-stu-id="d4e48-152">Replace the default template with the skeleton below</span></span>

```c#
#if !WINDOWS_UWP
// When the .NET scripting backend is enabled and C# projects are built
// The assembly that this file is part of is still built for the player,
// even though the assembly itself is marked as a test assembly (this is not
// expected because test assemblies should not be included in player builds).
// Because the .NET backend is deprecated in 2018 and removed in 2019 and this
// issue will likely persist for 2018, this issue is worked around by wrapping all
// play mode tests in this check.

using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using NUnit.Framework;
using System;
using System.Collections;
using System.Linq;
using UnityEngine;
using UnityEngine.TestTools;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class ExamplePlayModeTests
    {
        // This method is called once before we enter play mode and execute any of the tests
        // do any kind of setup here that can't be done in playmode
        public void Setup()
        {
            // eg installing unity packages is only possible in edit mode
            // so if a test requires TextMeshPro we will need to check for the package before entering play mode
            PlayModeTestUtilities.InstallTextMeshProEssentials();
        }

        // Do common setup for each of your tests here - this will be called for each individual test after entering playmode
        // Note that this uses UnitySetUp instead of [SetUp] because the init function needs to await a frame passing
        // to ensure that the MRTK system has had the chance to fully set up before the test runs.
        [UnitySetUp]
        public IEnumerator Init()
        {
            // in most play mode test cases you would want to at least create an MRTK GameObject using the default profile
            TestUtilities.InitializeMixedRealityToolkit(true);
            yield return null;
        }

        // Destroy the scene - this method is called after each test listed below has completed
        // Note that this uses UnityTearDown instead of [TearDown] because the init function needs to await a frame passing
        // to ensure that the MRTK system has fully torn down before the next test setup->run cycle starts.
        [UnityTearDown]
        public IEnumerator TearDown()
        {
            PlayModeTestUtilities.TearDown();
            yield return null;
        }

        #region Tests

        /// <summary>
        /// Skeleton for a new MRTK play mode test.
        /// </summary>
        [UnityTest]
        public IEnumerator TestMyFeature()
        {
            // ----------------------------------------------------------
            // EXAMPLE PLAY MODE TEST METHODS
            // ----------------------------------------------------------
            // Getting the input system
            // var inputSystem = PlayModeTestUtilities.GetInputSystem();

            // Creating a new test hand for input
            // var rightHand = new TestHand(Handedness.Right);
            // yield return rightHand.Show(new Vector3(0, 0, 0.5f));

            // Moving the new test hand
            // We are doing a yield return here because moving the hand to a new position
            // requires multiple frames to complete the action.
            // yield return rightHand.MoveTo(new Vector3(0, 0, 2.0f));

            // Getting a specific pointer from the hand
            // var linePointer = PointerUtils.GetPointer<LinePointer>(Handedness.Right);
            // Assert.IsNotNull(linePointer);
            // ---------------------------------------------------------

            // Your new test here
            yield return null;
        }
        #endregion
    }
}
#endif
```

### <a name="edit-mode-tests"></a><span data-ttu-id="d4e48-153">Проверка режима редактирования</span><span class="sxs-lookup"><span data-stu-id="d4e48-153">Edit mode tests</span></span>

<span data-ttu-id="d4e48-154">тесты режима редактирования выполняются в режиме редактирования Unity и могут быть добавлены в папку **мртк**  >  **tests**  >  **едитмодетестс** в репозитории смешанной реальности набор средств.</span><span class="sxs-lookup"><span data-stu-id="d4e48-154">Edit mode tests are executed in Unity's edit mode and can be added under the **MRTK** > **Tests** > **EditModeTests** folder in the Mixed Reality Toolkit repo.</span></span>
<span data-ttu-id="d4e48-155">Для создания нового теста можно использовать следующий шаблон:</span><span class="sxs-lookup"><span data-stu-id="d4e48-155">To create a new test the following template can be used:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.

using NUnit.Framework;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class EditModeExampleTest
    {
        [Test]
        /// the name of this method will be used as test name in the unity test runner
        public void TestEditModeExampleFeature()
        {

        }
    }
}
```

### <a name="test-naming-conventions"></a><span data-ttu-id="d4e48-156">Проверка соглашений об именовании</span><span class="sxs-lookup"><span data-stu-id="d4e48-156">Test naming conventions</span></span>

<span data-ttu-id="d4e48-157">Тесты обычно должны называться в зависимости от тестируемого класса или сценария, в котором они тестируются.</span><span class="sxs-lookup"><span data-stu-id="d4e48-157">Tests should generally be named based on the class they are testing, or the scenario that they are testing.</span></span>
<span data-ttu-id="d4e48-158">Например, при наличии проверенного класса:</span><span class="sxs-lookup"><span data-stu-id="d4e48-158">For example, given a to-be-tested class:</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

<span data-ttu-id="d4e48-159">Рассмотрите возможность именования теста</span><span class="sxs-lookup"><span data-stu-id="d4e48-159">Consider naming the test</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

<span data-ttu-id="d4e48-160">Рассмотрите возможность размещения теста в иерархии папок, похожей на соответствующий файл, не являющийся тестом.</span><span class="sxs-lookup"><span data-stu-id="d4e48-160">Consider placing the test in a folder hierarchy that is similar to its corresponding non-test file.</span></span>
<span data-ttu-id="d4e48-161">Пример.</span><span class="sxs-lookup"><span data-stu-id="d4e48-161">For example:</span></span>

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

<span data-ttu-id="d4e48-162">Это позволяет убедиться в том, что существует четкий способ найти соответствующий тестовый класс каждого класса, если такой тестовый класс существует.</span><span class="sxs-lookup"><span data-stu-id="d4e48-162">This is to ensure that there's a clear an obvious way of finding each class's corresponding test class, if such a test class exists.</span></span>

<span data-ttu-id="d4e48-163">Размещение тестов на основе сценариев менее определено — если тест выполняет свою общую входную систему, например, Попробуйте поместить его в папку "Инпутсистем" в соответствующей папке для режима редактирования или проверки в режиме воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="d4e48-163">Placement of scenario based tests is less defined - if the test exercises the overall input system, for example, consider putting it into an "InputSystem" folder in the corresponding edit mode or play mode test folder.</span></span>

### <a name="test-script-icons"></a><span data-ttu-id="d4e48-164">Значки тестовых скриптов</span><span class="sxs-lookup"><span data-stu-id="d4e48-164">Test script icons</span></span>

<span data-ttu-id="d4e48-165">При добавлении нового теста измените скрипт, чтобы он имел правильный значок МРТК.</span><span class="sxs-lookup"><span data-stu-id="d4e48-165">When adding a new test, please modify the script to have the correct MRTK icon.</span></span> <span data-ttu-id="d4e48-166">Существует простое средство МРТК для этого:</span><span class="sxs-lookup"><span data-stu-id="d4e48-166">There's an easy MRTK tool to do so:</span></span>

1. <span data-ttu-id="d4e48-167">переход к пункту меню "смешанная реальность" набор средств</span><span class="sxs-lookup"><span data-stu-id="d4e48-167">Go go the Mixed Reality Toolkit menu item</span></span>
1. <span data-ttu-id="d4e48-168">Щелкните Служебные программы, затем обновить, а затем — значки.</span><span class="sxs-lookup"><span data-stu-id="d4e48-168">Click on Utilities, then Update, then Icons</span></span>
1. <span data-ttu-id="d4e48-169">Щелкните тесты, и обновление будет запущено автоматически, после чего в скрипты теста отсутствуют значки.</span><span class="sxs-lookup"><span data-stu-id="d4e48-169">Click on Tests, and the updater will run automatically, updating any test scripts missing their icons</span></span>

### <a name="mrtk-utility-methods"></a><span data-ttu-id="d4e48-170">Методы служебной программы МРТК</span><span class="sxs-lookup"><span data-stu-id="d4e48-170">MRTK Utility methods</span></span>

<span data-ttu-id="d4e48-171">В этом разделе показаны некоторые из часто используемых фрагментов кода и методов при написании тестов для МРТК.</span><span class="sxs-lookup"><span data-stu-id="d4e48-171">This section shows some of the commonly used code snippets / methods when writing tests for MRTK.</span></span>

<span data-ttu-id="d4e48-172">Существует два служебных класса, помогающих настроить МРТК и тестирование взаимодействия с компонентами в МРТК</span><span class="sxs-lookup"><span data-stu-id="d4e48-172">There are two Utility classes that help with setting up MRTK and testing interactions with components in MRTK</span></span>

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

<span data-ttu-id="d4e48-173">Тестутилитиес предоставляют следующие методы настройки сцены МРТК и объекты gameobject:</span><span class="sxs-lookup"><span data-stu-id="d4e48-173">TestUtilities provide the following methods to set up your MRTK scene and GameObjects:</span></span>

```c#
/// creates the mrtk GameObject and sets the default profile if passed param is true
TestUtilities.InitializeMixedRealityToolkit()

/// creates an empty scene prior to adding the mrtk GameObject to it
TestUtilities.InitializeMixedRealityToolkitAndCreateScenes();

/// sets the initial playspace transform and camera position
TestUtilities.InitializePlayspace();

/// destroys previously created mrtk GameObject and playspace
TestUtilities.ShutdownMixedRealityToolkit();
```

<span data-ttu-id="d4e48-174">Дополнительные [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) методы этих классов util см. в документации по API, [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) так как они расширены на регулярной основе, а новые тесты добавляются в мртк.</span><span class="sxs-lookup"><span data-stu-id="d4e48-174">Please refer to the API docs of [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) and [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) for further methods of these util classes as they're extended on a regular basis while new tests get added to MRTK.</span></span>
