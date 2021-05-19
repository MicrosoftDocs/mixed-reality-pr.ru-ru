---
title: Рекомендации по кодированию
description: принципы программирования и соглашения, которым следует следовать при участии в МРТК.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, C#,
ms.openlocfilehash: 8887e248bd550bdd7a59f19c16df1ec3647ceff7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145240"
---
# <a name="coding-guidelines"></a><span data-ttu-id="0af5a-104">Рекомендации по программированию</span><span class="sxs-lookup"><span data-stu-id="0af5a-104">Coding guidelines</span></span>

<span data-ttu-id="0af5a-105">В этом документе описываются принципы и соглашения по написанию кода, которым следует следовать при добавлении в МРТК.</span><span class="sxs-lookup"><span data-stu-id="0af5a-105">This document outlines coding principles and conventions to follow when contributing to MRTK.</span></span>

---

## <a name="philosophy"></a><span data-ttu-id="0af5a-106">Подход</span><span class="sxs-lookup"><span data-stu-id="0af5a-106">Philosophy</span></span>

### <a name="be-concise-and-strive-for-simplicity"></a><span data-ttu-id="0af5a-107">Будьте кратко и стремитесь к простоте</span><span class="sxs-lookup"><span data-stu-id="0af5a-107">Be concise and strive for simplicity</span></span>

<span data-ttu-id="0af5a-108">Наиболее простым решением зачастую является лучшее решение.</span><span class="sxs-lookup"><span data-stu-id="0af5a-108">The simplest solution is often the best.</span></span> <span data-ttu-id="0af5a-109">Это переопределение предназначено для этих рекомендаций и должно быть целью всего действия кодирования.</span><span class="sxs-lookup"><span data-stu-id="0af5a-109">This is an overriding aim of these guidelines and should be the goal of all coding activity.</span></span> <span data-ttu-id="0af5a-110">Часть простой является краткой и согласуется с существующим кодом.</span><span class="sxs-lookup"><span data-stu-id="0af5a-110">Part of being simple is being concise, and consistent with existing code.</span></span> <span data-ttu-id="0af5a-111">Постарайтесь не усложнять свой код.</span><span class="sxs-lookup"><span data-stu-id="0af5a-111">Try to keep your code simple.</span></span>

<span data-ttu-id="0af5a-112">Читатели должны столкнуться только с артефактами, которые предоставляют полезную информацию.</span><span class="sxs-lookup"><span data-stu-id="0af5a-112">Readers should only encounter artifacts that provide useful information.</span></span> <span data-ttu-id="0af5a-113">Например, комментарии, изменяющие, что очевидны, не предоставляют дополнительных сведений и увеличивают коэффициент шума до сигнала.</span><span class="sxs-lookup"><span data-stu-id="0af5a-113">For example, comments that restate what is obvious provide no extra information and increase the noise to signal ratio.</span></span>

<span data-ttu-id="0af5a-114">Старайтесь не усложнять логику кода.</span><span class="sxs-lookup"><span data-stu-id="0af5a-114">Keep code logic simple.</span></span> <span data-ttu-id="0af5a-115">Обратите внимание, что это не инструкция по использованию минимального числа строк, минимизации размера имен идентификаторов или стиля фигурных скобок, но об уменьшении числа концепций и максимизации видимости этих элементов с помощью привычных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="0af5a-115">Note that this is not a statement about using the fewest number of lines, minimizing the size of identifier names or brace style, but about reducing the number of concepts and maximizing the visibility of those through familiar patterns.</span></span>

### <a name="produce-consistent-readable-code"></a><span data-ttu-id="0af5a-116">Создание единообразного, доступного для чтения кода</span><span class="sxs-lookup"><span data-stu-id="0af5a-116">Produce consistent, readable code</span></span>

<span data-ttu-id="0af5a-117">Удобочитаемость кода соотносится с низкой частотой дефектов.</span><span class="sxs-lookup"><span data-stu-id="0af5a-117">Code readability is correlated with low defect rates.</span></span> <span data-ttu-id="0af5a-118">Стремитесь создавать код, который легко читать.</span><span class="sxs-lookup"><span data-stu-id="0af5a-118">Strive to create code that is easy to read.</span></span> <span data-ttu-id="0af5a-119">Стремитесь создавать код, который имеет простую логику и повторно использует существующие компоненты, так как он также позволяет гарантировать правильность.</span><span class="sxs-lookup"><span data-stu-id="0af5a-119">Strive to create code that has simple logic and re-uses existing components as it will also help ensure correctness.</span></span>

<span data-ttu-id="0af5a-120">Все сведения о коде, которые вы создаете, от самых основных сведений о правильности до единообразного стиля и форматирования.</span><span class="sxs-lookup"><span data-stu-id="0af5a-120">All details of the code you produce matter, from the most basic detail of correctness to consistent style and formatting.</span></span> <span data-ttu-id="0af5a-121">Стиль написания кода следует использовать в соответствии с уже существующим, даже если он не соответствует вашим предпочтениям.</span><span class="sxs-lookup"><span data-stu-id="0af5a-121">Keep your coding style consistent with what already exists, even if it is not matching your preference.</span></span> <span data-ttu-id="0af5a-122">Это повышает удобочитаемость общей базы кода.</span><span class="sxs-lookup"><span data-stu-id="0af5a-122">This increases the readability of the overall codebase.</span></span>

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a><span data-ttu-id="0af5a-123">Поддержка настройки компонентов как в редакторе, так и во время выполнения</span><span class="sxs-lookup"><span data-stu-id="0af5a-123">Support configuring components both in editor and at run-time</span></span>

<span data-ttu-id="0af5a-124">МРТК поддерживает различные пользователи — люди, предпочитающие настраивать компоненты в редакторе Unity и загрузку Prefabs, а также пользователей, которым необходимо создавать экземпляры и настраивать объекты во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0af5a-124">MRTK supports a diverse set of users – people who prefer to configure components in the Unity editor and load prefabs, and people who need to instantiate and configure objects at run-time.</span></span>

<span data-ttu-id="0af5a-125">Весь код должен работать как при добавлении компонента к GameObject в сохраненной сцене, так и при создании экземпляра этого компонента в коде.</span><span class="sxs-lookup"><span data-stu-id="0af5a-125">All your code should work by BOTH adding a component to a GameObject in a saved scene, and by instantiating that component in code.</span></span> <span data-ttu-id="0af5a-126">Тесты должны включать тестовый случай как для создания экземпляра Prefabs, так и для создания экземпляра, настройки компонента во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0af5a-126">Tests should include a test case both for instantiating prefabs and instantiating, configuring the component at runtime.</span></span>

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a><span data-ttu-id="0af5a-127">Первая и Основная целевая платформа для воспроизведения в редакторе</span><span class="sxs-lookup"><span data-stu-id="0af5a-127">Play-in-editor is your first and primary target platform</span></span>

<span data-ttu-id="0af5a-128">Воспроизведение в редакторе — это самый быстрый способ выполнить итерацию в Unity.</span><span class="sxs-lookup"><span data-stu-id="0af5a-128">Play-In-Editor is the fastest way to iterate in Unity.</span></span> <span data-ttu-id="0af5a-129">Предоставить нашим клиентам возможность быстро и быстро разрабатывать решения, а затем испытать другие идеи.</span><span class="sxs-lookup"><span data-stu-id="0af5a-129">Providing ways for our customers to iterate quickly allows them to both develop solutions more quickly and try out more ideas.</span></span> <span data-ttu-id="0af5a-130">Другими словами, увеличение скорости итерации повышает эффективность наших клиентов.</span><span class="sxs-lookup"><span data-stu-id="0af5a-130">In other words, maximizing the speed of iteration empowers our customers to achieve more.</span></span>

