---
title: Справка по документации
description: руководства и стандарты документации для МРТК.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 37233141bd43f27db47935574bac7630b8bea8d7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121392"
---
# <a name="documentation-guidelines"></a><span data-ttu-id="12c4b-104">Руководства по документации</span><span class="sxs-lookup"><span data-stu-id="12c4b-104">Documentation guidelines</span></span>

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

<span data-ttu-id="12c4b-105">В этом документе описываются руководства и стандарты документации для набора средств Mixed Reality (МРТК).</span><span class="sxs-lookup"><span data-stu-id="12c4b-105">This document outlines the documentation guidelines and standards for the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="12c4b-106">Это введение в технические аспекты написания и создания документации, выделения распространенных ловушек и описания рекомендуемого стиля записи.</span><span class="sxs-lookup"><span data-stu-id="12c4b-106">This provides an introduction to technical aspects of documentation writing and generation, to highlight common pitfalls, and to describe the recommended writing style.</span></span>

<span data-ttu-id="12c4b-107">Сама страница должна служить примером, поэтому она использует предполагаемый стиль и наиболее распространенные функции разметки документации.</span><span class="sxs-lookup"><span data-stu-id="12c4b-107">The page itself is supposed to serve as an example, therefore it uses the intended style and the most common markup features of the documentation.</span></span>

