---
title: WinRT в Unreal
description: Общие сведения о подключаемом модуле пространственного звука для Unreal Engine.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Нереал, нереалистичный механизм 4, UE4, HoloLens, HoloLens 2, потоковая передача, удаленное взаимодействие, Смешанная реальность, разработка, начало работы, функции, новый проект, эмулятор, документация, руководства, функции, голограммы, Разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, WinRT, DLL
ms.openlocfilehash: 722add1601013d206ffface84d3a53cf3a9d89f9
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354451"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="92f92-104">WinRT в Unreal</span><span class="sxs-lookup"><span data-stu-id="92f92-104">WinRT in Unreal</span></span>

<span data-ttu-id="92f92-105">В процессе разработки HoloLens может потребоваться написать функцию с помощью WinRT.</span><span class="sxs-lookup"><span data-stu-id="92f92-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="92f92-106">Например, для открытия диалогового окна файла в приложении HoloLens потребуется Филесавепиккер в файле заголовка WinRT/Windows. Storage.. h.</span><span class="sxs-lookup"><span data-stu-id="92f92-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="92f92-107">Среда WinRT поддерживается в системе сборки нереального времени с версии 4,26.</span><span class="sxs-lookup"><span data-stu-id="92f92-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="92f92-108">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="92f92-108">Next Development Checkpoint</span></span>

<span data-ttu-id="92f92-109">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении возможностей и API платформы смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="92f92-109">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="92f92-110">Здесь можно перейти к любому [разделу](unreal-development-overview.md#3-platform-capabilities-and-apis) или перейти непосредственно к развертыванию приложения на устройстве или в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="92f92-110">From here, you can proceed to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="92f92-111">Развертывание на устройстве</span><span class="sxs-lookup"><span data-stu-id="92f92-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="92f92-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="92f92-112">See also</span></span>
* [<span data-ttu-id="92f92-113">API-интерфейсы/WinRT C++</span><span class="sxs-lookup"><span data-stu-id="92f92-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="92f92-114">Класс Филесавепиккер</span><span class="sxs-lookup"><span data-stu-id="92f92-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="92f92-115">Нереал. сторонние библиотеки</span><span class="sxs-lookup"><span data-stu-id="92f92-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
