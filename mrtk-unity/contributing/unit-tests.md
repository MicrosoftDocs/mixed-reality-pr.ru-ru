---
title: Написание и выполнение тестов
description: Модульные тесты для проверки надежности МРТК.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, UnitTest,
ms.openlocfilehash: 85c8a330d9af5b0d91c2b1b838ead7d10d97f981
ms.sourcegitcommit: 3176df29fb0c9508751bd370f1211031d50d2c14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/28/2021
ms.locfileid: "129148669"
---
# <a name="writing-and-running-tests"></a>Написание и выполнение тестов

Чтобы обеспечить надежность МРТК, МРТК имеет набор тестов, которые гарантируют, что изменения в коде не порегрессируют существующее поведение. Наличие хорошего объема тестирования в больших базах кода, таких как МРТК, крайне важно для обеспечения стабильности и уверенности при внесении изменений.

МРТК использует средство выполнения [тестов Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) , которое использует интеграцию Unity в [NUnit](https://nunit.org/). В этом руководство будет представлена отправная точка для добавления тестов в МРТК. Не будет объяснено средство выполнения [тестов Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) и [NUnit](https://nunit.org/) , которые можно искать в предоставленных ссылках.

Перед отправкой запроса на вытягивание необходимо выполнить следующие действия.

1. Выполните тесты локально, чтобы изменения не проверяли существующее поведение (завершение вытягивание не будет разрешено, если какие-либо тесты завершаются сбоем).

1. При исправлении ошибки напишите тест для тестирования исправления и убедитесь, что будущие изменения кода не нарушат его.

1. Если вы записываете функцию, напишите новые тесты, чтобы предотвратить внесение изменений в код, нарушающих эту функцию.

В настоящее время плаймоде тесты предназначены для выполнения в Unity 2018,4 и могут завершаться ошибкой в других версиях Unity

## <a name="running-tests"></a>Выполнение тестов

### <a name="unity-editor"></a>Редактор Unity

Средство выполнения [тестов Unity](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) можно найти в **окне**"Общее средство выполнения  >    >  **тестов** " и отобразит все доступные тесты мртк Play и Edit Mode.

### <a name="command-line"></a>Командная строка

Тесты также можно выполнять с помощью сценария [PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) , расположенного по адресу `Scripts\test\run_playmode_tests.ps1` . Тесты плаймоде будут выполняться точно так же, как они выполняются в GitHub/CI (см. ниже), и результаты выводятся на печать. Ниже приведены некоторые примеры выполнения сценария.

Выполнение тестов в проекте, расположенном по адресу Х:\мртк.Дев, с Unity 2018,4 (например, Unity 2018.4.26 F1)

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

Выполнение тестов в проекте, расположенном по адресу Х:\мртк.Дев, с Unity 2018,4, вывод результатов в C:\ playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

Можно также выполнять тесты плаймоде несколько раз с помощью `run_repeat_tests.ps1` скрипта. Все параметры, используемые в `run_playmode_tests.ps1` , могут использоваться.

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>Проверка запроса на вытягивание

МРТК CI будет создавать МРТК во всех конфигурациях и выполнять все тесты режима редактирования и воспроизведения. CI можно активировать, публикуя комментарий на GitHub, `/azp run mrtk_pr` Если у пользователя есть необходимые права. Запуски CI можно увидеть на вкладке "проверки" запроса на вытягивание.

Только после успешного прохождения всех тестов запрос на включение внесенных изменений можно объединить в Main.

### <a name="stress-tests--bulk-tests"></a>Нагрузочные тесты и групповые тесты

Иногда тесты будут завершаться сбоем только в то время, что может быть непростой для отладки.

Чтобы несколько тестовых запусков выполнялись локально, измените их в соответствии с тестовыми скриптами. Следующий сценарий Python должен сделать этот сценарий более удобным.

Для выполнения скрипта Python необходимо [установить Python 3. X](https://www.python.org/downloads/).

Для одного теста, который должен выполняться несколько раз:

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

Выполните следующую команду из командной строки (рекомендуется использовать[PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) ).

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

Скопируйте и вставьте выходные данные в файл теста. Следующий скрипт предназначен для выполнения нескольких тестов последовательно:

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

Теперь новый файл теста должен содержать

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

Откройте средство выполнения тестов и просмотрите новые тесты, которые теперь можно вызывать многократно.

## <a name="writing-tests"></a>Написание тестов

Существует два типа тестов, которые можно добавить в новый код.

* Тесты режима воспроизведения
* Проверка режима редактирования

### <a name="play-mode-tests"></a>Тесты режима воспроизведения

Тесты режима воспроизведения МРТК позволяют протестировать реакцию новой функции на различные источники входных данных, такие как руки или глаза.

Новые тесты режима воспроизведения могут наследовать [басеплаймодетестс](xref:Microsoft.MixedReality.Toolkit.Tests) или можно использовать приведенную ниже схему.

Чтобы создать новый тест режима воспроизведения, выполните следующие действия.

* Перейдите к разделу активы > МРТК > Tests > Плаймодетестс
* Щелкните правой кнопкой мыши, создайте > тестирование > скрипт теста C#
* Замените шаблон по умолчанию на показанную ниже схему.

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

### <a name="edit-mode-tests"></a>Проверка режима редактирования

тесты режима редактирования выполняются в режиме редактирования Unity и могут быть добавлены в папку **мртк**  >  **tests**  >  **едитмодетестс** в репозитории смешанной реальности набор средств.
Для создания нового теста можно использовать следующий шаблон:

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

### <a name="test-naming-conventions"></a>Проверка соглашений об именовании

Тесты обычно должны называться в зависимости от тестируемого класса или сценария, в котором они тестируются.
Например, при наличии проверенного класса:

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

Рассмотрите возможность именования теста

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

Рассмотрите возможность размещения теста в иерархии папок, похожей на соответствующий файл, не являющийся тестом.
Пример:

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

Это позволяет убедиться в том, что существует четкий способ найти соответствующий тестовый класс каждого класса, если такой тестовый класс существует.

Размещение тестов на основе сценариев менее определено — если тест выполняет свою общую входную систему, например, Попробуйте поместить его в папку "Инпутсистем" в соответствующей папке для режима редактирования или проверки в режиме воспроизведения.

### <a name="test-script-icons"></a>Значки тестовых скриптов

При добавлении нового теста измените скрипт, чтобы он имел правильный значок МРТК. Существует простое средство МРТК для этого:

1. переход к пункту меню "смешанная реальность" набор средств
1. Щелкните Служебные программы, затем обновить, а затем — значки.
1. Щелкните тесты, и обновление будет запущено автоматически, после чего в скрипты теста отсутствуют значки.

### <a name="mrtk-utility-methods"></a>Методы служебной программы МРТК

В этом разделе показаны некоторые из часто используемых фрагментов кода и методов при написании тестов для МРТК.

Существует два служебных класса, помогающих настроить МРТК и тестирование взаимодействия с компонентами в МРТК

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

Тестутилитиес предоставляют следующие методы настройки сцены МРТК и объекты gameobject:

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

Дополнительные [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) методы этих классов util см. в документации по API, [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) так как они расширены на регулярной основе, а новые тесты добавляются в мртк.
