---
title: Контроллеры
description: Использование контроллеров в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, контроллеры,
ms.openlocfilehash: c92ad099d770cc52467918053af02e7bebab928d
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850340"
---
# <a name="controllers"></a><span data-ttu-id="82797-104">Контроллеры</span><span class="sxs-lookup"><span data-stu-id="82797-104">Controllers</span></span>

<span data-ttu-id="82797-105">Контроллеры создаются и уничтожаются автоматически [**поставщиками входных данных**](input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="82797-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="82797-106">Каждый тип контроллера имеет ряд *физических входов* , определенных *типом оси*, указывая тип данных входного значения (цифровые, одинарную ось, двойную ось, шесть ДОФ,...) и *тип ввода* (нажатие кнопки, триггер, закрепление, пространственный указатель,...), описывающий источник входных данных.</span><span class="sxs-lookup"><span data-stu-id="82797-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="82797-107">Физические входные данные сопоставлены с *входными действиями* через **профиль сопоставления входных данных контроллера** в *системном профиле входных* данных в компоненте набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="82797-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

<span data-ttu-id="82797-108">МРТК будет автоматически обнаруживать контроллеры ВМР и отображать их при установке пакета [**Microsoft. микседреалити. Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) .</span><span class="sxs-lookup"><span data-stu-id="82797-108">MRTK will automatically detect WMR controllers and display them when the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package is installed.</span></span> <span data-ttu-id="82797-109">Модели контроллеров отображаются в редакторе только при использовании конвейера Опенкср.</span><span class="sxs-lookup"><span data-stu-id="82797-109">Controllers models will only show up in the editor when using the OpenXR pipeline.</span></span> <span data-ttu-id="82797-110">Для визуализации моделей контроллеров Окулус следуйте инструкциям по [развертыванию Окулус Quest](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md) .</span><span class="sxs-lookup"><span data-stu-id="82797-110">To visualize Oculus controller models, follow the [Oculus Quest deployment instructions](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span></span>

![Сопоставление входных данных контроллера](../images/input/ControllerInputMapping.png)