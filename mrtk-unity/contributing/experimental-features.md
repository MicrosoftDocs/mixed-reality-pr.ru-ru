---
title: Экспериментальные функции
description: Документ, относящийся к экспериментальным функциям в МРТК.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 341ba0ee3e5900cc52f1ef715232f49064102309
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121382"
---
# <a name="experimental-features"></a><span data-ttu-id="ebdfc-104">Экспериментальные функции</span><span class="sxs-lookup"><span data-stu-id="ebdfc-104">Experimental features</span></span>

<span data-ttu-id="ebdfc-105">Некоторые функции, на которых работает команда МРТК, имеют большое значение, даже если мы не полностью создали подробные сведения.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-105">Some features the MRTK team works on appear to have a lot of initial value even if we haven’t fully fleshed out the details.</span></span> <span data-ttu-id="ebdfc-106">Для этих типов функций мы хотим, чтобы сообщество познакомиться с ними на раннем этапе.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-106">For these types of features, we want the community to get a chance to see them early.</span></span> <span data-ttu-id="ebdfc-107">Так как они находятся на раннем этапе цикла, мы помечаем их как экспериментальные, чтобы указать, что они продолжают развиваться и могут меняться со временем.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-107">Because they are early in the cycle, we label them as experimental to indicate that they are still evolving, and subject to change over time.</span></span>

## <a name="what-to-expect-from-an-experimental-feature"></a><span data-ttu-id="ebdfc-108">Что следует делать в экспериментальной функции</span><span class="sxs-lookup"><span data-stu-id="ebdfc-108">What to expect from an experimental feature</span></span>

<span data-ttu-id="ebdfc-109">Если компонент помечен как экспериментальный, вы можете рассчитывать на следующее:</span><span class="sxs-lookup"><span data-stu-id="ebdfc-109">If a component is marked experimental you can expect the following:</span></span>

- <span data-ttu-id="ebdfc-110">Пример сцены, демонстрирующий использование, расположенное под `MRTK/Examples/Experimental` вложенной папкой</span><span class="sxs-lookup"><span data-stu-id="ebdfc-110">An example scene demonstrating usage, located under `MRTK/Examples/Experimental` sub-folder</span></span>
- <span data-ttu-id="ebdfc-111">В экспериментальных функциях могут отсутствовать документы.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-111">Experimental features may not have docs.</span></span>
- <span data-ttu-id="ebdfc-112">Возможно, у них нет тестов.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-112">They probably don't have tests.</span></span>
- <span data-ttu-id="ebdfc-113">Экспериментальные функции могут быть изменены.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-113">Experimental features are subject to change.</span></span>

## <a name="experimental-feature-guidelines"></a><span data-ttu-id="ebdfc-114">Экспериментальные рекомендации по функциям</span><span class="sxs-lookup"><span data-stu-id="ebdfc-114">Experimental feature guidelines</span></span>

### <a name="experimental-code-should-live-in-a-separate-folder"></a><span data-ttu-id="ebdfc-115">Экспериментальный код должен находиться в отдельной папке</span><span class="sxs-lookup"><span data-stu-id="ebdfc-115">Experimental code should live in a separate folder</span></span>

<span data-ttu-id="ebdfc-116">Экспериментальный код должен попасть в экспериментальную папку верхнего уровня, за которой следует имя экспериментальной функции.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-116">Experimental code should go into a top-level experimental folder followed by the experimental feature name.</span></span> <span data-ttu-id="ebdfc-117">Например, если попытаться создать новый компонент FooBar, разместите код следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ebdfc-117">For example, if trying to contribute a new feature FooBar, put code in the following:</span></span>

- <span data-ttu-id="ebdfc-118">Примеры сцен, переходы по сценариям `MRTK/Examples/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="ebdfc-118">Example scenes, scripts go into `MRTK/Examples/Experimental/FooBar/`</span></span>
- <span data-ttu-id="ebdfc-119">Скрипты компонентов, Prefabs `MRTK/SDK/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="ebdfc-119">Component scripts, prefabs go into `MRTK/SDK/Experimental/FooBar/`</span></span>
- <span data-ttu-id="ebdfc-120">Переходят инспекторы компонентов `MRTK/SDK/Inspectors/Experimental/FooBar`</span><span class="sxs-lookup"><span data-stu-id="ebdfc-120">Component inspectors go into `MRTK/SDK/Inspectors/Experimental/FooBar`</span></span>

