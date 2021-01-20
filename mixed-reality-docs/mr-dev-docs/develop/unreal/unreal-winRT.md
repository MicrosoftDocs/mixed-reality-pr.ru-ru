---
title: WinRT в Unreal
description: Узнайте, как создавать пользовательские функции WinRT и управлять ими в нереальных приложениях Mixed Reality для устройств HoloLens.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Нереал, нереалистичный механизм 4, UE4, HoloLens, HoloLens 2, потоковая передача, удаленное взаимодействие, Смешанная реальность, разработка, начало работы, функции, новый проект, эмулятор, документация, руководства, функции, голограммы, Разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, WinRT, DLL
ms.openlocfilehash: f32b5b3ddbee2e24e61d08b0a1b887b7b06e6da4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580406"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="e20c6-104">WinRT в Unreal</span><span class="sxs-lookup"><span data-stu-id="e20c6-104">WinRT in Unreal</span></span>

<span data-ttu-id="e20c6-105">В процессе разработки HoloLens может потребоваться написать функцию с помощью WinRT.</span><span class="sxs-lookup"><span data-stu-id="e20c6-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="e20c6-106">Например, для открытия диалогового окна файла в приложении HoloLens потребуется Филесавепиккер в файле заголовка WinRT/Windows. Storage.. h.</span><span class="sxs-lookup"><span data-stu-id="e20c6-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="e20c6-107">Среда WinRT поддерживается в системе сборки нереального времени с версии 4,26.</span><span class="sxs-lookup"><span data-stu-id="e20c6-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="e20c6-108">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="e20c6-108">Next Development Checkpoint</span></span>

<span data-ttu-id="e20c6-109">Если вы следуете изложенной нами стратегии разработки для Unreal, вы как раз прошли половину в изучении возможностей и API платформы Смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="e20c6-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="e20c6-110">Здесь можно перейти к любому [разделу](unreal-development-overview.md#3-advanced-features) или перейти непосредственно к развертыванию приложения на устройстве или в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="e20c6-110">From here, you can continue to any [topic](unreal-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e20c6-111">Развертывание на устройстве</span><span class="sxs-lookup"><span data-stu-id="e20c6-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="e20c6-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e20c6-112">See also</span></span>

* [<span data-ttu-id="e20c6-113">API-интерфейсы/WinRT C++</span><span class="sxs-lookup"><span data-stu-id="e20c6-113">C++/WinRT APIs</span></span>](/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="e20c6-114">Класс Филесавепиккер</span><span class="sxs-lookup"><span data-stu-id="e20c6-114">FileSavePicker class</span></span>](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="e20c6-115">Нереал. сторонние библиотеки</span><span class="sxs-lookup"><span data-stu-id="e20c6-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)