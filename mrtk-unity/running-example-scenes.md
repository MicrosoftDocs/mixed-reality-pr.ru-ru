---
title: Примеры сцен
description: Узнайте, как получить и использовать примеры сцен МРТК.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: набор средств для смешанной реальности, мртк, примеры, HoloLens, HoloLens 2, шейдеры, подсказки, взаимодействие с руки, обрезка, ограничивающие прямоугольники, кнопки, меню руки, планшет, ползунок
ms.openlocfilehash: d8d2bb40ff1c95e01cb051f36de04beb93829ba1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177471"
---
# <a name="example-scenes"></a><span data-ttu-id="57650-104">Примеры сцен</span><span class="sxs-lookup"><span data-stu-id="57650-104">Example scenes</span></span>

<span data-ttu-id="57650-105">МРТК предоставляет различные типы примеров сцен, демонстрирующие функции МРТК и стандартные блоки для удобства работы пользователей.</span><span class="sxs-lookup"><span data-stu-id="57650-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="57650-106">Примеры сцен и которая разбила могут быть полезными для понимания функций и применения их к проектам.</span><span class="sxs-lookup"><span data-stu-id="57650-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="57650-107">Как получить примеры сцен</span><span class="sxs-lookup"><span data-stu-id="57650-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="57650-108">Использование инструмента для функций смешанной реальности и диспетчера пакетов Unity</span><span class="sxs-lookup"><span data-stu-id="57650-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="57650-109">вы можете скачать и импортировать **примеры пакетов смешанной реальности набор средств** с помощью [инструмента "функция смешанной реальности](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) ".</span><span class="sxs-lookup"><span data-stu-id="57650-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="57650-110">в Unity используйте **окно меню > диспетчер пакетов > в Project > Custom** и выберите **примеры набор средств смешанной реальности**.</span><span class="sxs-lookup"><span data-stu-id="57650-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="57650-111">в списке, расположенном в правой части панели, нажмите кнопку **импортировать в Project** кнопку рядом с примером имен сцен.</span><span class="sxs-lookup"><span data-stu-id="57650-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="57650-112">например, можно нажать кнопку **импорт в Project** кнопку рядом с параметром **демонстрации — хандтраккинг**.</span><span class="sxs-lookup"><span data-stu-id="57650-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="57650-113">После импорта их можно будет найти в папке **assets > Samples** .</span><span class="sxs-lookup"><span data-stu-id="57650-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="57650-114">**Хандинтерактионексамплес** сцена — отличное место для начала работы с пространственными взаимодействиями мртк и стандартными блоками пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="57650-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="57650-115">Непосредственная загрузка и импорт пакетов из GitHub</span><span class="sxs-lookup"><span data-stu-id="57650-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="57650-116">если вы не используете средство для работы с смешанной реальности, вы можете загрузить и импортировать файл **Microsoft. микседреалити. набор средств напрямую. Unity. examples. пакет unitypackage** со [страницы выпуска мртк GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="57650-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="57650-117">Чтобы импортировать скачанный файл пакет unitypackage, используйте **активы > импортировать пакет > меню настраиваемого пакета** .</span><span class="sxs-lookup"><span data-stu-id="57650-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="57650-118">После импорта вы сможете найти примеры сцен в разделе **assets > мртк > examples > демонстрации**.</span><span class="sxs-lookup"><span data-stu-id="57650-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>
