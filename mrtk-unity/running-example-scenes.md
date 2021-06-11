---
title: Выполнение примера сцен
description: Узнайте, как получить и использовать примеры сцен МРТК.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: набор средств для смешанной реальности, МРТК, примеры, HoloLens, HoloLens 2, шейдеры, подсказки, взаимодействие руки, обрезка, ограничивающие прямоугольники, кнопки, меню руки, планшет, ползунок
ms.openlocfilehash: 8ba4df237189f0de3bd869bc05bdf7e3c5451490
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/10/2021
ms.locfileid: "111911884"
---
# <a name="example-scenes"></a><span data-ttu-id="79d96-104">Примеры сцен</span><span class="sxs-lookup"><span data-stu-id="79d96-104">Example scenes</span></span>

<span data-ttu-id="79d96-105">МРТК предоставляет различные типы примеров сцен, демонстрирующие функции МРТК и стандартные блоки для удобства работы пользователей.</span><span class="sxs-lookup"><span data-stu-id="79d96-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="79d96-106">Примеры сцен и которая разбила могут быть полезными для понимания функций и применения их к проектам.</span><span class="sxs-lookup"><span data-stu-id="79d96-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="79d96-107">Как получить примеры сцен</span><span class="sxs-lookup"><span data-stu-id="79d96-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="79d96-108">Использование инструмента для функций смешанной реальности и диспетчера пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="79d96-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="79d96-109">Пакет **примеров набора средств для смешанной реальности** можно скачать и импортировать с помощью [инструмента для функций смешанной реальности](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) .</span><span class="sxs-lookup"><span data-stu-id="79d96-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="79d96-110">В Unity используйте **окно меню > диспетчер пакетов > в Project > Custom** и выберите **примеры набора средств смешанной реальности**.</span><span class="sxs-lookup"><span data-stu-id="79d96-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="79d96-111">В списке в правой части панели нажмите кнопку **импортировать в проект** рядом с примером имен сцен.</span><span class="sxs-lookup"><span data-stu-id="79d96-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="79d96-112">Например, можно нажать кнопку **импортировать в проект** рядом с параметром **демонстрации — хандтраккинг**.</span><span class="sxs-lookup"><span data-stu-id="79d96-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="79d96-113">После импорта их можно будет найти в папке **assets > Samples** .</span><span class="sxs-lookup"><span data-stu-id="79d96-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="79d96-114">**Хандинтерактионексамплес** сцена — отличное место для начала работы с пространственными взаимодействиями мртк и стандартными блоками пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="79d96-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="79d96-115">Непосредственная загрузка и импорт пакетов из GitHub</span><span class="sxs-lookup"><span data-stu-id="79d96-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="79d96-116">Если вы не используете средство для работы с смешанной реальности, вы можете загрузить и импортировать файл **Microsoft. микседреалити. Toolkit. Unity. examples. пакет unitypackage** со [страницы выпуска мртк GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) .</span><span class="sxs-lookup"><span data-stu-id="79d96-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="79d96-117">Чтобы импортировать скачанный файл пакет unitypackage, используйте **активы > импортировать пакет > меню настраиваемого пакета** .</span><span class="sxs-lookup"><span data-stu-id="79d96-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="79d96-118">После импорта вы сможете найти примеры сцен в разделе **assets > мртк > examples > демонстрации**.</span><span class="sxs-lookup"><span data-stu-id="79d96-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>