<span data-ttu-id="ebdfc-121">При использовании вложенных папок в имени экспериментальной функции попробуйте создать зеркальную копию той же структуры папок МРТК.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-121">When using sub-folders under the experimental feature name, try to mirror the same folder structure of MRTK.</span></span>

<span data-ttu-id="ebdfc-122">Например, поисковые решения будут выглядеть по адресу `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span><span class="sxs-lookup"><span data-stu-id="ebdfc-122">For example, solvers would go under `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span></span>

<span data-ttu-id="ebdfc-123">Не заключайте сцены в папку сцены вверху: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span><span class="sxs-lookup"><span data-stu-id="ebdfc-123">Keep scenes in a scene folder near the top: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span></span>

> [!NOTE]
> <span data-ttu-id="ebdfc-124">Мы не будем использовать одну экспериментальную корневую папку `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` .</span><span class="sxs-lookup"><span data-stu-id="ebdfc-124">We considered not having a single Experimental root folder and instead putting Experimental under say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity`.</span></span> <span data-ttu-id="ebdfc-125">Мы решили открыть папки в базе, чтобы упростить обнаружение экспериментальных функций.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-125">We decided to go with folders at the base to make the experimental features easier to discover.</span></span>

### <a name="experimental-code-should-be-in-a-special-namespace"></a><span data-ttu-id="ebdfc-126">Экспериментальный код должен находиться в специальном пространстве имен</span><span class="sxs-lookup"><span data-stu-id="ebdfc-126">Experimental code should be in a special namespace</span></span>

<span data-ttu-id="ebdfc-127">Убедитесь, что экспериментальный код находится в экспериментальном пространстве имен, соответствующем неэкспериментальному расположению.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-127">Ensure that the experimental code lives in an experimental namespace that matches the non-experimental location.</span></span> <span data-ttu-id="ebdfc-128">Например, если компонент является частью поиска решений `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , его пространство имен должно быть `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .</span><span class="sxs-lookup"><span data-stu-id="ebdfc-128">For example, if your component is part of solvers at `Microsoft.MixedReality.Toolkit.Utilities.Solvers`, its namespace should be `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers`.</span></span>

<span data-ttu-id="ebdfc-129">Пример см. в [этой](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) статье.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-129">See [this PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) for an example.</span></span>

### <a name="experimental-features-should-have-an-experimental-attribute"></a><span data-ttu-id="ebdfc-130">Экспериментальные функции должны иметь атрибут [экспериментальный]</span><span class="sxs-lookup"><span data-stu-id="ebdfc-130">Experimental features should have an [Experimental] attribute</span></span>

<span data-ttu-id="ebdfc-131">Добавьте `[Experimental]` атрибут над одним из полей, чтобы в редакторе компонентов отображалось небольшое диалоговое окно, в котором упоминается ваша функция, которая подвергается значительным изменениям.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-131">Add an `[Experimental]` attribute above one of your fields to have a small dialog appear in the component editor that mentions your feature is experimental and subject to significant changes.</span></span>

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a><span data-ttu-id="ebdfc-132">Меню экспериментальных функций следует открывать в подменю "экспериментальные"</span><span class="sxs-lookup"><span data-stu-id="ebdfc-132">Menus for experimental features should go under "Experimental" sub-menu</span></span>

<span data-ttu-id="ebdfc-133">Убедитесь, что экспериментальные функции находятся в подменю "экспериментальные" при добавлении команд в меню редактора.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-133">Ensure that experimental features are under "experimental" sub-menus when adding commands to menus in the editor.</span></span> <span data-ttu-id="ebdfc-134">Вот несколько таких случаев.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-134">Here are a few examples:</span></span>

<span data-ttu-id="ebdfc-135">Добавление команды меню верхнего уровня:</span><span class="sxs-lookup"><span data-stu-id="ebdfc-135">Adding a top-level menu command:</span></span>

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

<span data-ttu-id="ebdfc-136">Добавление меню компонента:</span><span class="sxs-lookup"><span data-stu-id="ebdfc-136">Adding a component menu:</span></span>

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a><span data-ttu-id="ebdfc-137">Документация</span><span class="sxs-lookup"><span data-stu-id="ebdfc-137">Documentation</span></span>

<span data-ttu-id="ebdfc-138">Чтобы добавить документацию для экспериментальной функции, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-138">Follow these steps to add documentation for your experimental feature:</span></span>

1. <span data-ttu-id="ebdfc-139">Любая документация для экспериментальной функции должна находиться в `readme.md` файле в экспериментальной папке.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-139">Any documentation for an experimental feature should go in a `readme.md` file in the experimental folder.</span></span> <span data-ttu-id="ebdfc-140">Например, МРТК/SDK/экспериментальный/Пулсешадер/readme. md.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-140">For example, MRTK/SDK/Experimental/PulseShader/readme.md.</span></span>

1. <span data-ttu-id="ebdfc-141">В разделе *обзоры функций* добавьте ссылку в *экспериментальном* разделе по адресу [`Documentation/toc.yml`](../toc.yml) .</span><span class="sxs-lookup"><span data-stu-id="ebdfc-141">Under *Feature Overviews* Add a link in the *Experimental* section at [`Documentation/toc.yml`](../toc.yml).</span></span>

### <a name="minimize-impact-to-mrtk-code"></a><span data-ttu-id="ebdfc-142">Уменьшение влияния на код МРТК</span><span class="sxs-lookup"><span data-stu-id="ebdfc-142">Minimize impact to MRTK code</span></span>

<span data-ttu-id="ebdfc-143">В то время как изменение МРТК может повлиять на работу вашего эксперимента, оно может оказать влияние на других людей.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-143">While your MRTK change might get your experiment to work, it could impact other people in ways you do not expect.</span></span>
<span data-ttu-id="ebdfc-144">Любые регрессии, вносимые в основной код МРТК, приведут к возврату запроса на включение внесенных изменений.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-144">Any regressions you make to the MRTK core code would result in your pull request getting reverted.</span></span>

<span data-ttu-id="ebdfc-145">Не следует вносить изменения в папки, отличные от экспериментальных папок.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-145">Aim to have zero changes in folders other than experimental folders.</span></span> <span data-ttu-id="ebdfc-146">Ниже приведен список папок, в которых могут быть экспериментальные изменения.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-146">Here is a list of folders that can have experimental changes:</span></span>

- <span data-ttu-id="ebdfc-147">МРТК/SDK/экспериментальная версия</span><span class="sxs-lookup"><span data-stu-id="ebdfc-147">MRTK/SDK/Experimental</span></span>
- <span data-ttu-id="ebdfc-148">МРТК/SDK/инспекторы/экспериментальные</span><span class="sxs-lookup"><span data-stu-id="ebdfc-148">MRTK/SDK/Inspectors/Experimental</span></span>
- <span data-ttu-id="ebdfc-149">МРТК/примеры/экспериментальные</span><span class="sxs-lookup"><span data-stu-id="ebdfc-149">MRTK/Examples/Experimental</span></span>

<span data-ttu-id="ebdfc-150">Изменения за пределами этих папок следует тщательно обрабатывать.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-150">Changes outside of these folders should be treated very carefully.</span></span> <span data-ttu-id="ebdfc-151">Если экспериментальная функция должна включать изменения в основной код МРТК, рассмотрите возможность разделения изменений МРТК в отдельный запрос на вытягивание, включающий в себя тесты и документацию.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-151">If your experimental feature must include changes to MRTK core code, consider splitting out MRTK changes into a separate pull request that includes tests and documentation.</span></span>

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a><span data-ttu-id="ebdfc-152">Использование экспериментальной функции не должно повлиять на возможность использования основных элементов управления пользователями</span><span class="sxs-lookup"><span data-stu-id="ebdfc-152">Using your experimental feature should not impact people's ability to use core controls</span></span>

<span data-ttu-id="ebdfc-153">Большинство людей используют основные компоненты UX, такие как кнопка, Манипулатионхандлер и взаимодействующие очень часто.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-153">Most people use core UX components like the button, ManipulationHandler and Interactable very frequently.</span></span> <span data-ttu-id="ebdfc-154">Скорее всего, они не будут использовать экспериментальную функцию, если они не позволяют использовать кнопки.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-154">They will likely not use your experimental feature if it prevents them from using buttons.</span></span>

<span data-ttu-id="ebdfc-155">Использование компонента не должно прерывать кнопки, Манипулатионхандлер, BoundingBox или взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-155">Using your component should not break buttons, ManipulationHandler, BoundingBox, or interactable.</span></span>

<span data-ttu-id="ebdfc-156">Например, в [этом скроллаблеобжектколлектионе](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), добавление скроллаблеобжектколлектион привело к тому, что пользователи не смогут использовать кнопку HoloLens Prefabs.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-156">For example, in [this ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), adding a ScrollableObjectCollection caused people to not be able to use the HoloLens button prefabs.</span></span> <span data-ttu-id="ebdfc-157">Несмотря на то, что это не было вызвано ошибкой в запросе на вытягивание (но, в своюмся случае, уже имеющей существующую ошибку), это не позволило получить запрос на возврат.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-157">Even though this was not caused by a bug in the PR (but rather exposed an existing bug), it prevented the PR from getting checked in.</span></span>

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a><span data-ttu-id="ebdfc-158">Укажите пример сцены, демонстрирующий использование этой функции</span><span class="sxs-lookup"><span data-stu-id="ebdfc-158">Provide an example scene that demonstrates how to use the feature</span></span>

<span data-ttu-id="ebdfc-159">Пользователям необходимо узнать, как использовать вашу функцию и как ее тестировать.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-159">People need to see how to use your feature, and how to test it.</span></span>

<span data-ttu-id="ebdfc-160">Укажите пример в разделе МРТК/examples/экспериментальный/YOUR_FEATURE</span><span class="sxs-lookup"><span data-stu-id="ebdfc-160">Provide an example under MRTK/Examples/Experimental/YOUR_FEATURE</span></span>

### <a name="minimize-user-visible-flaws-in-experimental-features"></a><span data-ttu-id="ebdfc-161">Сокращение числа видимых пользователем недостатков в экспериментальных функциях</span><span class="sxs-lookup"><span data-stu-id="ebdfc-161">Minimize user visible flaws in experimental features</span></span>

<span data-ttu-id="ebdfc-162">Другие не будут использовать экспериментальный компонент, если он не работает, но не будет перейдет к функции.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-162">Others will not use the experimental feature if it does not work, it will not graduate to a feature.</span></span>

<span data-ttu-id="ebdfc-163">Протестируйте пример сцены на целевой платформе, убедитесь, что он работает должным образом.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-163">Test your example scene on your target platform, make sure it works as expected.</span></span> <span data-ttu-id="ebdfc-164">Убедитесь, что ваша функция также работает в редакторе, чтобы пользователи могли быстро выполнять итерации и видеть вашу функцию, даже если у них нет целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-164">Make sure your feature also works in editor, so people can rapidly iterate and see your feature even if they don’t have the target platform.</span></span>

## <a name="graduating-experimental-code-into-mrtk-code"></a><span data-ttu-id="ebdfc-165">Экспериментальный пример кода в код МРТК</span><span class="sxs-lookup"><span data-stu-id="ebdfc-165">Graduating experimental code into MRTK code</span></span>

<span data-ttu-id="ebdfc-166">Если функция приостанавливается на большом объеме использования, мы должны углубиться в основной код МРТК.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-166">If a feature ends up seeing quite a lot of use, then we should graduate it into core MRTK code.</span></span> <span data-ttu-id="ebdfc-167">Для этого компонент должен иметь тесты, документацию и пример сцены.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-167">To do this, the feature should have tests, documentation, and an example scene.</span></span>

<span data-ttu-id="ebdfc-168">Когда вы будете готовы приступить к работе с функцией МРТК, создайте вопрос для возврата запроса на вытягивание.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-168">When you are ready to graduate the feature MRTK, create an issue to check in your PR against.</span></span> <span data-ttu-id="ebdfc-169">В запрос на включение внесенных изменений должны быть включены все, что необходимо, чтобы сделать эту основную функцию: тесты, документация и пример сцены, демонстрирующий использование.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-169">The PR should include all the things needed to make this a core feature: tests, documentation, and an example scene showing usage.</span></span>

<span data-ttu-id="ebdfc-170">Кроме того, не забудьте обновить пространства имен, чтобы удалить "экспериментальное" подпространство.</span><span class="sxs-lookup"><span data-stu-id="ebdfc-170">Also, don’t forget to update the namespaces to remove the “Experimental” subspace.</span></span>
