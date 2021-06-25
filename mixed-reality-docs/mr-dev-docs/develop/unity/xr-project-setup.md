---
title: Настройка конфигурации XR
description: Оставайтесь в курсе последних рекомендаций по конфигурации Unity XR для разработки приложений HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: микседреалититулкит, микседреалититулкит-Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Unity
ms.openlocfilehash: d265725caf95379dfa01baa6dad1b7927fbeca5c
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906948"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="0feb7-104">Настройка конфигурации XR</span><span class="sxs-lookup"><span data-stu-id="0feb7-104">Setting up your XR configuration</span></span>

<span data-ttu-id="0feb7-105">При запуске нового проекта Unity у вас есть три разных варианта для обработки потребностей XR:</span><span class="sxs-lookup"><span data-stu-id="0feb7-105">When you start a new Unity project, you have three different options for handling your XR needs:</span></span> 
* <span data-ttu-id="0feb7-106">Подключаемый модуль Опенкср</span><span class="sxs-lookup"><span data-stu-id="0feb7-106">OpenXR plugin</span></span>
* <span data-ttu-id="0feb7-107">Подключаемый модуль Windows XR</span><span class="sxs-lookup"><span data-stu-id="0feb7-107">Windows XR plugin</span></span>
* <span data-ttu-id="0feb7-108">Устаревший подключаемый модуль XR</span><span class="sxs-lookup"><span data-stu-id="0feb7-108">Legacy XR plugin</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="0feb7-109">Настройка проекта с помощью МРТК</span><span class="sxs-lookup"><span data-stu-id="0feb7-109">Setting up your project with MRTK</span></span>

<span data-ttu-id="0feb7-110">MRTK для Unity предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="0feb7-110">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="0feb7-111">MRTK версии 2 предназначен для ускорения разработки приложений для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR.</span><span class="sxs-lookup"><span data-stu-id="0feb7-111">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="0feb7-112">Цель проекта — упростить разработку приложений смешанной реальности и вносить вклад в сообщество по мере развития навыков.</span><span class="sxs-lookup"><span data-stu-id="0feb7-112">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0feb7-113">Ознакомьтесь с нашими руководствами по МРТК</span><span class="sxs-lookup"><span data-stu-id="0feb7-113">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="0feb7-114">Дополнительные сведения о функциях см. в [документации по MRTK ](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="0feb7-114">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

### <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="0feb7-115">Использование МРТК с поддержкой Опенкср</span><span class="sxs-lookup"><span data-stu-id="0feb7-115">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="0feb7-116">Выпуск MRTK-Unity 2,7 обеспечивает лучшую поддержку для подключаемого модуля Опенкср в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="0feb7-116">MRTK-Unity 2.7 release provides better supports for the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="0feb7-117">Снова откройте [средство "функция смешанной реальности](welcome-to-mr-feature-tool.md) ", чтобы установить набор средств Mixed Reality, если вы этого еще не сделали.</span><span class="sxs-lookup"><span data-stu-id="0feb7-117">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="0feb7-118">Поддержка Опенкср находится в пакете **Foundation** .</span><span class="sxs-lookup"><span data-stu-id="0feb7-118">OpenXR support is in the **Foundation** package.</span></span>

<span data-ttu-id="0feb7-119">[Более подробные сведения о переходе на опенкср](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)см. в документации по мртк.</span><span class="sxs-lookup"><span data-stu-id="0feb7-119">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="0feb7-120">При обновлении предыдущей версии МРТК, более ранней, чем **2.5.3**, убедитесь, что в файле **Assets/микседреалититулкит. generated/link.xml** указана следующая строка:</span><span class="sxs-lookup"><span data-stu-id="0feb7-120">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="0feb7-121">Эта строка будет добавлена по умолчанию, если вы начали работу с МРТК 2.5.4 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="0feb7-121">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="0feb7-122">Настройка вручную без МРТК</span><span class="sxs-lookup"><span data-stu-id="0feb7-122">Manual setup without MRTK</span></span>

<span data-ttu-id="0feb7-123">Хотя корпорация Майкрософт и сообщество создали средства конвертер, такие как набор средств для [смешанной реальности (мртк)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) , который автоматически настраивает среду ВМР, многие разработчики хотят создавать свои впечатления с нуля.</span><span class="sxs-lookup"><span data-stu-id="0feb7-123">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]