<span data-ttu-id="0af5a-131">Сделайте все работу в редакторе, а затем убедитесь, что она работает на любой другой платформе.</span><span class="sxs-lookup"><span data-stu-id="0af5a-131">Make everything work in editor, then make it work on any other platform.</span></span> <span data-ttu-id="0af5a-132">Не отключайте его работу в редакторе.</span><span class="sxs-lookup"><span data-stu-id="0af5a-132">Keep it working in the editor.</span></span> <span data-ttu-id="0af5a-133">Можно легко добавить новую платформу для воспроизведения в редакторе.</span><span class="sxs-lookup"><span data-stu-id="0af5a-133">It is easy to add a new platform to Play-In-Editor.</span></span> <span data-ttu-id="0af5a-134">Если приложение работает только на устройстве, работа в редакторе очень сложна.</span><span class="sxs-lookup"><span data-stu-id="0af5a-134">It is very difficult to get Play-In-Editor working if your app only works on a device.</span></span>

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a><span data-ttu-id="0af5a-135">Добавлять новые открытые поля, свойства, методы и сериализованные закрытые поля с осторожностью</span><span class="sxs-lookup"><span data-stu-id="0af5a-135">Add new public fields, properties, methods and serialized private fields with care</span></span>

<span data-ttu-id="0af5a-136">Каждый раз, когда вы добавляете открытый метод, поле, свойство, он станет частью общедоступной области API МРТК.</span><span class="sxs-lookup"><span data-stu-id="0af5a-136">Every time you add a public method, field, property, it becomes part of MRTK’s public API surface.</span></span> <span data-ttu-id="0af5a-137">Закрытые поля, помеченные как, `[SerializeField]` также предоставляют поля для редактора и являются частью общедоступной области API.</span><span class="sxs-lookup"><span data-stu-id="0af5a-137">Private fields marked with `[SerializeField]` also expose fields to the editor and are part of the public API surface.</span></span> <span data-ttu-id="0af5a-138">Другие пользователи могут использовать этот открытый метод, настраивать пользовательский Prefabs с помощью общедоступного поля и зависеть от него.</span><span class="sxs-lookup"><span data-stu-id="0af5a-138">Other people might use that public method, configure custom prefabs with your public field, and take a dependency on it.</span></span>

<span data-ttu-id="0af5a-139">Новые открытые члены следует тщательно проверять.</span><span class="sxs-lookup"><span data-stu-id="0af5a-139">New public members should be carefully examined.</span></span> <span data-ttu-id="0af5a-140">Любое общедоступное поле должно поддерживаться в будущем.</span><span class="sxs-lookup"><span data-stu-id="0af5a-140">Any public field will need to be maintained in the future.</span></span> <span data-ttu-id="0af5a-141">Помните, что если тип открытого поля (или сериализованного закрытого поля) изменяется или удаляется из одноименного поведения, это может нарушить работу других пользователей.</span><span class="sxs-lookup"><span data-stu-id="0af5a-141">Remember that if the type of a public field (or serialized private field) changes or gets removed from a MonoBehaviour, that could break other people.</span></span> <span data-ttu-id="0af5a-142">Поле должно быть рекомендовано к выпуску, а код для переноса изменений для людей, которые затратили зависимости, должен быть предоставлен.</span><span class="sxs-lookup"><span data-stu-id="0af5a-142">The field will need to first be deprecated for a release, and code to migrate changes for people that have taken dependencies would need to be provided.</span></span>

### <a name="prioritize-writing-tests"></a><span data-ttu-id="0af5a-143">Определение приоритетов при написании тестов</span><span class="sxs-lookup"><span data-stu-id="0af5a-143">Prioritize writing tests</span></span>

<span data-ttu-id="0af5a-144">МРТК — это проект сообщества, который изменяется различными участниками.</span><span class="sxs-lookup"><span data-stu-id="0af5a-144">MRTK is a community project, modified by a diverse range of contributors.</span></span> <span data-ttu-id="0af5a-145">Эти участники могут не иметь сведений об исправлении или функции, а также случайно привести к нарушению работы функции.</span><span class="sxs-lookup"><span data-stu-id="0af5a-145">These contributors may not know the details of your bug fix / feature, and accidentally break your feature.</span></span> <span data-ttu-id="0af5a-146">[Мртк выполняет тесты непрерывной интеграции](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) перед выполнением каждого запроса на включение внесенных изменений.</span><span class="sxs-lookup"><span data-stu-id="0af5a-146">[MRTK runs continuous integration tests](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) before completing every pull request.</span></span> <span data-ttu-id="0af5a-147">Изменения, которые нарушают тесты, не могут быть возвращены.</span><span class="sxs-lookup"><span data-stu-id="0af5a-147">Changes that break tests cannot be checked in.</span></span> <span data-ttu-id="0af5a-148">Таким образом, тесты являются лучшим способом гарантировать, что другие пользователи не нарушат вашу функцию.</span><span class="sxs-lookup"><span data-stu-id="0af5a-148">Therefore, tests are the best way to ensure that other people do not break your feature.</span></span>

<span data-ttu-id="0af5a-149">При исправлении ошибки напишите тест, чтобы убедиться в том, что она не будет регрессия в будущем.</span><span class="sxs-lookup"><span data-stu-id="0af5a-149">When you fix a bug, write a test to ensure it does not regress in the future.</span></span> <span data-ttu-id="0af5a-150">При добавлении функции напишите тесты, которые проверяют работу функции.</span><span class="sxs-lookup"><span data-stu-id="0af5a-150">If adding a feature, write tests that verify your feature works.</span></span> <span data-ttu-id="0af5a-151">Это необходимо для всех функций UX, за исключением экспериментальных функций.</span><span class="sxs-lookup"><span data-stu-id="0af5a-151">This is required for all UX features except experimental features.</span></span>

## <a name="c-coding-conventions"></a><span data-ttu-id="0af5a-152">Соглашения о написании кода на C#</span><span class="sxs-lookup"><span data-stu-id="0af5a-152">C# Coding conventions</span></span>

### <a name="script-license-information-headers"></a><span data-ttu-id="0af5a-153">Создать скрипт для заголовков лицензионных данных</span><span class="sxs-lookup"><span data-stu-id="0af5a-153">Script license information headers</span></span>

<span data-ttu-id="0af5a-154">Все сотрудники корпорации Майкрософт, которые вносят новые файлы, должны добавить следующий стандартный заголовок лицензии в начало всех новых файлов, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="0af5a-154">All Microsoft employees contributing new files should add the following standard License header at the top of any new files, exactly as shown below:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a><span data-ttu-id="0af5a-155">Заголовки сводных сведений о функциях и методах</span><span class="sxs-lookup"><span data-stu-id="0af5a-155">Function / method summary headers</span></span>