- [<span data-ttu-id="12c4b-108">Источник</span><span class="sxs-lookup"><span data-stu-id="12c4b-108">Source</span></span>](#source-documentation)
- [<span data-ttu-id="12c4b-109">Практические руководства</span><span class="sxs-lookup"><span data-stu-id="12c4b-109">How-to</span></span>](#how-to-documentation)
- [<span data-ttu-id="12c4b-110">Оформление</span><span class="sxs-lookup"><span data-stu-id="12c4b-110">Design</span></span>](#design-documentation)
- [<span data-ttu-id="12c4b-111">Заметки о производительности</span><span class="sxs-lookup"><span data-stu-id="12c4b-111">Performance notes</span></span>](#performance-notes)
- [<span data-ttu-id="12c4b-112">Критические изменения</span><span class="sxs-lookup"><span data-stu-id="12c4b-112">Breaking changes</span></span>](#breaking-changes)

---

## <a name="functionality-and-markup"></a><span data-ttu-id="12c4b-113">Функциональность и разметка</span><span class="sxs-lookup"><span data-stu-id="12c4b-113">Functionality and markup</span></span>

<span data-ttu-id="12c4b-114">В этом разделе описываются часто требуемые функции.</span><span class="sxs-lookup"><span data-stu-id="12c4b-114">This section describes frequently needed features.</span></span> <span data-ttu-id="12c4b-115">Чтобы увидеть, как они работают, Взгляните на исходный код страницы.</span><span class="sxs-lookup"><span data-stu-id="12c4b-115">To see how they work, look at the source code of the page.</span></span>

1. <span data-ttu-id="12c4b-116">Нумерованные списки</span><span class="sxs-lookup"><span data-stu-id="12c4b-116">Numbered lists</span></span>
   1. <span data-ttu-id="12c4b-117">Вложенные нумерованные списки, содержащие не менее 3 начальных пробелов</span><span class="sxs-lookup"><span data-stu-id="12c4b-117">Nested numbered lists with at least 3 leading blank spaces</span></span>
   1. <span data-ttu-id="12c4b-118">Фактическое число в коде не имеет значения; при синтаксическом анализе будет устанавливаться правильный номер элемента.</span><span class="sxs-lookup"><span data-stu-id="12c4b-118">The actual number in code is irrelevant; parsing will take care of setting the correct item number.</span></span>

- <span data-ttu-id="12c4b-119">Списки точек маркеров</span><span class="sxs-lookup"><span data-stu-id="12c4b-119">Bullet point lists</span></span>
  - <span data-ttu-id="12c4b-120">Вложенные списки точек маркеров</span><span class="sxs-lookup"><span data-stu-id="12c4b-120">Nested bullet point lists</span></span>
- <span data-ttu-id="12c4b-121">**Полужирный** текст с \* \* двойной звездочкой\*\*</span><span class="sxs-lookup"><span data-stu-id="12c4b-121">Text in **bold** with \*\*double asterisk\*\*</span></span>
- <span data-ttu-id="12c4b-122">_курсив_ *с* \_ символом подчеркивания \_ или \* одинарной звездочкой\*</span><span class="sxs-lookup"><span data-stu-id="12c4b-122">_italic_ *text* with \_underscore\_ or \*single asterisk\*</span></span>
- <span data-ttu-id="12c4b-123">Текст `highlighted as code` в предложении, \` использующий кавычки\`</span><span class="sxs-lookup"><span data-stu-id="12c4b-123">Text `highlighted as code` within a sentence \`using backquotes\`</span></span>
- <span data-ttu-id="12c4b-124">Ссылки на страницы [документации мртк рекомендации](documentation-guide.md)</span><span class="sxs-lookup"><span data-stu-id="12c4b-124">Links to docs pages [MRTK documentation guidelines](documentation-guide.md)</span></span>
- <span data-ttu-id="12c4b-125">Ссылки на [привязки в пределах страницы](#style); привязки формируются путем замены пробелов дефисами и преобразования в нижний регистр.</span><span class="sxs-lookup"><span data-stu-id="12c4b-125">Links to [anchors within a page](#style); anchors are formed by replacing spaces with dashes, and converting to lowercase</span></span>

<span data-ttu-id="12c4b-126">Для примеров кода мы используем блоки с тремя обратными кавычками \` \` \` и указываем *CSharp* в качестве языка для выделения синтаксиса:</span><span class="sxs-lookup"><span data-stu-id="12c4b-126">For code samples we use the blocks with three backticks \`\`\` and specify *csharp* as the language for syntax highlighting:</span></span>

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

<span data-ttu-id="12c4b-127">При упоминании кода в предложении `use a single backtick` .</span><span class="sxs-lookup"><span data-stu-id="12c4b-127">When mentioning code within a sentence `use a single backtick`.</span></span>

### <a name="todos"></a><span data-ttu-id="12c4b-128">Дел</span><span class="sxs-lookup"><span data-stu-id="12c4b-128">TODOs</span></span>

<span data-ttu-id="12c4b-129">Старайтесь не использовать TODO в документах, как и в случае с этими задачами (например, с кодом TODO), как правило, собирает сведения о том, как они должны быть обновлены и почему теряются.</span><span class="sxs-lookup"><span data-stu-id="12c4b-129">Avoid using TODOs in docs, as over time these TODOs (like code TODOs) tend to accumulate and information about how they should be updated and why gets lost.</span></span>

<span data-ttu-id="12c4b-130">Если необходимо добавить TODO, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="12c4b-130">If it is absolutely necessary to add a TODO, follow these steps:</span></span>

1. <span data-ttu-id="12c4b-131">Создайте новую ошибку в GitHub, описывающую контекст, который следует за TODO, и предоставьте достаточный фон, который может понять другой участник, а затем решить задачу.</span><span class="sxs-lookup"><span data-stu-id="12c4b-131">File a new issue on Github describing the context behind the TODO, and provide enough background that another contributor would be able to understand and then address the TODO.</span></span>
2. <span data-ttu-id="12c4b-132">Ссылка на URL-адрес проблемы в TODO в документации.</span><span class="sxs-lookup"><span data-stu-id="12c4b-132">Reference the issue URL in the todo in the docs.</span></span>

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a><span data-ttu-id="12c4b-133">Выделенные разделы</span><span class="sxs-lookup"><span data-stu-id="12c4b-133">Highlighted sections</span></span>

<span data-ttu-id="12c4b-134">Чтобы выделить определенные точки для читателя, используйте *> [!NOTE]* , *> [!WARNING]* и *> [!IMPORTANT]* для создания следующих стилей.</span><span class="sxs-lookup"><span data-stu-id="12c4b-134">To highlight specific points to the reader, use *> [!NOTE]* , *> [!WARNING]* , and *> [!IMPORTANT]* to produce the following styles.</span></span> <span data-ttu-id="12c4b-135">Рекомендуется использовать заметки для общих точек и предупреждений/важных точек только для специальных важных вариантов.</span><span class="sxs-lookup"><span data-stu-id="12c4b-135">It is recommended to use notes for general points and warning/important points only for special relevant cases.</span></span>

> [!NOTE]
> <span data-ttu-id="12c4b-136">Пример заметки</span><span class="sxs-lookup"><span data-stu-id="12c4b-136">Example of a note</span></span>

> [!WARNING]
> <span data-ttu-id="12c4b-137">Пример предупреждения</span><span class="sxs-lookup"><span data-stu-id="12c4b-137">Example of a warning</span></span>

> [!IMPORTANT]
> <span data-ttu-id="12c4b-138">Пример важного комментария</span><span class="sxs-lookup"><span data-stu-id="12c4b-138">Example of an important comment</span></span>

## <a name="page-layout"></a><span data-ttu-id="12c4b-139">Макет страницы</span><span class="sxs-lookup"><span data-stu-id="12c4b-139">Page layout</span></span>

### <a name="introduction"></a><span data-ttu-id="12c4b-140">Введение</span><span class="sxs-lookup"><span data-stu-id="12c4b-140">Introduction</span></span>

<span data-ttu-id="12c4b-141">Эта часть сразу после основного заголовка главы будет служить кратким введением в главу.</span><span class="sxs-lookup"><span data-stu-id="12c4b-141">The part right after the main chapter title should serve as a short introduction what the chapter is about.</span></span> <span data-ttu-id="12c4b-142">Не делайте этого слишком длинным, вместо этого добавляйте субтитры.</span><span class="sxs-lookup"><span data-stu-id="12c4b-142">Do not make this too long, instead add sub headlines.</span></span> <span data-ttu-id="12c4b-143">Они позволяют ссылаться на разделы и сохранять их в виде закладок.</span><span class="sxs-lookup"><span data-stu-id="12c4b-143">These allow to link to sections and can be saved as bookmarks.</span></span>

### <a name="main-body"></a><span data-ttu-id="12c4b-144">Основной текст</span><span class="sxs-lookup"><span data-stu-id="12c4b-144">Main body</span></span>

<span data-ttu-id="12c4b-145">Используйте заголовки двух и трех уровней для структурирования остальных.</span><span class="sxs-lookup"><span data-stu-id="12c4b-145">Use two-level and three-level headlines to structure the rest.</span></span>

<span data-ttu-id="12c4b-146">**Мини-разделы**</span><span class="sxs-lookup"><span data-stu-id="12c4b-146">**Mini Sections**</span></span>

<span data-ttu-id="12c4b-147">Используйте жирную строку текста для блоков, которые должны быть изолированы. В какой-то момент мы можем заменить эти заголовки на четыре уровня.</span><span class="sxs-lookup"><span data-stu-id="12c4b-147">Use a bold line of text for blocks that should stand out. We might replace this by four-level headlines at some point.</span></span>

### <a name="see-also-section"></a><span data-ttu-id="12c4b-148">Раздел "см. также"</span><span class="sxs-lookup"><span data-stu-id="12c4b-148">'See also' section</span></span>

<span data-ttu-id="12c4b-149">Большинство страниц должно заканчиваться главой с именем *см. также*.</span><span class="sxs-lookup"><span data-stu-id="12c4b-149">Most pages should end with a chapter called *See also*.</span></span> <span data-ttu-id="12c4b-150">Эта глава представляет собой список ссылок на страницы, относящиеся к этому разделу.</span><span class="sxs-lookup"><span data-stu-id="12c4b-150">This chapter is simply a bullet pointed list of links to pages related to this topic.</span></span> <span data-ttu-id="12c4b-151">Эти ссылки могут также отображаться в тексте страницы там, где это необходимо, но это не является обязательным.</span><span class="sxs-lookup"><span data-stu-id="12c4b-151">These links may also appear within the page text where appropriate, but this is not required.</span></span> <span data-ttu-id="12c4b-152">Аналогичным образом, текст страницы может содержать ссылки на страницы, не связанные с главным разделом, они не должны включаться в список " *см. также* ".</span><span class="sxs-lookup"><span data-stu-id="12c4b-152">Similarly, the page text may contain links to pages that are not related to the main topic, these should not be included in the *See also* list.</span></span> <span data-ttu-id="12c4b-153">См. эту страницу в качестве примера для выбора ссылок, [см. также раздел](#see-also) "".</span><span class="sxs-lookup"><span data-stu-id="12c4b-153">See [this page's ''See also'' chapter](#see-also) as an example for the choice of links.</span></span>

## <a name="table-of-contents-toc"></a><span data-ttu-id="12c4b-154">Оглавление (ОГЛАВЛЕНИе)</span><span class="sxs-lookup"><span data-stu-id="12c4b-154">Table of Contents (TOC)</span></span>

<span data-ttu-id="12c4b-155">Файлы оглавления используются для создания панелей навигации в документации по МРТК github.io.</span><span class="sxs-lookup"><span data-stu-id="12c4b-155">Toc files are used for generating the navigation bars in the MRTK github.io documentation.</span></span>
<span data-ttu-id="12c4b-156">При добавлении нового файла документации убедитесь, что в одном из файлов TOC. yml папки документация есть запись для этого файла.</span><span class="sxs-lookup"><span data-stu-id="12c4b-156">Whenever a new documentation file is added, make sure that there's an entry for that file in one of the toc.yml files of the documentation folder.</span></span> <span data-ttu-id="12c4b-157">В области навигации по документам разработчика будут отображаться только статьи, перечисленные в файлах оглавления. Может существовать файл оглавления для каждой вложенной папки в папке документации, которую можно связать с любым существующим файлом оглавления, чтобы добавить его в качестве подраздела в соответствующую часть навигации.</span><span class="sxs-lookup"><span data-stu-id="12c4b-157">Only articles listed in the toc files will show up in the navigation of the developer docs. There can be a toc file for every subfolder in the documentation folder which can be linked into any existing toc file to add it as a subsection to the corresponding part of the navigation.</span></span>

## <a name="style"></a><span data-ttu-id="12c4b-158">Стиль</span><span class="sxs-lookup"><span data-stu-id="12c4b-158">Style</span></span>

### <a name="writing-style"></a><span data-ttu-id="12c4b-159">Стиль письма</span><span class="sxs-lookup"><span data-stu-id="12c4b-159">Writing style</span></span>

<span data-ttu-id="12c4b-160">Общее правило бегунка: попробуйте использовать **Sound Professional**.</span><span class="sxs-lookup"><span data-stu-id="12c4b-160">General rule of thumb: Try to **sound professional**.</span></span> <span data-ttu-id="12c4b-161">Это обычно означает, что следует избегать «диалогового тона».</span><span class="sxs-lookup"><span data-stu-id="12c4b-161">That usually means to avoid a 'conversational tone'.</span></span> <span data-ttu-id="12c4b-162">Также старайтесь не использовать гиперболический и сенсатионалисм.</span><span class="sxs-lookup"><span data-stu-id="12c4b-162">Also try to avoid hyperbole and sensationalism.</span></span>

1. <span data-ttu-id="12c4b-163">Не пытайтесь (слишком) веселое.</span><span class="sxs-lookup"><span data-stu-id="12c4b-163">Don't try to be (overly) funny.</span></span>
2. <span data-ttu-id="12c4b-164">Никогда не писать "I"</span><span class="sxs-lookup"><span data-stu-id="12c4b-164">Never write 'I'</span></span>
3. <span data-ttu-id="12c4b-165">Избегайте "мы".</span><span class="sxs-lookup"><span data-stu-id="12c4b-165">Avoid 'we'.</span></span> <span data-ttu-id="12c4b-166">Обычно это можно легко заменять, используя вместо этого "МРТК".</span><span class="sxs-lookup"><span data-stu-id="12c4b-166">This can usually be rephrased easily, using 'MRTK' instead.</span></span> <span data-ttu-id="12c4b-167">Пример: "Мы поддерживаем эту функцию"-> "МРТК поддерживает эту функцию" или "поддерживаются следующие функции...".</span><span class="sxs-lookup"><span data-stu-id="12c4b-167">Example: "we support this feature" -> "MRTK supports this feature" or "the following features are supported ...".</span></span>
4. <span data-ttu-id="12c4b-168">Аналогичным образом старайтесь не использовать.</span><span class="sxs-lookup"><span data-stu-id="12c4b-168">Similarly, try to avoid 'you'.</span></span> <span data-ttu-id="12c4b-169">Пример: "благодаря этому простому изменению шейдер станет настраиваемым!"</span><span class="sxs-lookup"><span data-stu-id="12c4b-169">Example: "With this simple change your shader becomes configurable!"</span></span> <span data-ttu-id="12c4b-170">-> "шейдеры могут быть настроены с минимальными усилиями".</span><span class="sxs-lookup"><span data-stu-id="12c4b-170">-> "Shaders can be made configurable with little effort."</span></span>
5. <span data-ttu-id="12c4b-171">Не используйте фразы "сыром".</span><span class="sxs-lookup"><span data-stu-id="12c4b-171">Do not use 'sloppy phrases'.</span></span>
6. <span data-ttu-id="12c4b-172">Старайтесь не подавать никакого звука, поэтому не нужно ничего продавать.</span><span class="sxs-lookup"><span data-stu-id="12c4b-172">Avoid sounding overly excited, we do not need to sell anything.</span></span>
7. <span data-ttu-id="12c4b-173">Аналогичным образом Избегайте чрезмерного существенного.</span><span class="sxs-lookup"><span data-stu-id="12c4b-173">Similarly, avoid being overly dramatic.</span></span> <span data-ttu-id="12c4b-174">Восклицательные знаки редко требуются.</span><span class="sxs-lookup"><span data-stu-id="12c4b-174">Exclamation marks are rarely needed.</span></span>

### <a name="capitalization"></a><span data-ttu-id="12c4b-175">Регистр букв</span><span class="sxs-lookup"><span data-stu-id="12c4b-175">Capitalization</span></span>

- <span data-ttu-id="12c4b-176">Используйте **предложение для заголовков**.</span><span class="sxs-lookup"><span data-stu-id="12c4b-176">Use **Sentence case for headlines**.</span></span> <span data-ttu-id="12c4b-177">Пример.</span><span class="sxs-lookup"><span data-stu-id="12c4b-177">Ie.</span></span> <span data-ttu-id="12c4b-178">делать первые буквы и имена прописными, но не предпринимайте никаких других действий.</span><span class="sxs-lookup"><span data-stu-id="12c4b-178">capitalize the first letter and names, but nothing else.</span></span>
- <span data-ttu-id="12c4b-179">Используйте обычную английскую версию для всех остальных.</span><span class="sxs-lookup"><span data-stu-id="12c4b-179">Use regular English for everything else.</span></span> <span data-ttu-id="12c4b-180">Это означает, что не следует заменять **прописными буквы произвольными словами**, даже если они содержат специальное значение в этом контексте.</span><span class="sxs-lookup"><span data-stu-id="12c4b-180">That means **do not capitalize arbitrary words**, even if they hold a special meaning in that context.</span></span> <span data-ttu-id="12c4b-181">Предпочитать *текст курсивом* для выделения определенных слов [см. ниже](#emphasis-and-highlighting).</span><span class="sxs-lookup"><span data-stu-id="12c4b-181">Prefer *italic text* for highlighting certain words, [see below](#emphasis-and-highlighting).</span></span>
- <span data-ttu-id="12c4b-182">Если ссылка внедрена в предложение (предпочтительный метод), стандартное название главы всегда использует прописные буквы, тем самым нарушая правило отсутствия произвольного капитализации внутри текста.</span><span class="sxs-lookup"><span data-stu-id="12c4b-182">When a link is embedded in a sentence (which is the preferred method), the standard chapter name always uses capital letters, thus breaking the rule of no arbitrary capitalization inside text.</span></span> <span data-ttu-id="12c4b-183">Поэтому для исправления регистра используйте пользовательское имя ссылки.</span><span class="sxs-lookup"><span data-stu-id="12c4b-183">Therefore use a custom link name to fix the capitalization.</span></span> <span data-ttu-id="12c4b-184">Например, ниже приведена ссылка на документацию по [элементу управления Bounds](../features/ux-building-blocks/bounds-control.md) .</span><span class="sxs-lookup"><span data-stu-id="12c4b-184">As an example, here is a link to the [bounds control](../features/ux-building-blocks/bounds-control.md) documentation.</span></span>
- <span data-ttu-id="12c4b-185">Заменяйте прописные имена, например *Unity*.</span><span class="sxs-lookup"><span data-stu-id="12c4b-185">Do capitalize names, such as *Unity*.</span></span>
- <span data-ttu-id="12c4b-186">При написании *редактора Unity* не используйте прописные буквы "редактор".</span><span class="sxs-lookup"><span data-stu-id="12c4b-186">Do NOT capitalize "editor" when writing *Unity editor*.</span></span>

### <a name="emphasis-and-highlighting"></a><span data-ttu-id="12c4b-187">Выделение и выделение</span><span class="sxs-lookup"><span data-stu-id="12c4b-187">Emphasis and highlighting</span></span>

<span data-ttu-id="12c4b-188">Есть два способа подчеркнуть или выделить слова, сделав их полужирным шрифтом или сделав их курсивом.</span><span class="sxs-lookup"><span data-stu-id="12c4b-188">There are two ways to emphasize or highlight words, making them bold or making them italic.</span></span> <span data-ttu-id="12c4b-189">Выделение полужирным шрифтом заключается в том, что **полужирный текст фиксируется** и, следовательно, может быть легко замечен при скимминг фрагмента текста или даже при простом прокрутке страницы.</span><span class="sxs-lookup"><span data-stu-id="12c4b-189">The effect of bold text is that **bold text sticks out** and therefore can easily be noticed while skimming a piece of text or even just scrolling over a page.</span></span> <span data-ttu-id="12c4b-190">Полужирный шрифт прекрасно подходит для выделения фраз, которые следует запомнить.</span><span class="sxs-lookup"><span data-stu-id="12c4b-190">Bold is great to highlight phrases that people should remember.</span></span> <span data-ttu-id="12c4b-191">Однако **полужирный текст редко используется**, так как обычно отвлекает внимание.</span><span class="sxs-lookup"><span data-stu-id="12c4b-191">However, **use bold text rarely**, because it is generally distracting.</span></span>

<span data-ttu-id="12c4b-192">Часто требуется, чтобы группа была логически объединена или выделяющая определенный термин, поскольку имеет специальное значение.</span><span class="sxs-lookup"><span data-stu-id="12c4b-192">Often one wants to either 'group' something that belongs logically together or highlight a specific term, because it has a special meaning.</span></span> <span data-ttu-id="12c4b-193">Такие вещи не нужно выделять из общего текста.</span><span class="sxs-lookup"><span data-stu-id="12c4b-193">Such things do not need to stand out of the overall text.</span></span> <span data-ttu-id="12c4b-194">Используйте курсивный текст в качестве *упрощенного метода* , чтобы выделить что-нибудь.</span><span class="sxs-lookup"><span data-stu-id="12c4b-194">Use italic text as a *lightweight method* to highlight something.</span></span>

<span data-ttu-id="12c4b-195">Аналогично, когда в тексте упоминается имя файла, путь или запись меню, желательно сделать его курсивом, чтобы логически сгруппировать его, не отвлекаясь.</span><span class="sxs-lookup"><span data-stu-id="12c4b-195">Similarly, when a filename, a path or a menu-entry is mentioned in text, prefer to make it italic to logically group it, without being distracting.</span></span>

<span data-ttu-id="12c4b-196">Как правило, старайтесь **избегать ненужных выделений текста**.</span><span class="sxs-lookup"><span data-stu-id="12c4b-196">In general, try to **avoid unnecessary text highlighting**.</span></span> <span data-ttu-id="12c4b-197">Специальные термины можно выделить один раз, чтобы сделать его осведомленным, не повторяйте такое выделение во всем тексте, если оно больше не работает и только отвлекается от него.</span><span class="sxs-lookup"><span data-stu-id="12c4b-197">Special terms can be highlighted once to make the reader aware, do not repeat such highlighting throughout the text, when it serves no purpose anymore and only distracts.</span></span>

### <a name="mentioning-menu-entries"></a><span data-ttu-id="12c4b-198">Упоминание пунктов меню</span><span class="sxs-lookup"><span data-stu-id="12c4b-198">Mentioning menu entries</span></span>

<span data-ttu-id="12c4b-199">При упоминании записи меню, которую должен щелкнуть пользователь, текущее соглашение: *файлы проекта > > создать > конечный* элемент</span><span class="sxs-lookup"><span data-stu-id="12c4b-199">When mentioning a menu entry that a user should click, the current convention is: *Project > Files > Create > Leaf*</span></span>

### <a name="links"></a><span data-ttu-id="12c4b-200">Ссылки</span><span class="sxs-lookup"><span data-stu-id="12c4b-200">Links</span></span>

<span data-ttu-id="12c4b-201">Вставляйте как можно больше полезных ссылок на другие страницы, но только один раз.</span><span class="sxs-lookup"><span data-stu-id="12c4b-201">Insert as many useful links to other pages as possible, but each link only once.</span></span> <span data-ttu-id="12c4b-202">Предположим, что читатель щелкает каждую ссылку на странице и считает, насколько неудобно, если одна и та же страница открывается 20 раз.</span><span class="sxs-lookup"><span data-stu-id="12c4b-202">Assume a reader clicks on every link in the page, and think about how annoying it would be, if the same page opens 20 times.</span></span>

<span data-ttu-id="12c4b-203">Предпочитать ссылки, внедренные в предложение:</span><span class="sxs-lookup"><span data-stu-id="12c4b-203">Prefer links embedded in a sentence:</span></span>

- <span data-ttu-id="12c4b-204">Ошибка: рекомендации полезны.</span><span class="sxs-lookup"><span data-stu-id="12c4b-204">BAD: Guidelines are useful.</span></span> <span data-ttu-id="12c4b-205">Дополнительные сведения см. в [этой главе](../contributing/documentation-guide.md) .</span><span class="sxs-lookup"><span data-stu-id="12c4b-205">See [this chapter](../contributing/documentation-guide.md) for details.</span></span>
- <span data-ttu-id="12c4b-206">ХОРОШЕЕ: [рекомендации](documentation-guide.md) полезны.</span><span class="sxs-lookup"><span data-stu-id="12c4b-206">GOOD: [Guidelines](documentation-guide.md) are useful.</span></span>

<span data-ttu-id="12c4b-207">Избегайте внешних ссылок, они могут устареть или содержать содержимое с авторскими правами.</span><span class="sxs-lookup"><span data-stu-id="12c4b-207">Avoid external links, they can become outdated or contain copyrighted content.</span></span>

<span data-ttu-id="12c4b-208">При добавлении ссылки определите, следует ли также добавить ее в список в разделе " [см. также](#see-also) ".</span><span class="sxs-lookup"><span data-stu-id="12c4b-208">When adding a link, consider whether it should also be listed in the [See also](#see-also) section.</span></span> <span data-ttu-id="12c4b-209">Аналогичным образом проверьте, следует ли добавить ссылку на новую страницу в связанную страницу.</span><span class="sxs-lookup"><span data-stu-id="12c4b-209">Similarly, check whether a link to the new page should be added to the linked-to page.</span></span>

### <a name="images--screenshots"></a><span data-ttu-id="12c4b-210">Изображения и снимки экрана</span><span class="sxs-lookup"><span data-stu-id="12c4b-210">Images / screenshots</span></span>

<span data-ttu-id="12c4b-211">**Используйте снимки экрана с осторожностью.**</span><span class="sxs-lookup"><span data-stu-id="12c4b-211">**Use screenshots sparingly.**</span></span> <span data-ttu-id="12c4b-212">Обслуживание образов в документации является большим объемом работы, но небольшие изменения пользовательского интерфейса могут привести к небольшому количеству снимков экрана.</span><span class="sxs-lookup"><span data-stu-id="12c4b-212">Maintaining images in documentation is a lot of work, small UI changes can make a lot of screenshots outdated.</span></span> <span data-ttu-id="12c4b-213">Следующие правила снижают затраты на обслуживание:</span><span class="sxs-lookup"><span data-stu-id="12c4b-213">The following rules will reduce maintenance effort:</span></span>

1. <span data-ttu-id="12c4b-214">Не используйте снимки экрана для тех вещей, которые можно описать в тексте.</span><span class="sxs-lookup"><span data-stu-id="12c4b-214">Do not use screenshots for things that can be described in text.</span></span> <span data-ttu-id="12c4b-215">В частности, **никогда не следует отображать сетку свойств** с целью отображения имен и значений свойств.</span><span class="sxs-lookup"><span data-stu-id="12c4b-215">Especially, **never screenshot a property grid** for the sole purpose of showing property names and values.</span></span>
2. <span data-ttu-id="12c4b-216">Не включайте в снимок экрана элементы, которые не нужны для отображения.</span><span class="sxs-lookup"><span data-stu-id="12c4b-216">Do not include things in a screenshot that are irrelevant to what is shown.</span></span> <span data-ttu-id="12c4b-217">Например, когда отображается результат отрисовки, сделайте снимок экрана окна просмотра, но исключите для него пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="12c4b-217">For instance, when a rendering effect is shown, make a screenshot of the viewport, but exclude any UI around it.</span></span> <span data-ttu-id="12c4b-218">Отображение пользовательского интерфейса. Попробуйте переместить окна таким образом, чтобы в изображении был только этот важный компонент.</span><span class="sxs-lookup"><span data-stu-id="12c4b-218">Showing some UI, try to move windows around such that only that important part is in the image.</span></span>
3. <span data-ttu-id="12c4b-219">При включении пользовательского интерфейса снимка экрана отображаются только важные части.</span><span class="sxs-lookup"><span data-stu-id="12c4b-219">When including screenshot UI, only show the important parts.</span></span> <span data-ttu-id="12c4b-220">Например, если речь идет о кнопках на панели инструментов, создайте небольшое изображение, отображающее важные кнопки на панели инструментов, но исключите все вокруг нее.</span><span class="sxs-lookup"><span data-stu-id="12c4b-220">For example, when talking about buttons in a toolbar, make a small image that shows the important toolbar buttons, but exclude everything around it.</span></span>
4. <span data-ttu-id="12c4b-221">Используйте только те образы, которые легко воспроизвести.</span><span class="sxs-lookup"><span data-stu-id="12c4b-221">Only use images that are easy to reproduce.</span></span> <span data-ttu-id="12c4b-222">Это означает, что не следует рисовать маркеры или выделения на снимках экрана.</span><span class="sxs-lookup"><span data-stu-id="12c4b-222">That means do not paint markers or highlights into screenshots.</span></span> <span data-ttu-id="12c4b-223">Во – первых, не существует правил, определяющих, как они должны выглядеть.</span><span class="sxs-lookup"><span data-stu-id="12c4b-223">First, there are no consistent rules how these should look, anyway.</span></span> <span data-ttu-id="12c4b-224">Во-вторых, воссоздание такого снимка экрана является дополнительными усилиями.</span><span class="sxs-lookup"><span data-stu-id="12c4b-224">Second, reproducing such a screenshot is additional effort.</span></span> <span data-ttu-id="12c4b-225">Вместо этого Опишите важные части в тексте.</span><span class="sxs-lookup"><span data-stu-id="12c4b-225">Instead, describe the important parts in text.</span></span> <span data-ttu-id="12c4b-226">Существуют исключения из этого правила, но они редки.</span><span class="sxs-lookup"><span data-stu-id="12c4b-226">There are exceptions to this rule, but they are rare.</span></span>
5. <span data-ttu-id="12c4b-227">Очевидно, что создавать анимированный GIF-файл гораздо сложнее.</span><span class="sxs-lookup"><span data-stu-id="12c4b-227">Obviously, it is much more effort to recreate an animated GIF.</span></span> <span data-ttu-id="12c4b-228">Предполагалось, что он должен быть ответственным за его повторное создание до окончания времени или ожидать, что пользователи не хотят тратить это время.</span><span class="sxs-lookup"><span data-stu-id="12c4b-228">Expect to be responsible to recreate it until the end of time, or expect people to throw it out, if they don't want to spend that time.</span></span>
6. <span data-ttu-id="12c4b-229">Постарайтесь, чтобы количество образов в статье было низким.</span><span class="sxs-lookup"><span data-stu-id="12c4b-229">Keep the number of images in an article low.</span></span> <span data-ttu-id="12c4b-230">Часто хорошим методом является создание одного общего снимка экрана некоторого средства, показывающего все, а затем описание остальной части текста.</span><span class="sxs-lookup"><span data-stu-id="12c4b-230">Often a good method is to make one overall screenshot of some tool, that shows everything, and then describe the rest in text.</span></span> <span data-ttu-id="12c4b-231">Это позволяет легко заменить снимок экрана при необходимости.</span><span class="sxs-lookup"><span data-stu-id="12c4b-231">This makes it easy to replace the screenshot when necessary.</span></span>

<span data-ttu-id="12c4b-232">Некоторые другие аспекты:</span><span class="sxs-lookup"><span data-stu-id="12c4b-232">Some other aspects:</span></span>

- <span data-ttu-id="12c4b-233">В пользовательском интерфейсе редактора снимков экрана должен использоваться светло-серый редактор тем, что не все пользователи имеют доступ к темной теме, и нам хотелось бы, чтобы они были как можно более постоянными.</span><span class="sxs-lookup"><span data-stu-id="12c4b-233">The editor UI for screenshots should use light gray theme editor as not all users have access to the dark theme and we'd like to keep things as consistent as possible.</span></span>
- <span data-ttu-id="12c4b-234">Ширина изображения по умолчанию — 500 пикселей, так как она хорошо отображается на большинстве мониторов.</span><span class="sxs-lookup"><span data-stu-id="12c4b-234">Default image width is 500 pixels, as this displays well on most monitors.</span></span> <span data-ttu-id="12c4b-235">Старайтесь не отклоняться от него слишком много.</span><span class="sxs-lookup"><span data-stu-id="12c4b-235">Try not to deviate too much from it.</span></span> <span data-ttu-id="12c4b-236">ширина 800 пикселей должна быть максимально допустимой.</span><span class="sxs-lookup"><span data-stu-id="12c4b-236">800 pixels width should be the maximum.</span></span>
- <span data-ttu-id="12c4b-237">Используйте Пнгс для снимков экрана пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="12c4b-237">Use PNGs for screenshots of UI.</span></span>
- <span data-ttu-id="12c4b-238">Используйте Пнгс или Жпгс для снимков экрана с трехмерным окном просмотра.</span><span class="sxs-lookup"><span data-stu-id="12c4b-238">Use PNGs or JPGs for 3D viewport screenshots.</span></span> <span data-ttu-id="12c4b-239">Предпочтение степени качества сжатия.</span><span class="sxs-lookup"><span data-stu-id="12c4b-239">Prefer quality over compression ratio.</span></span>

### <a name="list-of-component-properties"></a><span data-ttu-id="12c4b-240">Список свойств компонента</span><span class="sxs-lookup"><span data-stu-id="12c4b-240">List of component properties</span></span>

<span data-ttu-id="12c4b-241">При документировании списка свойств используйте полужирный текст, чтобы выделить имя свойства, а затем разрывы строк и обычный текст для описания.</span><span class="sxs-lookup"><span data-stu-id="12c4b-241">When documenting a list of properties, use bold text to highlight the property name, then line breaks and regular text to describe them.</span></span> <span data-ttu-id="12c4b-242">Не используйте разделы или списки маркированных точек.</span><span class="sxs-lookup"><span data-stu-id="12c4b-242">Do not use sub-chapters or bullet point lists.</span></span>

<span data-ttu-id="12c4b-243">Кроме того, не забудьте завершить все предложения с точкой.</span><span class="sxs-lookup"><span data-stu-id="12c4b-243">Also, don't forget to finish all sentences with a period.</span></span>

## <a name="page-completion-checklist"></a><span data-ttu-id="12c4b-244">Контрольный список завершения страницы</span><span class="sxs-lookup"><span data-stu-id="12c4b-244">Page completion checklist</span></span>

1. <span data-ttu-id="12c4b-245">Убедитесь, что выполнены рекомендации этого документа.</span><span class="sxs-lookup"><span data-stu-id="12c4b-245">Ensure that this document's guidelines were followed.</span></span>
1. <span data-ttu-id="12c4b-246">Просмотрите структуру документа и посмотрите, можно ли добавить новый документ в раздел " [см. также](#see-also) " на других страницах.</span><span class="sxs-lookup"><span data-stu-id="12c4b-246">Browse the document structure and see if the new document could be mentioned under the [See also](#see-also) section of other pages.</span></span>
1. <span data-ttu-id="12c4b-247">Если он доступен, обратитесь к странице с сведениями о проверке правильности.</span><span class="sxs-lookup"><span data-stu-id="12c4b-247">If available, have someone with knowledge of the topic proof-read the page for technical correctness.</span></span>
1. <span data-ttu-id="12c4b-248">Прочтите страницу с подтверждением стиля и форматирования.</span><span class="sxs-lookup"><span data-stu-id="12c4b-248">Have someone proof-read the page for style and formatting.</span></span> <span data-ttu-id="12c4b-249">Это может быть пользователь, не знакомый с разделом, который также является хорошей идеей, чтобы получить отзыв о том, насколько понятна документация.</span><span class="sxs-lookup"><span data-stu-id="12c4b-249">This can be someone unfamiliar with the topic, which is also a good idea to get feedback about how understandable the documentation is.</span></span>

## <a name="source-documentation"></a><span data-ttu-id="12c4b-250">Документация по источнику</span><span class="sxs-lookup"><span data-stu-id="12c4b-250">Source documentation</span></span>

<span data-ttu-id="12c4b-251">Документация по API будет создана автоматически из исходных файлов МРТК.</span><span class="sxs-lookup"><span data-stu-id="12c4b-251">API documentation will be generated automatically from the MRTK source files.</span></span> <span data-ttu-id="12c4b-252">Для облегчения этой задачи исходные файлы должны содержать следующее:</span><span class="sxs-lookup"><span data-stu-id="12c4b-252">To facilitate this, source files are required to contain the following:</span></span>

- [<span data-ttu-id="12c4b-253">Класс, структура, перечисление блоков сводки</span><span class="sxs-lookup"><span data-stu-id="12c4b-253">Class, struct, enum summary blocks</span></span>](#class-struct-enum-summary-blocks)
- [<span data-ttu-id="12c4b-254">Свойства, методы, блоки сводки событий</span><span class="sxs-lookup"><span data-stu-id="12c4b-254">Property, method, event summary blocks</span></span>](#property-method-event-summary-blocks)
- [<span data-ttu-id="12c4b-255">Версия и зависимости введения функции</span><span class="sxs-lookup"><span data-stu-id="12c4b-255">Feature introduction version and dependencies</span></span>](#feature-introduction-version-and-dependencies)
- [<span data-ttu-id="12c4b-256">Сериализованные поля</span><span class="sxs-lookup"><span data-stu-id="12c4b-256">Serialized fields</span></span>](#serialized-fields)
- [<span data-ttu-id="12c4b-257">Значения перечисления</span><span class="sxs-lookup"><span data-stu-id="12c4b-257">Enumeration values</span></span>](#enumeration-values)

<span data-ttu-id="12c4b-258">В дополнение к приведенному выше коду следует прокомментировать код, чтобы обеспечить возможность обслуживания, исправления ошибок и простоту настройки.</span><span class="sxs-lookup"><span data-stu-id="12c4b-258">In addition to the above, the code should be well commented to allow for maintenance, bug fixes and ease of customization.</span></span>

### <a name="class-struct-enum-summary-blocks"></a><span data-ttu-id="12c4b-259">Класс, структура, перечисление блоков сводки</span><span class="sxs-lookup"><span data-stu-id="12c4b-259">Class, struct, enum summary blocks</span></span>

<span data-ttu-id="12c4b-260">Если в МРТК добавляется класс, структура или перечисление, необходимо описать его назначение.</span><span class="sxs-lookup"><span data-stu-id="12c4b-260">If a class, struct or enum is being added to the MRTK, its purpose must be described.</span></span> <span data-ttu-id="12c4b-261">Это следует сделать в виде блока сводки над классом.</span><span class="sxs-lookup"><span data-stu-id="12c4b-261">This is to take the form of a summary block above the class.</span></span>

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

<span data-ttu-id="12c4b-262">Если имеются какие-либо зависимости уровня класса, их следует задокументировать в блоке «примечания» непосредственно под сводкой.</span><span class="sxs-lookup"><span data-stu-id="12c4b-262">If there are any class level dependencies, they should be documented in a remarks block, immediately below the summary.</span></span>

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

<span data-ttu-id="12c4b-263">Запросы на вытягивание, отправленные без сводок для классов, структур или перечислений не будут утверждены.</span><span class="sxs-lookup"><span data-stu-id="12c4b-263">Pull Requests submitted without summaries for classes, structures or enums will not be approved.</span></span>

### <a name="property-method-event-summary-blocks"></a><span data-ttu-id="12c4b-264">Свойства, методы, блоки сводки событий</span><span class="sxs-lookup"><span data-stu-id="12c4b-264">Property, method, event summary blocks</span></span>

<span data-ttu-id="12c4b-265">Свойства, методы и события (ПМЕС), а также поля задокументированы с помощью сводных блоков, независимо от видимости кода (общедоступный, частный, защищенный и внутренний).</span><span class="sxs-lookup"><span data-stu-id="12c4b-265">Properties, methods and events (PMEs) as well as fields are to be documented with summary blocks, regardless of code visibility (public, private, protected and internal).</span></span> <span data-ttu-id="12c4b-266">Средство создания документации отвечает за фильтрацию и публикацию только общедоступных и защищенных компонентов.</span><span class="sxs-lookup"><span data-stu-id="12c4b-266">The documentation generation tool is responsible for filtering out and publishing only the public and protected features.</span></span>

<span data-ttu-id="12c4b-267">Примечание. блок сводки **не** требуется для методов Unity (например: "спящий", "запустить", "Обновить").</span><span class="sxs-lookup"><span data-stu-id="12c4b-267">NOTE: A summary block is **not** required for Unity methods (ex: Awake, Start, Update).</span></span>

<span data-ttu-id="12c4b-268">Для утверждения запроса на вытягивание **требуется** документация по PME.</span><span class="sxs-lookup"><span data-stu-id="12c4b-268">PME documentation is **required** for a pull request to be approved.</span></span>

<span data-ttu-id="12c4b-269">Как часть сводного блока PME, требуется значение и назначение параметров и возвращаемых данных.</span><span class="sxs-lookup"><span data-stu-id="12c4b-269">As part of a PME summary block, the meaning and purpose of parameters and returned data is required.</span></span>

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a><span data-ttu-id="12c4b-270">Версия и зависимости введения функции</span><span class="sxs-lookup"><span data-stu-id="12c4b-270">Feature introduction version and dependencies</span></span>

<span data-ttu-id="12c4b-271">В составе сводной документации по API содержатся сведения о версии МРТК, в которой была представлена эта функция, а также о любых зависимостях, которые следует задокументировать в блоке примечаний.</span><span class="sxs-lookup"><span data-stu-id="12c4b-271">As part of the API summary documentation, information regarding the MRTK version in which the feature was introduced and any dependencies should be documented in a remarks block.</span></span>

<span data-ttu-id="12c4b-272">Зависимости должны включать расширения и (или) зависимости платформы.</span><span class="sxs-lookup"><span data-stu-id="12c4b-272">Dependencies should include extension and/or platform dependencies.</span></span>

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a><span data-ttu-id="12c4b-273">Сериализованные поля</span><span class="sxs-lookup"><span data-stu-id="12c4b-273">Serialized fields</span></span>

<span data-ttu-id="12c4b-274">Рекомендуется использовать атрибут ToolTip Unity, чтобы предоставить документацию среды выполнения для полей сценария в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="12c4b-274">It is a good practice to use Unity's tooltip attribute to provide runtime documentation for a script's fields in the inspector.</span></span>

<span data-ttu-id="12c4b-275">Так что параметры конфигурации включены в документацию по API, скрипты должны включать *по крайней мере* содержимое подсказки в блок сводки.</span><span class="sxs-lookup"><span data-stu-id="12c4b-275">So that configuration options are included in the API documentation, scripts are required to include *at least* the tooltip contents in a summary block.</span></span>

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a><span data-ttu-id="12c4b-276">Значения перечисления</span><span class="sxs-lookup"><span data-stu-id="12c4b-276">Enumeration values</span></span>

<span data-ttu-id="12c4b-277">При определении и перечислении код должен также документировать значение перечислимых значений с помощью блока Summary.</span><span class="sxs-lookup"><span data-stu-id="12c4b-277">When defining and enumeration, code must also document the meaning of the enum values using a summary block.</span></span> <span data-ttu-id="12c4b-278">Блоки примечаний при необходимости можно использовать для предоставления дополнительных сведений для улучшения понимания.</span><span class="sxs-lookup"><span data-stu-id="12c4b-278">Remarks blocks can optionally be used to provide additional details to enhance understanding.</span></span>

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a><span data-ttu-id="12c4b-279">Документация с инструкциями</span><span class="sxs-lookup"><span data-stu-id="12c4b-279">How-to documentation</span></span>

<span data-ttu-id="12c4b-280">Многим пользователям набора средств Mixed Reality может не потребоваться использовать документацию по API.</span><span class="sxs-lookup"><span data-stu-id="12c4b-280">Many users of the Mixed Reality Toolkit may not need to use the API documentation.</span></span> <span data-ttu-id="12c4b-281">Эти пользователи будут использовать готовые, многократно используемые Prefabs и сценарии для создания своих возможностей.</span><span class="sxs-lookup"><span data-stu-id="12c4b-281">These users will take advantage of our pre-made, reusable prefabs and scripts to create their experiences.</span></span>

<span data-ttu-id="12c4b-282">Каждая область функций будет содержать один или несколько файлов Markdown (. md), которые описывают на достаточно высоком уровне, что предоставляется.</span><span class="sxs-lookup"><span data-stu-id="12c4b-282">Each feature area will contain one or more markdown (.md) files that describe at a fairly high level, what is provided.</span></span> <span data-ttu-id="12c4b-283">В зависимости от размера и (или) сложности определенной функциональной области может потребоваться наличие дополнительных файлов, вплоть до одной для каждой предоставляемой функции.</span><span class="sxs-lookup"><span data-stu-id="12c4b-283">Depending on the size and/or complexity of a given feature area, there may be a need for additional files, up to one per feature provided.</span></span>

<span data-ttu-id="12c4b-284">При добавлении компонента (или изменении его использования) необходимо предоставить обзорную документацию.</span><span class="sxs-lookup"><span data-stu-id="12c4b-284">When a feature is added (or the usage is changed), overview documentation must be provided.</span></span>

<span data-ttu-id="12c4b-285">Как часть этой документации, вы можете использовать разделы с инструкциями, включая иллюстрации, чтобы помочь клиентам в создании новой функции или концепции в разделе Приступая к работе.</span><span class="sxs-lookup"><span data-stu-id="12c4b-285">As part of this documentation, how-to sections, including illustrations, should be provided to assist customers new to a feature or concept in getting started.</span></span>

## <a name="design-documentation"></a><span data-ttu-id="12c4b-286">Документация по проектированию</span><span class="sxs-lookup"><span data-stu-id="12c4b-286">Design documentation</span></span>

<span data-ttu-id="12c4b-287">Смешанная реальность дает возможность создавать совершенно новые мировые возможности.</span><span class="sxs-lookup"><span data-stu-id="12c4b-287">Mixed Reality provides an opportunity to create entirely new worlds.</span></span> <span data-ttu-id="12c4b-288">В результате может потребоваться создание пользовательских ресурсов для использования с МРТК.</span><span class="sxs-lookup"><span data-stu-id="12c4b-288">Part of this is likely to involve the creation of custom assets for use with the MRTK.</span></span> <span data-ttu-id="12c4b-289">Чтобы сделать это как можно более свободным для клиентов, компоненты должны предоставить документацию по проектированию, описывающую форматирование или другие требования для художественных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="12c4b-289">To make this as friction free as possible for customers, components should provide design documentation describing any formatting or other requirements for art assets.</span></span>

<span data-ttu-id="12c4b-290">Ниже приведены некоторые примеры, в которых документация по разработке может быть полезной:</span><span class="sxs-lookup"><span data-stu-id="12c4b-290">Some examples where design documentation can be helpful:</span></span>

- <span data-ttu-id="12c4b-291">Модели курсоров</span><span class="sxs-lookup"><span data-stu-id="12c4b-291">Cursor models</span></span>
- <span data-ttu-id="12c4b-292">Визуализации пространственных сопоставлений</span><span class="sxs-lookup"><span data-stu-id="12c4b-292">Spatial mapping visualizations</span></span>
- <span data-ttu-id="12c4b-293">Файлы звуковых эффектов</span><span class="sxs-lookup"><span data-stu-id="12c4b-293">Sound effect files</span></span>

<span data-ttu-id="12c4b-294">Этот тип документации **настоятельно** рекомендуется и **может** быть запрошен в ходе проверки запроса на включение внесенных изменений.</span><span class="sxs-lookup"><span data-stu-id="12c4b-294">This type of documentation is **strongly** recommended, and **may** be requested as part of a pull request review.</span></span>

<span data-ttu-id="12c4b-295">Это может отличаться от рекомендаций по проектированию на [сайте MS Developer](/windows/mixed-reality/design) .</span><span class="sxs-lookup"><span data-stu-id="12c4b-295">This may or may not be different from the design recommendation on the [MS Developer site](/windows/mixed-reality/design)</span></span>

## <a name="performance-notes"></a><span data-ttu-id="12c4b-296">Заметки о производительности</span><span class="sxs-lookup"><span data-stu-id="12c4b-296">Performance notes</span></span>

<span data-ttu-id="12c4b-297">Некоторые важные функции имеют стоимость производительности.</span><span class="sxs-lookup"><span data-stu-id="12c4b-297">Some important features come at a performance cost.</span></span> <span data-ttu-id="12c4b-298">Часто этот код будет очень в зависимости от того, как они настроены.</span><span class="sxs-lookup"><span data-stu-id="12c4b-298">Often this code will very depending how they are configured.</span></span>

<span data-ttu-id="12c4b-299">Пример.</span><span class="sxs-lookup"><span data-stu-id="12c4b-299">For example:</span></span>

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

<span data-ttu-id="12c4b-300">Заметки о производительности рекомендуются для компонентов ЦП и (или) ресурсов с большим количеством GPU и **могут** быть запрошены в ходе проверки запроса на включение внесенных изменений.</span><span class="sxs-lookup"><span data-stu-id="12c4b-300">Performance notes are recommended for CPU and/or GPU heavy components and **may** be requested as part of a pull request review.</span></span> <span data-ttu-id="12c4b-301">Все применимые заметки о производительности должны быть включены в API **и** обзорную документацию.</span><span class="sxs-lookup"><span data-stu-id="12c4b-301">Any applicable performance notes are to be included in API **and** overview documentation.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="12c4b-302">Критические изменения</span><span class="sxs-lookup"><span data-stu-id="12c4b-302">Breaking changes</span></span>

<span data-ttu-id="12c4b-303">Документация по критическим изменениям состоит из [файла](../contributing/breaking-changes.md) верхнего уровня, который ссылается на отдельные breaking-changes.md каждой области функций.</span><span class="sxs-lookup"><span data-stu-id="12c4b-303">Breaking changes documentation is to consist of a top level [file](../contributing/breaking-changes.md) which links to each feature area's individual breaking-changes.md.</span></span>

<span data-ttu-id="12c4b-304">Файлы в области функций breaking-changes.md содержат список всех известных критических изменений для данного выпуска **,** а также историю критических изменений из прошлых выпусков.</span><span class="sxs-lookup"><span data-stu-id="12c4b-304">The feature area breaking-changes.md files are to contain the list of all known breaking changes for a given release **as well as** the history of breaking changes from past releases.</span></span>

<span data-ttu-id="12c4b-305">Пример.</span><span class="sxs-lookup"><span data-stu-id="12c4b-305">For example:</span></span>

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

<span data-ttu-id="12c4b-306">Сведения, содержащиеся в файлах breaking-changes.md уровня функций, будут объединены в заметки о выпуске для каждого нового выпуска МРТК.</span><span class="sxs-lookup"><span data-stu-id="12c4b-306">The information contained within the feature level breaking-changes.md files will be aggregated to the release notes for each new MRTK release.</span></span>

<span data-ttu-id="12c4b-307">Все критические изменения, которые являются частью изменения, **должны** быть документированы как часть запроса на включение внесенных изменений.</span><span class="sxs-lookup"><span data-stu-id="12c4b-307">Any breaking changes that are part of a change **must** be documented as part of a Pull Request.</span></span>

## <a name="tools-for-editing-markdown"></a><span data-ttu-id="12c4b-308">Средства для редактирования MarkDown</span><span class="sxs-lookup"><span data-stu-id="12c4b-308">Tools for editing MarkDown</span></span>

<span data-ttu-id="12c4b-309">[Visual Studio Code](https://code.visualstudio.com/) — это отличное средство для редактирования файлов Markdown, которые являются частью документации по мртк.</span><span class="sxs-lookup"><span data-stu-id="12c4b-309">[Visual Studio Code](https://code.visualstudio.com/) is a great tool for editing markdown files that are part of MRTK's documentation.</span></span>

<span data-ttu-id="12c4b-310">При написании документации также настоятельно рекомендуется установить следующие два расширения:</span><span class="sxs-lookup"><span data-stu-id="12c4b-310">When writing documentation, installing the following two extensions is also highly recommended:</span></span>

- <span data-ttu-id="12c4b-311">Документация расширения Markdown для Visual Studio Code — используйте сочетание клавиш ALT + M, чтобы открыть меню параметров создания документов.</span><span class="sxs-lookup"><span data-stu-id="12c4b-311">Docs Markdown Extension for Visual Studio Code - Use Alt+M to bring up a menu of docs authoring options.</span></span>

- <span data-ttu-id="12c4b-312">Средство проверки орфографии кода — слова с ошибками будут подчеркнуты. Щелкните правой кнопкой мыши слово с ошибками, чтобы изменить его или сохранить в словаре.</span><span class="sxs-lookup"><span data-stu-id="12c4b-312">Code Spell Checker - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

<span data-ttu-id="12c4b-313">Оба эти пакета поставляются в пакет создания опубликованных документов Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="12c4b-313">Both of these come packaged in the Microsoft published Docs Authoring Pack.</span></span>

## <a name="see-also"></a><span data-ttu-id="12c4b-314">См. также</span><span class="sxs-lookup"><span data-stu-id="12c4b-314">See also</span></span> 

* [<span data-ttu-id="12c4b-315">Пример ссылки</span><span class="sxs-lookup"><span data-stu-id="12c4b-315">Example link</span></span>](https://www.google.com)