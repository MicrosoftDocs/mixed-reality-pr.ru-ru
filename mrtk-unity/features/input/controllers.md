---
title: Контроллеры
description: Использование контроллеров в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, контроллеры,
ms.openlocfilehash: ea3dbd11baa669750f3bccc09d6cd7ab3eb7688f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176920"
---
# <a name="controllers"></a><span data-ttu-id="52a79-104">Контроллеры</span><span class="sxs-lookup"><span data-stu-id="52a79-104">Controllers</span></span>

<span data-ttu-id="52a79-105">Контроллеры создаются и уничтожаются автоматически [**поставщиками входных данных**](input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="52a79-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="52a79-106">Каждый тип контроллера имеет ряд *физических входов* , определенных *типом оси*, указывая тип данных входного значения (цифровые, одинарную ось, двойную ось, шесть ДОФ,...) и *тип ввода* (нажатие кнопки, триггер, закрепление, пространственный указатель,...), описывающий источник входных данных.</span><span class="sxs-lookup"><span data-stu-id="52a79-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="52a79-107">физические входные данные сопоставляются с *входными действиями* через **профиль сопоставления входных данных контроллера** в *системном профиле input* набор средств компоненте Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="52a79-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

![Сопоставление входных данных контроллера](../images/input/ControllerInputMapping.png)
