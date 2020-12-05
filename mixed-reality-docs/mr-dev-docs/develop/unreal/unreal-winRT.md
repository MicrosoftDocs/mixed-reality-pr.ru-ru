---
title: WinRT в Unreal
description: Общие сведения о подключаемом модуле пространственного звука для Unreal Engine.
author: hferrone
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Нереал, нереалистичный механизм 4, UE4, HoloLens, HoloLens 2, потоковая передача, удаленное взаимодействие, Смешанная реальность, разработка, начало работы, функции, новый проект, эмулятор, документация, руководства, функции, голограммы, Разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, WinRT, DLL
ms.openlocfilehash: f9001f3a9e36eb5d8553545f38cf10411bafd64b
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609414"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="7b38a-104">WinRT в Unreal</span><span class="sxs-lookup"><span data-stu-id="7b38a-104">WinRT in Unreal</span></span>

<span data-ttu-id="7b38a-105">В процессе разработки HoloLens может потребоваться написать функцию с помощью WinRT.</span><span class="sxs-lookup"><span data-stu-id="7b38a-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="7b38a-106">Например, для открытия диалогового окна файла в приложении HoloLens потребуется Филесавепиккер в файле заголовка WinRT/Windows. Storage.. h.</span><span class="sxs-lookup"><span data-stu-id="7b38a-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="7b38a-107">Среда WinRT поддерживается в системе сборки нереального времени с версии 4,26.</span><span class="sxs-lookup"><span data-stu-id="7b38a-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="7b38a-108">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="7b38a-108">Next Development Checkpoint</span></span>

<span data-ttu-id="7b38a-109">Если вы подготовились к нереальному пути разработки, мы собрались изучить возможности и API платформы смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="7b38a-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="7b38a-110">Здесь можно перейти к любому [разделу](unreal-development-overview.md#3-platform-capabilities-and-apis) или перейти непосредственно к развертыванию приложения на устройстве или в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="7b38a-110">From here, you can continue to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7b38a-111">Развертывание на устройстве</span><span class="sxs-lookup"><span data-stu-id="7b38a-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="7b38a-112">См. также</span><span class="sxs-lookup"><span data-stu-id="7b38a-112">See also</span></span>
* [<span data-ttu-id="7b38a-113">API-интерфейсы/WinRT C++</span><span class="sxs-lookup"><span data-stu-id="7b38a-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="7b38a-114">Класс Филесавепиккер</span><span class="sxs-lookup"><span data-stu-id="7b38a-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="7b38a-115">Нереал. сторонние библиотеки</span><span class="sxs-lookup"><span data-stu-id="7b38a-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