<span data-ttu-id="0af5a-156">Все открытые классы, структуры, перечисления, функции, свойства, поля, публикуемые в МРТК, должны быть описаны в соответствии с их целями и использованием, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="0af5a-156">All public classes, structs, enums, functions, properties, fields posted to the MRTK should be described as to its purpose and use, exactly as shown below:</span></span>

```c#
/// <summary>
/// The Controller definition defines the Controller as defined by the SDK / Unity.
/// </summary>
public struct Controller
{
    /// <summary>
    /// The ID assigned to the Controller
    /// </summary>
    public string ID;
}
```

<span data-ttu-id="0af5a-157">Это гарантирует правильную создание и распространение документации для всех классов, методов и свойств.</span><span class="sxs-lookup"><span data-stu-id="0af5a-157">This ensures documentation is properly generated and disseminated for all all classes, methods, and properties.</span></span>

<span data-ttu-id="0af5a-158">Все файлы скриптов, отправленные без соответствующих тегов сводки, будут отклонены.</span><span class="sxs-lookup"><span data-stu-id="0af5a-158">Any script files submitted without proper summary tags will be rejected.</span></span>

### <a name="mrtk-namespace-rules"></a><span data-ttu-id="0af5a-159">Правила пространства имен МРТК</span><span class="sxs-lookup"><span data-stu-id="0af5a-159">MRTK namespace rules</span></span>

<span data-ttu-id="0af5a-160">Набор средств для смешанной реальности использует модель пространства имен на основе компонентов, где все базовые пространства имен начинаются с "Microsoft. Микседреалити. Toolkit".</span><span class="sxs-lookup"><span data-stu-id="0af5a-160">The Mixed Reality Toolkit uses a feature based namespace model, where all foundational namespaces begin with "Microsoft.MixedReality.Toolkit".</span></span> <span data-ttu-id="0af5a-161">В общем случае в пространствах имен не нужно указывать уровень набора средств (например, ядра, поставщиков, служб).</span><span class="sxs-lookup"><span data-stu-id="0af5a-161">In general, you need not specify the toolkit layer (ex: Core, Providers, Services) in your namespaces.</span></span>

<span data-ttu-id="0af5a-162">В настоящее время определены следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="0af5a-162">The currently defined namespaces are:</span></span>

- <span data-ttu-id="0af5a-163">Microsoft. Микседреалити. Toolkit</span><span class="sxs-lookup"><span data-stu-id="0af5a-163">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="0af5a-164">Microsoft. Микседреалити. Toolkit. граница</span><span class="sxs-lookup"><span data-stu-id="0af5a-164">Microsoft.MixedReality.Toolkit.Boundary</span></span>
- <span data-ttu-id="0af5a-165">Microsoft. Микседреалити. Toolkit. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="0af5a-165">Microsoft.MixedReality.Toolkit.Diagnostics</span></span>
- <span data-ttu-id="0af5a-166">Microsoft. Микседреалити. Toolkit. Editor</span><span class="sxs-lookup"><span data-stu-id="0af5a-166">Microsoft.MixedReality.Toolkit.Editor</span></span>
- <span data-ttu-id="0af5a-167">Microsoft. Микседреалити. Toolkit. input</span><span class="sxs-lookup"><span data-stu-id="0af5a-167">Microsoft.MixedReality.Toolkit.Input</span></span>
- <span data-ttu-id="0af5a-168">Microsoft. Микседреалити. Toolkit. Спатиалаваренесс</span><span class="sxs-lookup"><span data-stu-id="0af5a-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span></span>
- <span data-ttu-id="0af5a-169">Microsoft. Микседреалити. Toolkit. телепортируйтесь</span><span class="sxs-lookup"><span data-stu-id="0af5a-169">Microsoft.MixedReality.Toolkit.Teleport</span></span>
- <span data-ttu-id="0af5a-170">Microsoft. Микседреалити. Toolkit. Utilities</span><span class="sxs-lookup"><span data-stu-id="0af5a-170">Microsoft.MixedReality.Toolkit.Utilities</span></span>

<span data-ttu-id="0af5a-171">Для пространств имен с большим количеством типов можно создать ограниченное число подпространств имен, чтобы помочь в области использования.</span><span class="sxs-lookup"><span data-stu-id="0af5a-171">For namespaces with a large amount of types, it is acceptable to create a limited number of sub-namespaces to aid in scoping usage.</span></span>

<span data-ttu-id="0af5a-172">Пропуск пространства имен для интерфейса, класса или типа данных приведет к блокировке изменения.</span><span class="sxs-lookup"><span data-stu-id="0af5a-172">Omitting the namespace for an interface, class or data type will cause your change to be blocked.</span></span>

### <a name="adding-new-monobehaviour-scripts"></a><span data-ttu-id="0af5a-173">Добавление новых скриптов с несложным поведением</span><span class="sxs-lookup"><span data-stu-id="0af5a-173">Adding new MonoBehaviour scripts</span></span>

