---
title: Окно зависимости
description: Документация по использованию окна зависимости в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 590476add6904f76081630c4416184bea9f694ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176663"
---
# <a name="dependency-window"></a><span data-ttu-id="60748-104">Окно зависимости</span><span class="sxs-lookup"><span data-stu-id="60748-104">Dependency window</span></span>

<span data-ttu-id="60748-105">В Unity часто бывает трудно глеам, какие ресурсы используются и на что они ссылаются.</span><span class="sxs-lookup"><span data-stu-id="60748-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="60748-106">Параметр "найти ссылки в сцене" прекрасно работает, если вас интересует только текущая сцена, но как насчет всего проекта Unity?</span><span class="sxs-lookup"><span data-stu-id="60748-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="60748-107">Здесь можно использовать **окно зависимости** (Assets/Мртк/Tools/депенденцивиндов).</span><span class="sxs-lookup"><span data-stu-id="60748-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="60748-108">В окне зависимости показано, как ресурсы ссылаются и зависят друг от друга.</span><span class="sxs-lookup"><span data-stu-id="60748-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="60748-109">Зависимости рассчитываются путем синтаксического анализа идентификаторов GUID в файлах проекта YAML (Обратите внимание, что зависимости скриптов в скриптах не рассматриваются).</span><span class="sxs-lookup"><span data-stu-id="60748-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="60748-110">Использование</span><span class="sxs-lookup"><span data-stu-id="60748-110">Usage</span></span>

<span data-ttu-id="60748-111">чтобы открыть это окно, выберите **смешанная реальность**  >  **набор средств**  >  **служебных программ**  >  **окно зависимостей** , которое откроет окно и автоматически начнет создавать граф зависимостей проекта.</span><span class="sxs-lookup"><span data-stu-id="60748-111">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Dependency Window** which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="60748-112">После построения графа зависимостей можно выбрать ресурсы на вкладке "проект", чтобы проверить их зависимости.</span><span class="sxs-lookup"><span data-stu-id="60748-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

![Окно зависимости](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="60748-114">В окне отображается список ресурсов, от которых зависит текущий выбранный ресурс, и иерархический список зависимых от него активов.</span><span class="sxs-lookup"><span data-stu-id="60748-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="60748-115">Если ничего не зависит от выбранного ресурса, можно удалить его из проекта (Обратите внимание, что некоторые ресурсы загружаются программно с помощью интерфейсов API, таких как шейдер. Find () и не могут быть перехвачены средством записи зависимостей).</span><span class="sxs-lookup"><span data-stu-id="60748-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="60748-116">В окне также может отображаться только список всех ресурсов, на которые не ссылаются другие активы, и они могут быть учтены при удалении:</span><span class="sxs-lookup"><span data-stu-id="60748-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![Окно зависимости, показывающее ресурсы, на которые нет ссылок](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="60748-118">Если ресурсы изменяются, добавляются или удаляются во время использования окна зависимости, рекомендуется обновить граф зависимостей для наиболее актуальных результатов.</span><span class="sxs-lookup"><span data-stu-id="60748-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
