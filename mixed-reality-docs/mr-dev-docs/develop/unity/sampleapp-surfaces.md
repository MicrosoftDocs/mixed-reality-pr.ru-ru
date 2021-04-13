---
title: Surfaces
description: Узнайте, как создать тактиле сенсатионс с помощью визуального, звукового и четкого отслеживания в примере приложения Surfaces.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality, проектирование, пример приложения, элементы управления, МРТК, набор средств для смешанной реальности, Unity, примеры приложений, примеры приложений, Открытый исходный код, Microsoft Store, HoloLens, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 0e75a72ec518dea3513b6868aec56d1c7c89bd05
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300139"
---
# <a name="surfaces"></a><span data-ttu-id="7bbaf-104">Surfaces</span><span class="sxs-lookup"><span data-stu-id="7bbaf-104">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="7bbaf-105">В этой статье рассматривается исследовательская выборка, созданная в [лабораторных занятиях по смешанной реальности](https://github.com/Microsoft/MRDesignLabs_Unity), где мы предоставляем наши знания и предложения по разработке приложений для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="7bbaf-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="7bbaf-106">Наши статьи и код, относящиеся к проектированию, будут развиваться по мере внесения новых обнаружений.</span><span class="sxs-lookup"><span data-stu-id="7bbaf-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="7bbaf-107">[Surfaces — это](https://github.com/microsoft/MRDL_Unity_Surfaces)  пример приложения с открытым исходным кодом от лабораторных занятий корпорации Майкрософт по проектированию смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="7bbaf-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="7bbaf-108">Он изучает, как можно создать тактиле неожиданностью с визуальным, звуковым и полноценным отслеживанием вручную.</span><span class="sxs-lookup"><span data-stu-id="7bbaf-108">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Surfaces](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="7bbaf-110">Демонстрационное видео</span><span class="sxs-lookup"><span data-stu-id="7bbaf-110">Demo video</span></span> 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="7bbaf-111">Записано с помощью HoloLens 2 с записью смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="7bbaf-111">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="7bbaf-112">Сведения о приложении</span><span class="sxs-lookup"><span data-stu-id="7bbaf-112">About the app</span></span>

<span data-ttu-id="7bbaf-113">На поверхностях показано, как использовать систему ввода и стандартные блоки набора средств Mixed Reality Toolkit (МРТК) для создания приложений для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7bbaf-113">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="7bbaf-114">В этом проекте можно найти примеры:</span><span class="sxs-lookup"><span data-stu-id="7bbaf-114">In this project, you can find the examples of:</span></span>

- <span data-ttu-id="7bbaf-115">Используйте [входную систему](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview)мртк, в частности отслеживание вручную или совместно.</span><span class="sxs-lookup"><span data-stu-id="7bbaf-115">Use MRTK's [Input System](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="7bbaf-116">Используйте [стандартный ШЕЙДЕР](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) мртк для работы с графикой.</span><span class="sxs-lookup"><span data-stu-id="7bbaf-116">Use MRTK's [Standard Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) for performant graphics.</span></span>

<span data-ttu-id="7bbaf-117">Вы можете использовать компоненты этого проекта для создания собственных приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="7bbaf-117">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="7bbaf-118">Дни разработки MR 2020 — сведения из приложения MR Surfaces</span><span class="sxs-lookup"><span data-stu-id="7bbaf-118">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>

[<span data-ttu-id="7bbaf-119">Сведения из приложения MR Surfaces</span><span class="sxs-lookup"><span data-stu-id="7bbaf-119">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="7bbaf-120">С Симкинс, старший дизайнер, лежащий в основе приложения МРДЛ Surfaces, рассказывает о статье о проектировании и технических возможностях приложения.</span><span class="sxs-lookup"><span data-stu-id="7bbaf-120">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="7bbaf-121">Репозиторий проекта в GitHub</span><span class="sxs-lookup"><span data-stu-id="7bbaf-121">Project repository on GitHub</span></span>

[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="7bbaf-122">Скачать приложение из Microsoft Store в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7bbaf-122">Download app from Microsoft Store in HoloLens 2</span></span>

https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="7bbaf-123">(Приложение доступно только в HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="7bbaf-123">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="7bbaf-124">Об авторе</span><span class="sxs-lookup"><span data-stu-id="7bbaf-124">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="7bbaf-125"><b>Дон Юн Парк</b> (Dong Yoon Park)</span><span class="sxs-lookup"><span data-stu-id="7bbaf-125"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="7bbaf-126">Разработчик средств взаимодействия с пользователем @Microsoft</span><span class="sxs-lookup"><span data-stu-id="7bbaf-126">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="7bbaf-127">См. также</span><span class="sxs-lookup"><span data-stu-id="7bbaf-127">See also</span></span>

* <span data-ttu-id="7bbaf-128">[MRTK Examples Hub](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(скачайте из Microsoft Store в HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="7bbaf-128">[MRTK Examples Hub](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="7bbaf-129">[Surfaces](sampleapp-surfaces.md) - [(скачайте из Microsoft Store в HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="7bbaf-129">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="7bbaf-130">Periodic Table of the Elements 2.0</span><span class="sxs-lookup"><span data-stu-id="7bbaf-130">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="7bbaf-131">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="7bbaf-131">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)
