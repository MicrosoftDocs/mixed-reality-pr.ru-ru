---
title: Настройка конфигурации смешанной реальности
description: оставайтесь в курсе последних рекомендаций по конфигурации Unity XR для разработки приложений HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: микседреалититулкит, микседреалититулкит-Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603730"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="f0a50-104">Настройка конфигурации смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="f0a50-104">Setting up your XR configuration</span></span>

<span data-ttu-id="f0a50-105">После [выбора версии Unity](choosing-unity-version.md)необходимо выбрать конфигурацию XR, которая будет использоваться для создания приложения смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="f0a50-105">Once you've [chosen a Unity version](choosing-unity-version.md), the next step is to select the XR configuration you'll use to build your mixed reality app:</span></span>

## <a name="choosing-an-xr-configuration"></a><span data-ttu-id="f0a50-106">Выбор конфигурации XR</span><span class="sxs-lookup"><span data-stu-id="f0a50-106">Choosing an XR configuration</span></span>

<span data-ttu-id="f0a50-107">при запуске нового проекта Unity вы можете выбрать различные конфигурации XR: **подключаемый модуль Mixed Reality опенкср**, **подключаемый модуль Windows XR** и **устаревший встроенный XR**.</span><span class="sxs-lookup"><span data-stu-id="f0a50-107">When you start a new Unity project, you have various XR configurations you can select from: the **Mixed Reality OpenXR plugin**, the **Windows XR plugin** and **Legacy Built-in XR**.</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="f0a50-108">Настройка проекта с помощью МРТК</span><span class="sxs-lookup"><span data-stu-id="f0a50-108">Setting up your project with MRTK</span></span>

<span data-ttu-id="f0a50-109">самый простой способ сделать так, чтобы проект Unity был настроен для смешанной реальности, — с набор средств смешанной реальности (мртк).</span><span class="sxs-lookup"><span data-stu-id="f0a50-109">The easiest way to get your Unity project set up for mixed reality is with the Mixed Reality Toolkit (MRTK).</span></span>  <span data-ttu-id="f0a50-110">МРТК для Unity — это многоплатформенный пакет средств разработки, разработанный с открытым исходным кодом, предназначенный для облегчения создания невероятных приложений в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="f0a50-110">MRTK for Unity is an open-source, cross-platform development kit designed to make it easy to build amazing mixed reality applications.</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="f0a50-112">MRTK предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="f0a50-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span>  <span data-ttu-id="f0a50-113">с помощью мртк версии 2 можно ускорить разработку приложений для Microsoft HoloLens, Windows Mixed Realityных головных телефонов (vr) и многих других устройств vr/AR.</span><span class="sxs-lookup"><span data-stu-id="f0a50-113">With MRTK version 2, you can speed up your application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and many other VR/AR devices.</span></span> <span data-ttu-id="f0a50-114">Проект предназначен для уменьшения барьеров, позволяя любому пользователю создавать приложения смешанной реальности и участвовать в сообществе по мере роста.</span><span class="sxs-lookup"><span data-stu-id="f0a50-114">The project is aimed at reducing barriers to entry, enabling everyone to build mixed reality applications and contribute back to the community as we all grow.</span></span>

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

<span data-ttu-id="f0a50-115">чтобы узнать больше о набор средств смешанной реальности, ознакомьтесь с [документацией по мртк](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="f0a50-115">To learn more about the Mixed Reality Toolkit, check out the [MRTK documentation](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="f0a50-116">Настройка вручную без МРТК</span><span class="sxs-lookup"><span data-stu-id="f0a50-116">Manual setup without MRTK</span></span>

<span data-ttu-id="f0a50-117">хотя корпорация майкрософт и сообщество создали средства с открытым кодом, такие как [смешанная реальность набор средств (мртк)](/windows/mixed-reality/mrtk-unity) , которая автоматически настраивает среду для смешанной реальности, некоторым разработчикам может потребоваться создать свои впечатления с нуля.</span><span class="sxs-lookup"><span data-stu-id="f0a50-117">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) that will automatically set up your environment for mixed reality, some developers may wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]