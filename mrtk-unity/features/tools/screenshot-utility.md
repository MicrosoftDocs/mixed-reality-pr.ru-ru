---
title: Служебная программа для создания снимков экрана
description: Документация по использованию средства для создания снимков экрана в MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 936126214f9e6d93ccbb871b9c80a2c93acf5a86
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176422"
---
# <a name="screenshot-utility"></a><span data-ttu-id="b45ee-104">Служебная программа для создания снимков экрана</span><span class="sxs-lookup"><span data-stu-id="b45ee-104">Screenshot utility</span></span>

<span data-ttu-id="b45ee-105">Если вы часто создаете снимки экрана в Unity для документации и рекламных материалов, этот процесс может быть очень трудоемким и не давать желаемых результатов.</span><span class="sxs-lookup"><span data-stu-id="b45ee-105">Often taking screenshots in Unity for documentation and promotional imagery can be burdensome and the output often looks less than desirable.</span></span> <span data-ttu-id="b45ee-106">Решить эти проблемы поможет `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility).</span><span class="sxs-lookup"><span data-stu-id="b45ee-106">This is where the `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) class comes into play.</span></span>

<span data-ttu-id="b45ee-107">Класс ScreenshotUtility позволяет создавать снимки экрана через пункты меню и общедоступные API в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="b45ee-107">The ScreenshotUtility class aides in taking screenshots via menu items and public APIs within the Unity editor.</span></span> <span data-ttu-id="b45ee-108">Снимки экрана можно создавать с разным разрешением и прозрачными цветами для последующего простого наложения изображений.</span><span class="sxs-lookup"><span data-stu-id="b45ee-108">Screenshots can be captured at various resolutions and with transparent clear colors for use in easy post compositing of images.</span></span> <span data-ttu-id="b45ee-109">Это средство не поддерживает создание снимков экрана из изолированной сборки.</span><span class="sxs-lookup"><span data-stu-id="b45ee-109">Taking screenshots from a standalone build is not supported by this tool.</span></span>

## <a name="taking-screenshots"></a><span data-ttu-id="b45ee-110">Создание снимков экрана</span><span class="sxs-lookup"><span data-stu-id="b45ee-110">Taking screenshots</span></span>

<span data-ttu-id="b45ee-111">снимки экрана можно легко захватить в редакторе, выбрав **смешанная реальность**  >  **набор средств**  >  **служебные программы** на  >  **снимке экрана** и выбрав нужный вариант.</span><span class="sxs-lookup"><span data-stu-id="b45ee-111">Screenshots can be easily capture while in the editor by selecting **Mixed Reality** > **Toolkit** > **Utilities** > **Take Screenshot** and then selecting your desired option.</span></span> <span data-ttu-id="b45ee-112">Если вы создаете снимок экрана не во время игры, убедитесь, что вкладка с окном игры отображается. В противном случае снимок экрана не будет сохранен.</span><span class="sxs-lookup"><span data-stu-id="b45ee-112">Make sure to have the game window tab visible if capturing while not playing, or a screenshot may not be saved.</span></span>

<span data-ttu-id="b45ee-113">По умолчанию все снимки экрана сохраняются по [пути временного кэша](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), а путь к самому снимку экрана отобразится в консоли Unity.</span><span class="sxs-lookup"><span data-stu-id="b45ee-113">By default, all screenshots are saved to your [temporary cache path](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), the path to the screenshot will be displayed in the Unity console.</span></span>

![Пункт меню служебной программы для создания снимков экрана](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a><span data-ttu-id="b45ee-115">Пример создания снимка экрана</span><span class="sxs-lookup"><span data-stu-id="b45ee-115">Example screenshot capture</span></span>

<span data-ttu-id="b45ee-116">Приведенный ниже снимок экрана был создан с использованием варианта *"4x Resolution (Transparent Background)"* (Четырехкратное разрешение (прозрачный фон)).</span><span class="sxs-lookup"><span data-stu-id="b45ee-116">The below screenshot was captured with the *"4x Resolution (Transparent Background)"* option.</span></span> <span data-ttu-id="b45ee-117">При этом создается изображение с высоким разрешением и преобразованием пикселей с удаленным цветом в прозрачные пиксели.</span><span class="sxs-lookup"><span data-stu-id="b45ee-117">This outputs a high-resolution image with whatever pixels normally represented by the clear color saved as transparent pixels.</span></span> <span data-ttu-id="b45ee-118">Это позволяет разработчикам продемонстрировать использование своего приложения в магазине или других на других медиаплощадках, наложив это изображение поверх других изображений.</span><span class="sxs-lookup"><span data-stu-id="b45ee-118">This technique helps developers showcase their application for the store, or other media outlets, by overlaying this image on top of other imagery.</span></span>

![Пример захвата с помощью служебной программы для создания снимков экрана](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