<span data-ttu-id="0af5a-174">При добавлении новых скриптов с поддержкой проведений с запросом на включение внесенных изменений убедитесь, что [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) атрибут применяется ко всем применимым файлам.</span><span class="sxs-lookup"><span data-stu-id="0af5a-174">When adding new MonoBehaviour scripts with a pull request, ensure the [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="0af5a-175">Это гарантирует, что компонент будет легко обнаруживаться в редакторе при нажатии кнопки *Добавить компонент* .</span><span class="sxs-lookup"><span data-stu-id="0af5a-175">This ensures the component is easily discoverable in the editor under the *Add Component* button.</span></span> <span data-ttu-id="0af5a-176">Флаг атрибута не требуется, если компонент не может отображаться в редакторе, например в абстрактном классе.</span><span class="sxs-lookup"><span data-stu-id="0af5a-176">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="0af5a-177">В приведенном ниже примере *пакет* должен быть заполнен расположением пакета компонента.</span><span class="sxs-lookup"><span data-stu-id="0af5a-177">In the example below, the *Package here* should be filled with the package location of the component.</span></span> <span data-ttu-id="0af5a-178">Если поместить элемент в папку *мртк/SDK* , пакет будет иметь значение *SDK*.</span><span class="sxs-lookup"><span data-stu-id="0af5a-178">If placing an item in *MRTK/SDK* folder, then the package will be *SDK*.</span></span>

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a><span data-ttu-id="0af5a-179">Добавление новых скриптов инспектора Unity</span><span class="sxs-lookup"><span data-stu-id="0af5a-179">Adding new Unity inspector scripts</span></span>

<span data-ttu-id="0af5a-180">Как правило, старайтесь не создавать пользовательские скрипты инспектора для компонентов МРТК.</span><span class="sxs-lookup"><span data-stu-id="0af5a-180">In general, try to avoid creating custom inspector scripts for MRTK components.</span></span> <span data-ttu-id="0af5a-181">Он добавляет дополнительную нагрузку и управление базой кода, которая может обрабатываться подсистемой Unity.</span><span class="sxs-lookup"><span data-stu-id="0af5a-181">It adds additional overhead and management of the codebase that could be handled by the Unity engine.</span></span>

<span data-ttu-id="0af5a-182">Если требуется класс инспектора, попробуйте использовать Unity [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) .</span><span class="sxs-lookup"><span data-stu-id="0af5a-182">If an inspector class is necessary, try to use Unity's [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html).</span></span> <span data-ttu-id="0af5a-183">Это опять упрощает класс инспектора и оставляет большую часть работы в Unity.</span><span class="sxs-lookup"><span data-stu-id="0af5a-183">This again simplifies the inspector class and leaves much of the work to Unity.</span></span>

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

<span data-ttu-id="0af5a-184">Если в классе инспектора требуется пользовательская отрисовка, попробуйте использовать [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) и [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) .</span><span class="sxs-lookup"><span data-stu-id="0af5a-184">If custom rendering is required in the inspector class, try to utilize [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) and [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html).</span></span> <span data-ttu-id="0af5a-185">Это обеспечит правильную обработку Unity вложенных Prefabs и измененных значений.</span><span class="sxs-lookup"><span data-stu-id="0af5a-185">This will ensure Unity correctly handles rendering nested prefabs and modified values.</span></span>

<span data-ttu-id="0af5a-186">Если [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) не может использоваться из-за необходимости в пользовательской логике, убедитесь, что все сведения об использовании заключены в оболочку [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) .</span><span class="sxs-lookup"><span data-stu-id="0af5a-186">If [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) cannot be used due to a requirement in custom logic, ensure all usage is wrapped around a [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html).</span></span> <span data-ttu-id="0af5a-187">Это обеспечит правильное отображение инспектора для вложенных Prefabs и измененных значений с заданным свойством.</span><span class="sxs-lookup"><span data-stu-id="0af5a-187">This will ensure Unity renders the inspector correctly for nested prefabs and modified values with the given property.</span></span>

<span data-ttu-id="0af5a-188">Более того, попробуйте снабдить пользовательский класс инспектора [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) .</span><span class="sxs-lookup"><span data-stu-id="0af5a-188">Furthermore, try to decorate the custom inspector class with a [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html).</span></span> <span data-ttu-id="0af5a-189">Этот тег гарантирует, что несколько объектов с этим компонентом в сцене можно будет выбрать и изменить вместе.</span><span class="sxs-lookup"><span data-stu-id="0af5a-189">This tag ensure multiple objects with this component in the scene can be selected and modified together.</span></span> <span data-ttu-id="0af5a-190">Все новые классы инспектора должны проверять, работает ли код в этой ситуации в сцене.</span><span class="sxs-lookup"><span data-stu-id="0af5a-190">Any new inspector classes should test that their code works in this situation in the scene.</span></span>

```c#
    // Example inspector class demonstrating usage of SerializedProperty & EditorGUILayout.PropertyField
    // as well as use of EditorGUI.PropertyScope for custom property logic
    [CustomEditor(typeof(MyComponent))]
    public class MyComponentInspector : UnityEditor.Editor
    {
        private SerializedProperty myProperty;
        private SerializedProperty handedness;

        protected virtual void OnEnable()
        {
            myProperty = serializedObject.FindProperty("myProperty");
            handedness = serializedObject.FindProperty("handedness");
        }

        public override void OnInspectorGUI()
        {
            EditorGUILayout.PropertyField(destroyOnSourceLost);

            Rect position = EditorGUILayout.GetControlRect();
            var label = new GUIContent(handedness.displayName);
            using (new EditorGUI.PropertyScope(position, label, handedness))
            {
                var currentHandedness = (Handedness)handedness.enumValueIndex;

                handedness.enumValueIndex = (int)(Handedness)EditorGUI.EnumPopup(
                    position,
                    label,
                    currentHandedness,
                    (value) => {
                        // This function is executed by Unity to determine if a possible enum value
                        // is valid for selection in the editor view
                        // In this case, only Handedness.Left and Handedness.Right can be selected
                        return (Handedness)value == Handedness.Left
                        || (Handedness)value == Handedness.Right;
                    });
            }
        }
    }
```

### <a name="adding-new-scriptableobjects"></a><span data-ttu-id="0af5a-191">Добавление нового Скриптаблеобжектс</span><span class="sxs-lookup"><span data-stu-id="0af5a-191">Adding new ScriptableObjects</span></span>

<span data-ttu-id="0af5a-192">При добавлении новых скриптов Скриптаблеобжект убедитесь, что [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) атрибут применяется ко всем применимым файлам.</span><span class="sxs-lookup"><span data-stu-id="0af5a-192">When adding new ScriptableObject scripts, ensure the [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="0af5a-193">Это гарантирует, что компонент легко обнаруживается в редакторе с помощью меню создания ресурсов.</span><span class="sxs-lookup"><span data-stu-id="0af5a-193">This ensures the component is easily discoverable in the editor via the asset creation menus.</span></span> <span data-ttu-id="0af5a-194">Флаг атрибута не требуется, если компонент не может отображаться в редакторе, например в абстрактном классе.</span><span class="sxs-lookup"><span data-stu-id="0af5a-194">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="0af5a-195">В приведенном ниже примере *вложенная папка* должна быть заполнена вложенной папкой мртк, если это применимо.</span><span class="sxs-lookup"><span data-stu-id="0af5a-195">In the example below, the *Subfolder* should be filled with the MRTK subfolder, if applicable.</span></span> <span data-ttu-id="0af5a-196">Если поместить элемент в папку *мртк/providers* , пакет будет иметь *поставщики*.</span><span class="sxs-lookup"><span data-stu-id="0af5a-196">If placing an item in *MRTK/Providers* folder, then the package will be *Providers*.</span></span> <span data-ttu-id="0af5a-197">Если поместить элемент в папку *мртк/Core* , задайте для него значение "Profiles".</span><span class="sxs-lookup"><span data-stu-id="0af5a-197">If placing an item in the *MRTK/Core* folder, set this to "Profiles".</span></span>

<span data-ttu-id="0af5a-198">В приведенном ниже примере — *MyNewService | Миневпровидер* должен быть заполнен новым классом Name (если применимо).</span><span class="sxs-lookup"><span data-stu-id="0af5a-198">In the example below, the *MyNewService | MyNewProvider* should be filled with the your new class' name, if applicable.</span></span> <span data-ttu-id="0af5a-199">Если поместить элемент в папку *микседреалититулкит* , оставьте эту строку.</span><span class="sxs-lookup"><span data-stu-id="0af5a-199">If placing an item in the *MixedRealityToolkit* folder, leave this string out.</span></span>

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a><span data-ttu-id="0af5a-200">Logging</span><span class="sxs-lookup"><span data-stu-id="0af5a-200">Logging</span></span>

<span data-ttu-id="0af5a-201">При добавлении новых или обновлении существующих компонентов рекомендуется добавить журналы Дебугутилитиес. Логвербосе в интересный код, который может быть полезен для последующей отладки.</span><span class="sxs-lookup"><span data-stu-id="0af5a-201">When adding new features or updating existing features, consider adding DebugUtilities.LogVerbose logs to interesting code that may be useful for future debugging.</span></span> <span data-ttu-id="0af5a-202">Существует компромисс между добавлением журналов и дополнительными помехами и недостаточным протоколированием (что затрудняет диагностику).</span><span class="sxs-lookup"><span data-stu-id="0af5a-202">There's a tradeoff here between adding logging and the added noise and not enough logging (which makes diagnosis difficult).</span></span>

<span data-ttu-id="0af5a-203">Интересный пример, где полезно ведение журнала (вместе с интересующими полезными данными):</span><span class="sxs-lookup"><span data-stu-id="0af5a-203">An interesting example where having logging is useful (along with interesting payload):</span></span>

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

<span data-ttu-id="0af5a-204">Этот тип ведения журнала может помочь в перехвате таких проблем [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) , как, вызванных несоответствием обнаруженных источников и потерянными событиями источника.</span><span class="sxs-lookup"><span data-stu-id="0af5a-204">This type of logging can help catch issues like [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016), which were caused by mismatched source detected and source lost events.</span></span>

<span data-ttu-id="0af5a-205">Не добавляйте журналы для данных и событий, происходящих при каждом кадре, в идеале, должны охватывать «интересные» события, управляемые различными входными данными пользователя (т. е. «щелчок» пользователем, а также набор изменений и событий, происходящих в журнале).</span><span class="sxs-lookup"><span data-stu-id="0af5a-205">Avoid adding logs for data and events that are occurring on every frame - ideally logging should cover "interesting" events driven by distinct user inputs (i.e. a "click" by a user and the set of changes and events that come from that are interesting to log).</span></span> <span data-ttu-id="0af5a-206">Текущее состояние "пользователь по-прежнему удерживает жест" записал каждый кадр в журнал не интересно, и журналы будут переполнены.</span><span class="sxs-lookup"><span data-stu-id="0af5a-206">The ongoing state of "user is still holding a gesture" logged every frame is not interesting and will overwhelm the logs.</span></span>

<span data-ttu-id="0af5a-207">Обратите внимание, что это подробное ведение журнала не включено по умолчанию (оно должно быть включено в [параметрах системы диагностики](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging)).</span><span class="sxs-lookup"><span data-stu-id="0af5a-207">Note that this verbose logging is not turned on by default (it must be enabled in the [Diagnostic System settings](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging))</span></span>

### <a name="spaces-vs-tabs"></a><span data-ttu-id="0af5a-208">Пробелы и знаки табуляции</span><span class="sxs-lookup"><span data-stu-id="0af5a-208">Spaces vs tabs</span></span>

<span data-ttu-id="0af5a-209">При участии в этом проекте обязательно используйте 4 пробела вместо вкладок.</span><span class="sxs-lookup"><span data-stu-id="0af5a-209">Please be sure to use 4 spaces instead of tabs when contributing to this project.</span></span>

### <a name="spacing"></a><span data-ttu-id="0af5a-210">Интервал</span><span class="sxs-lookup"><span data-stu-id="0af5a-210">Spacing</span></span>

<span data-ttu-id="0af5a-211">Не добавляйте дополнительные пробелы между квадратными скобками и круглыми скобками:</span><span class="sxs-lookup"><span data-stu-id="0af5a-211">Do not to add additional spaces between square brackets and parenthesis:</span></span>

#### <a name="dont"></a><span data-ttu-id="0af5a-212">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-212">Don't</span></span>

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a><span data-ttu-id="0af5a-213">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-213">Do</span></span>

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a><span data-ttu-id="0af5a-214">Соглашения об именах</span><span class="sxs-lookup"><span data-stu-id="0af5a-214">Naming conventions</span></span>

<span data-ttu-id="0af5a-215">Всегда используйте `PascalCase` для свойств.</span><span class="sxs-lookup"><span data-stu-id="0af5a-215">Always use `PascalCase` for properties.</span></span> <span data-ttu-id="0af5a-216">Используется `camelCase` для большинства полей, за исключением использования `PascalCase` для `static readonly` `const` полей и.</span><span class="sxs-lookup"><span data-stu-id="0af5a-216">Use `camelCase` for most fields, except use `PascalCase` for `static readonly` and `const` fields.</span></span> <span data-ttu-id="0af5a-217">Единственным исключением из этого является структура данных, требующая сериализации полей с помощью `JsonUtility` .</span><span class="sxs-lookup"><span data-stu-id="0af5a-217">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`.</span></span>

#### <a name="dont"></a><span data-ttu-id="0af5a-218">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-218">Don't</span></span>

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a><span data-ttu-id="0af5a-219">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-219">Do</span></span>

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a><span data-ttu-id="0af5a-220">Модификаторы доступа</span><span class="sxs-lookup"><span data-stu-id="0af5a-220">Access modifiers</span></span>

<span data-ttu-id="0af5a-221">Всегда объявляйте модификатор доступа для всех полей, свойств и методов.</span><span class="sxs-lookup"><span data-stu-id="0af5a-221">Always declare an access modifier for all fields, properties and methods.</span></span>

- <span data-ttu-id="0af5a-222">Все методы API Unity должны быть по `private` умолчанию, если их не нужно переопределять в производном классе.</span><span class="sxs-lookup"><span data-stu-id="0af5a-222">All Unity API Methods should be `private` by default, unless you need to override them in a derived class.</span></span> <span data-ttu-id="0af5a-223">В этом случае `protected` следует использовать.</span><span class="sxs-lookup"><span data-stu-id="0af5a-223">In this case `protected` should be used.</span></span>

- <span data-ttu-id="0af5a-224">Поля всегда должны иметь `private` значение, со `public` свойствами или с помощью `protected` методов доступа к свойствам.</span><span class="sxs-lookup"><span data-stu-id="0af5a-224">Fields should always be `private`, with `public` or `protected` property accessors.</span></span>

- <span data-ttu-id="0af5a-225">По возможности используйте [элементы Expression-воплощающего](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) и [автоматические свойства](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) .</span><span class="sxs-lookup"><span data-stu-id="0af5a-225">Use [expression-bodied members](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) and [auto properties](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) where possible</span></span>

#### <a name="dont"></a><span data-ttu-id="0af5a-226">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-226">Don't</span></span>

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a><span data-ttu-id="0af5a-227">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-227">Do</span></span>

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a><span data-ttu-id="0af5a-228">Использовать фигурные скобки</span><span class="sxs-lookup"><span data-stu-id="0af5a-228">Use braces</span></span>

<span data-ttu-id="0af5a-229">Всегда используйте фигурные скобки после каждого блока операторов и поместите их на следующую строку.</span><span class="sxs-lookup"><span data-stu-id="0af5a-229">Always use braces after each statement block, and place them on the next line.</span></span>

#### <a name="dont"></a><span data-ttu-id="0af5a-230">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-230">Don't</span></span>

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a><span data-ttu-id="0af5a-231">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-231">Don't</span></span>

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a><span data-ttu-id="0af5a-232">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-232">Do</span></span>

```c#
private Foo()
{
    if (Bar==true)
    {
        DoThing();
    }
    else
    {
        DoTheOtherThing();
    }
}
```

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a><span data-ttu-id="0af5a-233">Открытые классы, структуры и перечисления должны поступать в свои файлы</span><span class="sxs-lookup"><span data-stu-id="0af5a-233">Public classes, structs, and enums should all go in their own files</span></span>

<span data-ttu-id="0af5a-234">Если класс, структура или перечисление могут быть сделаны частными, то их можно добавить в один и тот же файл.</span><span class="sxs-lookup"><span data-stu-id="0af5a-234">If the class, struct, or enum can be made private then it's okay to be included in the same file.</span></span>  <span data-ttu-id="0af5a-235">Это позволяет избежать проблем с компиляцией с Unity и обеспечить правильную абстракцию кода, а также снизить вероятность конфликтов и критических изменений, когда необходимо изменить код.</span><span class="sxs-lookup"><span data-stu-id="0af5a-235">This avoids compilations issues with Unity and ensure that proper code abstraction occurs, it also reduces conflicts and breaking changes when code needs to change.</span></span>

#### <a name="dont"></a><span data-ttu-id="0af5a-236">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-236">Don't</span></span>

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="0af5a-237">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-237">Do</span></span>

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="0af5a-238">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-238">Do</span></span>

<span data-ttu-id="0af5a-239">MyStruct. CS</span><span class="sxs-lookup"><span data-stu-id="0af5a-239">MyStruct.cs</span></span>

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

<span data-ttu-id="0af5a-240">Менумтипе. CS</span><span class="sxs-lookup"><span data-stu-id="0af5a-240">MyEnumType.cs</span></span>

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

<span data-ttu-id="0af5a-241">MyClass. CS</span><span class="sxs-lookup"><span data-stu-id="0af5a-241">MyClass.cs</span></span>

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a><span data-ttu-id="0af5a-242">Инициализация перечислений</span><span class="sxs-lookup"><span data-stu-id="0af5a-242">Initialize enums</span></span>

<span data-ttu-id="0af5a-243">Чтобы убедиться, что все перечисления инициализированы правильно, начиная с 0, .NET предоставляет сокращенное сочетание клавиш для автоматической инициализации перечисления путем добавления первого (начального) значения.</span><span class="sxs-lookup"><span data-stu-id="0af5a-243">To ensure all enums are initialized correctly starting at 0, .NET gives you a tidy shortcut to automatically initialize the enum by just adding the first (starter) value.</span></span> <span data-ttu-id="0af5a-244">(например, значение 1 = 0 оставшиеся значения не требуются)</span><span class="sxs-lookup"><span data-stu-id="0af5a-244">(e.g Value 1 = 0 Remaining values are not required)</span></span>

#### <a name="dont"></a><span data-ttu-id="0af5a-245">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-245">Don't</span></span>

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a><span data-ttu-id="0af5a-246">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-246">Do</span></span>

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a><span data-ttu-id="0af5a-247">Упорядочение перечислений для соответствующего расширения</span><span class="sxs-lookup"><span data-stu-id="0af5a-247">Order enums for appropriate extension</span></span>

<span data-ttu-id="0af5a-248">Очень важно, что если перечисление, скорее всего, будет расширено в будущем, чтобы упорядочить значения по умолчанию в верхней части перечисления, это гарантирует, что новые дополнения не затрагивают индексы перечисления.</span><span class="sxs-lookup"><span data-stu-id="0af5a-248">It is critical that if an Enum is likely to be extended in the future, to order defaults at the top of the Enum, this ensures Enum indexes are not affected with new additions.</span></span>

#### <a name="dont"></a><span data-ttu-id="0af5a-249">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-249">Don't</span></span>

```c#
public enum SDKType
{
    WindowsMR,
    OpenVR,
    OpenXR,
    None, <- default value not at start
    Other <- anonymous value left to end of enum
}
```

#### <a name="do"></a><span data-ttu-id="0af5a-250">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-250">Do</span></span>

```c#
/// <summary>
/// The SDKType lists the VR SDKs that are supported by the MRTK
/// Initially, this lists proposed SDKs, not all may be implemented at this time (please see ReleaseNotes for more details)
/// </summary>
public enum SDKType
{
    /// <summary>
    /// No specified type or Standalone / non-VR type
    /// </summary>
    None = 0,
    /// <summary>
    /// Undefined SDK.
    /// </summary>
    Other,
    /// <summary>
    /// The Windows 10 Mixed reality SDK provided by the Universal Windows Platform (UWP), for Immersive MR headsets and HoloLens.
    /// </summary>
    WindowsMR,
    /// <summary>
    /// The OpenVR platform provided by Unity (does not support the downloadable SteamVR SDK).
    /// </summary>
    OpenVR,
    /// <summary>
    /// The OpenXR platform. SDK to be determined once released.
    /// </summary>
    OpenXR
}
```

### <a name="review-enum-use-for-bitfields"></a><span data-ttu-id="0af5a-251">Проверка использования перечисления для битовых полей</span><span class="sxs-lookup"><span data-stu-id="0af5a-251">Review enum use for bitfields</span></span>

<span data-ttu-id="0af5a-252">Если существует возможность, чтобы перечисление требовало несколько состояний в качестве значения, например правой или левой = Left & right.</span><span class="sxs-lookup"><span data-stu-id="0af5a-252">If there is a possibility for an enum to require multiple states as a value, e.g. Handedness = Left & Right.</span></span> <span data-ttu-id="0af5a-253">Затем необходимо правильно настроить перечисление с помощью Битфлагс, чтобы его можно было использовать правильно.</span><span class="sxs-lookup"><span data-stu-id="0af5a-253">Then the Enum needs to be decorated correctly with BitFlags to enable it to be used correctly</span></span>

<span data-ttu-id="0af5a-254">Файл правой или левой. CS имеет конкретную реализацию для этого</span><span class="sxs-lookup"><span data-stu-id="0af5a-254">The Handedness.cs file has a concrete implementation for this</span></span>

### <a name="dont"></a><span data-ttu-id="0af5a-255">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-255">Don't</span></span>

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a><span data-ttu-id="0af5a-256">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-256">Do</span></span>

```c#
[Flags]
public enum Handedness
{
    None = 0 << 0,
    Left = 1 << 0,
    Right = 1 << 1,
    Both = Left | Right
}
```

### <a name="hard-coded-file-paths"></a><span data-ttu-id="0af5a-257">Жестко запрограммированные пути к файлам</span><span class="sxs-lookup"><span data-stu-id="0af5a-257">Hard-coded file paths</span></span>

<span data-ttu-id="0af5a-258">При создании путей к файловым строкам и, в частности, при записи жестко запрограммированных строковых путей, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="0af5a-258">When generating string file paths, and in particular writing hard-coded string paths, do the following:</span></span>

1. <span data-ttu-id="0af5a-259">Используйте API- [ `Path` интерфейсы](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) C# везде, где это возможно, например `Path.Combine` или `Path.GetFullPath` .</span><span class="sxs-lookup"><span data-stu-id="0af5a-259">Use C#'s [`Path` APIs](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) whenever possible such as `Path.Combine` or `Path.GetFullPath`.</span></span>
1. <span data-ttu-id="0af5a-260">Используйте/или [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) вместо \ или \\ \\ .</span><span class="sxs-lookup"><span data-stu-id="0af5a-260">Use / or [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) instead of \ or \\\\.</span></span>

<span data-ttu-id="0af5a-261">Эти действия гарантируют, что МРТК работает в системах на базе Windows и UNIX.</span><span class="sxs-lookup"><span data-stu-id="0af5a-261">These steps ensure that MRTK works on both Windows and Unix-based systems.</span></span>

### <a name="dont"></a><span data-ttu-id="0af5a-262">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-262">Don't</span></span>

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a><span data-ttu-id="0af5a-263">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-263">Do</span></span>

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a><span data-ttu-id="0af5a-264">Рекомендации, включая рекомендации Unity</span><span class="sxs-lookup"><span data-stu-id="0af5a-264">Best practices, including Unity recommendations</span></span>

<span data-ttu-id="0af5a-265">Для некоторых целевых платформ этого проекта необходимо учитывать производительность.</span><span class="sxs-lookup"><span data-stu-id="0af5a-265">Some of the target platforms of this project require to take performance into consideration.</span></span> <span data-ttu-id="0af5a-266">Учитывая это, всегда будьте внимательны при выделении памяти в часто именуемом коде в тесном цикле обновления или алгоритмах.</span><span class="sxs-lookup"><span data-stu-id="0af5a-266">With this in mind always be careful when allocating memory in frequently called code in tight update loops or algorithms.</span></span>

### <a name="encapsulation"></a><span data-ttu-id="0af5a-267">Инкапсуляция</span><span class="sxs-lookup"><span data-stu-id="0af5a-267">Encapsulation</span></span>

<span data-ttu-id="0af5a-268">Всегда используйте закрытые поля и открытые свойства, если доступ к полю требуется извне класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="0af5a-268">Always use private fields and public properties if access to the field is needed from outside the class or struct.</span></span>  <span data-ttu-id="0af5a-269">Не забудьте разместить закрытое поле и открытое свойство.</span><span class="sxs-lookup"><span data-stu-id="0af5a-269">Be sure to co-locate the private field and the public property.</span></span> <span data-ttu-id="0af5a-270">Это упрощает наглядное представление, что обеспечивает обратную передачу свойства и поля, изменяемые сценарием.</span><span class="sxs-lookup"><span data-stu-id="0af5a-270">This makes it easier to see, at a glance, what backs the property and that the field is modifiable by script.</span></span>

> [!NOTE]
> <span data-ttu-id="0af5a-271">Единственным исключением из этого является структура данных, для которой требуется сериализация полей в `JsonUtility` , где класс данных должен иметь все открытые поля для работы сериализации.</span><span class="sxs-lookup"><span data-stu-id="0af5a-271">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`, where a data class is required to have all public fields for the serialization to work.</span></span>

#### <a name="dont"></a><span data-ttu-id="0af5a-272">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-272">Don't</span></span>

```c#
private float myValue1;
private float myValue2;

public float MyValue1
{
    get{ return myValue1; }
    set{ myValue1 = value }
}

public float MyValue2
{
    get{ return myValue2; }
    set{ myValue2 = value }
}
```

#### <a name="do"></a><span data-ttu-id="0af5a-273">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-273">Do</span></span>

```c#
// Enable field to be configurable in the editor and available externally to other scripts (field is correctly serialized in Unity)
[SerializeField]
[ToolTip("If using a tooltip, the text should match the public property's summary documentation, if appropriate.")]
private float myValue; // <- Notice we co-located the backing field above our corresponding property.

/// <summary>
/// If using a tooltip, the text should match the public property's summary documentation, if appropriate.
/// </summary>
public float MyValue
{
    get => myValue;
    set => myValue = value;
}

/// <summary>
/// Getter/Setters not wrapping a value directly should contain documentation comments just as public functions would
/// </summary>
public float AbsMyValue
{
    get
    {
        if (MyValue < 0)
        {
            return -MyValue;
        }

        return MyValue
    }
}
```

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a><span data-ttu-id="0af5a-274">Значения кэша и сериализуются их в сцене или prefab, когда это возможно</span><span class="sxs-lookup"><span data-stu-id="0af5a-274">Cache values and serialize them in the scene/prefab whenever possible</span></span>

<span data-ttu-id="0af5a-275">С учетом HoloLens лучше оптимизировать для производительности и ссылок на кэш в сцене или prefab, чтобы ограничить выделение памяти во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0af5a-275">With the HoloLens in mind, it's best to optimize for performance and cache references in the scene or prefab to limit runtime memory allocations.</span></span>

#### <a name="dont"></a><span data-ttu-id="0af5a-276">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-276">Don't</span></span>

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a><span data-ttu-id="0af5a-277">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-277">Do</span></span>

```c#
[SerializeField] // To enable setting the reference in the inspector.
private Renderer myRenderer;

private void Awake()
{
    // If you didn't set it in the inspector, then we cache it on awake.
    if (myRenderer == null)
    {
        myRenderer = gameObject.GetComponent<Renderer>();
    }
}

private void Update()
{
    myRenderer.Foo(Bar);
}
```

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a><span data-ttu-id="0af5a-278">Кэшировать ссылки на материалы, не вызывайте ". Material" каждый раз</span><span class="sxs-lookup"><span data-stu-id="0af5a-278">Cache references to materials, do not call the ".material" each time</span></span>

<span data-ttu-id="0af5a-279">Unity создаст новый материал каждый раз при использовании ". Material", что приведет к утечке памяти при неправильной очистке.</span><span class="sxs-lookup"><span data-stu-id="0af5a-279">Unity will create a new material each time you use ".material", which will cause a memory leak if not cleaned up properly.</span></span>

#### <a name="dont"></a><span data-ttu-id="0af5a-280">Не рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-280">Don't</span></span>

```c#
public class MyClass
{
    void Update()
    {
        Material myMaterial = GetComponent<Renderer>().material;
        myMaterial.SetColor("_Color", Color.White);
    }
}
```

#### <a name="do"></a><span data-ttu-id="0af5a-281">Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="0af5a-281">Do</span></span>

```c#
// Private references for use inside the class only
public class MyClass
{
    private Material cachedMaterial;

    private void Awake()
    {
        cachedMaterial = GetComponent<Renderer>().material;
    }

    void Update()
    {
        cachedMaterial.SetColor("_Color", Color.White);
    }

    private void OnDestroy()
    {
        Destroy(cachedMaterial);
    }
}
```

> [!NOTE]
> <span data-ttu-id="0af5a-282">Кроме того, можно использовать свойство "Шаредматериал" Unity, которое не создает новый материал при каждом обращении.</span><span class="sxs-lookup"><span data-stu-id="0af5a-282">Alternatively, use Unity's "SharedMaterial" property which does not create a new material each time it is referenced.</span></span>

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a><span data-ttu-id="0af5a-283">Используйте [зависимую от платформы компиляцию](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) , чтобы убедиться, что набор средств не нарушает сборку на другой платформе</span><span class="sxs-lookup"><span data-stu-id="0af5a-283">Use [platform dependent compilation](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) to ensure the Toolkit won't break the build on another platform</span></span>

- <span data-ttu-id="0af5a-284">Используйте `WINDOWS_UWP` для использования интерфейсов API, относящихся к UWP, не относящимся к Unity.</span><span class="sxs-lookup"><span data-stu-id="0af5a-284">Use `WINDOWS_UWP` in order to use UWP-specific, non-Unity APIs.</span></span> <span data-ttu-id="0af5a-285">Это предотвратит попытку запуска в редакторе или на неподдерживаемых платформах.</span><span class="sxs-lookup"><span data-stu-id="0af5a-285">This will prevent them from trying to run in the Editor or on unsupported platforms.</span></span> <span data-ttu-id="0af5a-286">Это эквивалентно `UNITY_WSA && !UNITY_EDITOR` и должно использоваться в пользу.</span><span class="sxs-lookup"><span data-stu-id="0af5a-286">This is equivalent to `UNITY_WSA && !UNITY_EDITOR` and should be used in favor of.</span></span>
- <span data-ttu-id="0af5a-287">Используйте `UNITY_WSA` для использования интерфейсов API Unity, зависящих от UWP, таких как `UnityEngine.XR.WSA` пространство имен.</span><span class="sxs-lookup"><span data-stu-id="0af5a-287">Use `UNITY_WSA` to use UWP-specific Unity APIs, such as the `UnityEngine.XR.WSA` namespace.</span></span> <span data-ttu-id="0af5a-288">Это будет выполняться в редакторе, если платформа имеет значение UWP, а также в созданных приложениях UWP.</span><span class="sxs-lookup"><span data-stu-id="0af5a-288">This will run in the Editor when the platform is set to UWP, as well as in built UWP apps.</span></span>

<span data-ttu-id="0af5a-289">Эта диаграмма поможет вам выбрать нужный `#if` вариант в зависимости от ваших вариантов использования и ожидаемых параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="0af5a-289">This chart can help you decide which `#if` to use, depending on your use cases and the build settings you expect.</span></span>

|<span data-ttu-id="0af5a-290">Платформа</span><span class="sxs-lookup"><span data-stu-id="0af5a-290">Platform</span></span> | <span data-ttu-id="0af5a-291">IL2CPP UWP</span><span class="sxs-lookup"><span data-stu-id="0af5a-291">UWP IL2CPP</span></span> | <span data-ttu-id="0af5a-292">UWP .NET</span><span class="sxs-lookup"><span data-stu-id="0af5a-292">UWP .NET</span></span> | <span data-ttu-id="0af5a-293">Редактор</span><span class="sxs-lookup"><span data-stu-id="0af5a-293">Editor</span></span> |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | <span data-ttu-id="0af5a-294">False</span><span class="sxs-lookup"><span data-stu-id="0af5a-294">False</span></span> | <span data-ttu-id="0af5a-295">False</span><span class="sxs-lookup"><span data-stu-id="0af5a-295">False</span></span> | <span data-ttu-id="0af5a-296">True</span><span class="sxs-lookup"><span data-stu-id="0af5a-296">True</span></span> |
| `UNITY_WSA` | <span data-ttu-id="0af5a-297">True</span><span class="sxs-lookup"><span data-stu-id="0af5a-297">True</span></span> | <span data-ttu-id="0af5a-298">True</span><span class="sxs-lookup"><span data-stu-id="0af5a-298">True</span></span> | <span data-ttu-id="0af5a-299">True</span><span class="sxs-lookup"><span data-stu-id="0af5a-299">True</span></span> |
| `WINDOWS_UWP` | <span data-ttu-id="0af5a-300">True</span><span class="sxs-lookup"><span data-stu-id="0af5a-300">True</span></span> | <span data-ttu-id="0af5a-301">True</span><span class="sxs-lookup"><span data-stu-id="0af5a-301">True</span></span> | <span data-ttu-id="0af5a-302">False</span><span class="sxs-lookup"><span data-stu-id="0af5a-302">False</span></span> |
| `UNITY_WSA && !UNITY_EDITOR` | <span data-ttu-id="0af5a-303">True</span><span class="sxs-lookup"><span data-stu-id="0af5a-303">True</span></span> | <span data-ttu-id="0af5a-304">True</span><span class="sxs-lookup"><span data-stu-id="0af5a-304">True</span></span> | <span data-ttu-id="0af5a-305">False</span><span class="sxs-lookup"><span data-stu-id="0af5a-305">False</span></span> |
| `ENABLE_WINMD_SUPPORT` | <span data-ttu-id="0af5a-306">True</span><span class="sxs-lookup"><span data-stu-id="0af5a-306">True</span></span> | <span data-ttu-id="0af5a-307">True</span><span class="sxs-lookup"><span data-stu-id="0af5a-307">True</span></span> | <span data-ttu-id="0af5a-308">False</span><span class="sxs-lookup"><span data-stu-id="0af5a-308">False</span></span> |
| `NETFX_CORE` | <span data-ttu-id="0af5a-309">False</span><span class="sxs-lookup"><span data-stu-id="0af5a-309">False</span></span> | <span data-ttu-id="0af5a-310">True</span><span class="sxs-lookup"><span data-stu-id="0af5a-310">True</span></span> | <span data-ttu-id="0af5a-311">False</span><span class="sxs-lookup"><span data-stu-id="0af5a-311">False</span></span> |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a><span data-ttu-id="0af5a-312">Предпочитать DateTime. UtcNow через DateTime. Now</span><span class="sxs-lookup"><span data-stu-id="0af5a-312">Prefer DateTime.UtcNow over DateTime.Now</span></span>

<span data-ttu-id="0af5a-313">DateTime. UtcNow работает быстрее, чем DateTime. Now.</span><span class="sxs-lookup"><span data-stu-id="0af5a-313">DateTime.UtcNow is faster than DateTime.Now.</span></span> <span data-ttu-id="0af5a-314">В предыдущем исследовании производительности мы обнаружили, что использование DateTime. теперь добавляет значительные издержки, особенно при использовании в цикле Update ().</span><span class="sxs-lookup"><span data-stu-id="0af5a-314">In previous performance investigations we've found that using DateTime.Now adds significant overhead especially when used in the Update() loop.</span></span> <span data-ttu-id="0af5a-315">[Другие пользователи столкнулись с той же проблемой](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).</span><span class="sxs-lookup"><span data-stu-id="0af5a-315">[Others have hit the same issue](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).</span></span>

<span data-ttu-id="0af5a-316">Предпочитать использование DateTime. UtcNow, если вам действительно не требуется локализованное время (по законным причинам может потребоваться отобразить текущее время в часовом поясе пользователя).</span><span class="sxs-lookup"><span data-stu-id="0af5a-316">Prefer using DateTime.UtcNow unless you actually need the localized times (a legitimate reason may be you wanting to show the current time in the user's time zone).</span></span> <span data-ttu-id="0af5a-317">Если вы работаете с относительным временем (т. е. разностью между последним обновлением и сейчас), лучше использовать DateTime. UtcNow, чтобы избежать издержек, связанных с преобразованиями часовых поясов.</span><span class="sxs-lookup"><span data-stu-id="0af5a-317">If you are dealing with relative times (i.e. the delta between some last update and now), it's best to use DateTime.UtcNow to avoid the overhead of doing timezone conversions.</span></span>

## <a name="powershell-coding-conventions"></a><span data-ttu-id="0af5a-318">Соглашения о написании кода PowerShell</span><span class="sxs-lookup"><span data-stu-id="0af5a-318">PowerShell coding conventions</span></span>

<span data-ttu-id="0af5a-319">Подмножество базы кода МРТК использует PowerShell для инфраструктуры конвейера и различных сценариев и служебных программ.</span><span class="sxs-lookup"><span data-stu-id="0af5a-319">A subset of the MRTK codebase uses PowerShell for pipeline infrastructure and various scripts and utilities.</span></span> <span data-ttu-id="0af5a-320">Новый код PowerShell должен соответствовать [стилю пошкоде](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span><span class="sxs-lookup"><span data-stu-id="0af5a-320">New PowerShell code should follow the [PoshCode style](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span></span>

## <a name="see-also"></a><span data-ttu-id="0af5a-321">См. также</span><span class="sxs-lookup"><span data-stu-id="0af5a-321">See also</span></span>

 [<span data-ttu-id="0af5a-322">Соглашения о написании кода на C# из MSDN</span><span class="sxs-lookup"><span data-stu-id="0af5a-322">C# coding conventions from MSDN</span></span>](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)