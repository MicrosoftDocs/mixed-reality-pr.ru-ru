---
title: Служебная программа переключения ресурсов
description: Документация по использованию служебной программы переключения ресурсов в МРТК для Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк
ms.openlocfilehash: 50ef252913575988b5f377dd9ff92f9e9ade3a72
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176164"
---
# <a name="asset-swap-utility"></a><span data-ttu-id="3176b-104">Служебная программа переключения ресурсов</span><span class="sxs-lookup"><span data-stu-id="3176b-104">Asset swap utility</span></span>

<span data-ttu-id="3176b-105">Поиск и замена повсеместно работают при работе в средствах создания текста и содержимого.</span><span class="sxs-lookup"><span data-stu-id="3176b-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="3176b-106">Если вам нужно поменять местами многие ресурсы в сцене Unity, это там, где [ассетсвапутилити](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [скриптаблеобжект](https://docs.unity3d.com/Manual/class-ScriptableObject.html) и редактор могут поработать с рукой.</span><span class="sxs-lookup"><span data-stu-id="3176b-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="3176b-107">Программа входит в состав `Microsoft.MixedReality.Toolkit.Unity.Tools` пакета.</span><span class="sxs-lookup"><span data-stu-id="3176b-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="3176b-108">`AssetSwapUtility`Команда сохраняет все действия Find и Replace в виде скриптаблеобжект, чтобы они тривал переключаться назад или сохранить подстановку «Themes» для будущего использования.</span><span class="sxs-lookup"><span data-stu-id="3176b-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="3176b-109">Переключение ресурсов</span><span class="sxs-lookup"><span data-stu-id="3176b-109">Swapping assets</span></span>

<span data-ttu-id="3176b-110">После создания можно легко поменять местами ресурсы `AssetSwapCollection` .</span><span class="sxs-lookup"><span data-stu-id="3176b-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="3176b-111">Давайте продемонстрируем использование, переключая два красных Куба с двумя голубыми шарик в сцене.</span><span class="sxs-lookup"><span data-stu-id="3176b-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="3176b-112">Сначала добавьте два Красного Куба в сцену, в которых используется куб Unity по умолчанию и `MRTK_Standard_Red` материал.</span><span class="sxs-lookup"><span data-stu-id="3176b-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="3176b-113">чтобы создать `AssetSwapCollection` , перейдите в раздел **смешанная реальность набор средств > служебные программы > создать коллекцию переключения ресурсов**.</span><span class="sxs-lookup"><span data-stu-id="3176b-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="3176b-114">Выбрав параметр `AssetSwapCollection` заполните свойства, как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="3176b-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Коллекция переключения ресурсов в редакторе Unity](images/asset-swap-img-01.png)

<span data-ttu-id="3176b-116">Затем выберите "синий шарик" из раскрывающегося списка "выбранная тема" и нажмите кнопку "Применить".</span><span class="sxs-lookup"><span data-stu-id="3176b-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="3176b-117">Все красные Кубы в сцене должны быть заменены синим шарик.</span><span class="sxs-lookup"><span data-stu-id="3176b-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![Коллекция переключения ресурсов в редакторе Unity с выделенной темой](images/asset-swap-img-02.png)

<span data-ttu-id="3176b-119">В этом примере мы выполнили полную замену сцены, но вы можете заменить части сцены, изменив режим выбора.</span><span class="sxs-lookup"><span data-stu-id="3176b-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="3176b-120">Вы также можете вернуться к красному Кубу, выбрав "красные Кубы" из раскрывающегося списка "выбранная тема" и нажав кнопку "Применить".</span><span class="sxs-lookup"><span data-stu-id="3176b-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="3176b-121">Можно поменять местами все типы ресурсов, такие как звуковые файлы, шрифты, Prefabs и т. д. Выполняет `AssetSwapUtility` несколько проверок работоспособности, чтобы обеспечить переключение на похожие типы.</span><span class="sxs-lookup"><span data-stu-id="3176b-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>
