---
title: Устранение неполадок с OpenXR
description: Найдите ресурсы и ответы на распространенные проблемы, связанные с устранением неполадок в приложениях Windows Mixed Reality Опенкср.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя, устранение неполадок
ms.openlocfilehash: 6e1696bca4f31f70af10c32087400ed56efa3c11
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006734"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="3cc1a-104">Устранение неполадок с OpenXR</span><span class="sxs-lookup"><span data-stu-id="3cc1a-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="3cc1a-105">Ниже приведены некоторые советы по устранению неполадок при разработке приложения Опенкср с использованием среды выполнения Опенкср Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3cc1a-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="3cc1a-106">Если у вас есть вопросы о <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">спецификации опенкср 1,0</a>, посетите <a href="https://community.khronos.org/c/openxr" target="_blank">форумы Кхронос опенкср</a> или <a href="https://khr.io/slack" target="_blank">резервный #openxr канал</a>.</span><span class="sxs-lookup"><span data-stu-id="3cc1a-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="3cc1a-107">Существуют известные проблемы в текущей среде выполнения Windows Mixed Reality Опенкср с приложениями x86.</span><span class="sxs-lookup"><span data-stu-id="3cc1a-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="3cc1a-108">В данный момент следует создать классические приложения Опенкср для x64.</span><span class="sxs-lookup"><span data-stu-id="3cc1a-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="3cc1a-109">Приложение Опенкср не запускает Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3cc1a-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="3cc1a-110">Если приложение Опенкср не запускает Windows Mixed Reality при запуске, то среда выполнения Windows Mixed Reality Опенкср может быть не установлена в качестве активной среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="3cc1a-110">If your OpenXR app isn't starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span> <span data-ttu-id="3cc1a-111">Чтобы устранить эту проблему, следуйте инструкциям по [началу работы с опенкср для головных телефонов Windows Mixed Reality](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) .</span><span class="sxs-lookup"><span data-stu-id="3cc1a-111">Follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to fix the issue.</span></span>

<span data-ttu-id="3cc1a-112">Вы также можете запустить [средства для разработчиков опенкср для Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) , чтобы получить справку по устранению неполадок в состоянии систем среды выполнения Windows Mixed Reality опенкср.</span><span class="sxs-lookup"><span data-stu-id="3cc1a-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) to get troubleshooting help on the state of your systems Windows Mixed Reality OpenXR Runtime.</span></span>