---
title: Использование устаревшей встроенной поддержки XR
description: Узнайте, как настроить проекты Unity с помощью и без МРТК, используя устаревшие встроенные службы поддержки XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, Mixed Reality, разработка, начало работы, новый проект, Windows Mixed Reality, UWP, XR, производительность, устаревший, мртк
ms.openlocfilehash: 0860154034a63d5058da09a3b842e70bc3775dc5
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938134"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="a3fca-104">Использование устаревшей встроенной поддержки XR</span><span class="sxs-lookup"><span data-stu-id="a3fca-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="a3fca-105">Настройка проекта с помощью МРТК</span><span class="sxs-lookup"><span data-stu-id="a3fca-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="a3fca-106">MRTK для Unity предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="a3fca-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="a3fca-107">MRTK версии 2 предназначен для ускорения разработки приложений для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR.</span><span class="sxs-lookup"><span data-stu-id="a3fca-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="a3fca-108">Цель проекта — упростить разработку приложений смешанной реальности и вносить вклад в сообщество по мере развития навыков.</span><span class="sxs-lookup"><span data-stu-id="a3fca-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a3fca-109">Ознакомьтесь с нашими руководствами по МРТК</span><span class="sxs-lookup"><span data-stu-id="a3fca-109">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="a3fca-110">Дополнительные сведения о функциях см. в [документации по мртк](/windows/mixed-reality/mrtk-unity) .</span><span class="sxs-lookup"><span data-stu-id="a3fca-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="a3fca-111">Настройка вручную без МРТК</span><span class="sxs-lookup"><span data-stu-id="a3fca-111">Manual setup without MRTK</span></span>

<span data-ttu-id="a3fca-112">Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:</span><span class="sxs-lookup"><span data-stu-id="a3fca-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](images/wmr-config-img-3.png)

<span data-ttu-id="a3fca-114">Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="a3fca-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="a3fca-115">Выберите **файл > параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="a3fca-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="a3fca-116">Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .</span><span class="sxs-lookup"><span data-stu-id="a3fca-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="a3fca-117">Установка **архитектуры** **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="a3fca-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="a3fca-118">Задать **целевое устройство** в **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="a3fca-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="a3fca-119">Задать для **типа сборки** **D3D**</span><span class="sxs-lookup"><span data-stu-id="a3fca-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="a3fca-120">Установить **последнюю версию** **пакета SDK для UWP**</span><span class="sxs-lookup"><span data-stu-id="a3fca-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="a3fca-121">Задать для **конфигурации сборки** значение **Release** , так как имеются известные проблемы с производительностью при отладке</span><span class="sxs-lookup"><span data-stu-id="a3fca-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](images/wmr-config-img-4.png)

<span data-ttu-id="a3fca-123">После настройки платформы необходимо разрешить Unity создавать [иммерсивное представление](../../design/app-views.md) вместо 2D-представления при экспорте.</span><span class="sxs-lookup"><span data-stu-id="a3fca-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="a3fca-124">Устаревший XR является устаревшим в Unity 2019 и удален в Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="a3fca-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="a3fca-125">Открыть **Параметры проигрывателя...** из **параметров сборки... и разверните** группу **параметров XR**</span><span class="sxs-lookup"><span data-stu-id="a3fca-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="a3fca-126">В разделе **Параметры XR** выберите **Виртуальная реальность поддержка** , чтобы добавить список устройств виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="a3fca-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="a3fca-127">Установка **16-разрядного** **формата глубины** и включение **общего доступа к буферу глубины**</span><span class="sxs-lookup"><span data-stu-id="a3fca-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="a3fca-128">Задать **режим отображения стерео** для **одного экземпляра Pass**</span><span class="sxs-lookup"><span data-stu-id="a3fca-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="a3fca-129">Выберите **WSA holographic Remoting поддерживается** , если вы хотите использовать удаленное взаимодействие с holographic</span><span class="sxs-lookup"><span data-stu-id="a3fca-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Снимок экрана: окно "Параметры проекта" открыто в редакторе Unity с выделенным разделом параметров проигрывателя](images/wmr-config-img-9.png)