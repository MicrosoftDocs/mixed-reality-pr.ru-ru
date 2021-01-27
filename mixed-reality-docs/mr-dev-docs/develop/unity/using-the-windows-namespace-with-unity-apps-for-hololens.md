---
title: API-интерфейсы WinRT с Unity для HoloLens
description: Использование API-интерфейсов WinRT и пространства имен Windows в проектах Unity Mixed Reality для HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, пошаговое руководство, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, интерфейсы API смешанной реальности
ms.openlocfilehash: cf80eff408b54c610c9e7878ccfa5185b3fbcca1
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2021
ms.locfileid: "98809992"
---
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="8dcff-104">API-интерфейсы WinRT с Unity для HoloLens</span><span class="sxs-lookup"><span data-stu-id="8dcff-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="8dcff-105">На этой странице описывается, как использовать API-интерфейсы WinRT в проекте Unity для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8dcff-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="8dcff-106">Интерфейсы API смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="8dcff-106">Mixed Reality APIs</span></span>

<span data-ttu-id="8dcff-107">Подмножество Windows SDK, сосредоточенное на смешанной реальности, было доступно в проекции, совместимой с .NET Standard 2,0, которую можно использовать в проекте без директив препроцессора.</span><span class="sxs-lookup"><span data-stu-id="8dcff-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="8dcff-108">Большинство интерфейсов API в Windows.</span><span class="sxs-lookup"><span data-stu-id="8dcff-108">Most APIs in the Windows.</span></span> <span data-ttu-id="8dcff-109">В будущем включены восприятие и Windows. UI. input. пространственные пространства имен. их можно расширить, чтобы включить дополнительные API.</span><span class="sxs-lookup"><span data-stu-id="8dcff-109">Perception and Windows.UI.Input.Spatial namespaces are included and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="8dcff-110">Планируемые API-интерфейсы можно использовать во время работы в редакторе, что позволяет использовать [режим воспроизведения](/windows/mixed-reality/unity-play-mode).</span><span class="sxs-lookup"><span data-stu-id="8dcff-110">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](/windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="8dcff-111">Чтобы использовать эту проекцию, внесите в проект следующие изменения:</span><span class="sxs-lookup"><span data-stu-id="8dcff-111">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="8dcff-112">Добавьте ссылку на пакет NuGet [Microsoft. Windows. микседреалити. дотнетвинрт](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) с помощью [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="8dcff-112">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="8dcff-113">Префикс ссылается на `Windows` пространство имен с помощью `Microsoft.` :</span><span class="sxs-lookup"><span data-stu-id="8dcff-113">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="8dcff-114">Замените приведение собственных указателей на `FromNativePtr` :</span><span class="sxs-lookup"><span data-stu-id="8dcff-114">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="8dcff-115">Условно включить вызовы API WinRT</span><span class="sxs-lookup"><span data-stu-id="8dcff-115">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="8dcff-116">Вы также можете использовать API-интерфейсы WinRT в проектах Unity, созданных для универсальная платформа Windows и платформы Xbox с помощью директив препроцессора.</span><span class="sxs-lookup"><span data-stu-id="8dcff-116">You can also use the WinRT APIs in Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives.</span></span> <span data-ttu-id="8dcff-117">Любой код, написанный в скриптах Unity, предназначенных для API-интерфейсов WinRT, должен включаться в условия только для этих сборок.</span><span class="sxs-lookup"><span data-stu-id="8dcff-117">Any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="8dcff-118">Это можно сделать с помощью двух шагов в Unity:</span><span class="sxs-lookup"><span data-stu-id="8dcff-118">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="8dcff-119">Уровень совместимости API должен иметь значение **.net 4,6** или **.NET Standard 2,0** в параметрах проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="8dcff-119">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="8dcff-120">**Изменить**  >  **Параметры проекта**  >  **Проигрыватель**  >  **Конфигурация**  >  **Уровень совместимости API** для **.net 4,6** или **.NET Standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="8dcff-120">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="8dcff-121">Директива препроцессора **ENABLE_WINMD_SUPPORT** должна быть заключена в оболочку любого кода, использующего WinRT</span><span class="sxs-lookup"><span data-stu-id="8dcff-121">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="8dcff-122">Следующий фрагмент кода находится на странице ручного письма Unity для [универсальная платформа Windows: WINRT API в скриптах C#](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="8dcff-122">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="8dcff-123">В этом примере возвращается идентификатор объявления, но только для UWP и одной сборки Xbox:</span><span class="sxs-lookup"><span data-stu-id="8dcff-123">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="8dcff-124">Редактирование скриптов в проекте C# для Unity</span><span class="sxs-lookup"><span data-stu-id="8dcff-124">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="8dcff-125">При двойном щелчке скрипта в редакторе Unity он по умолчанию запускает скрипт в проекте редактора.</span><span class="sxs-lookup"><span data-stu-id="8dcff-125">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="8dcff-126">Интерфейсы API WinRT будут неизвестны, так как проект Visual Studio не ссылается на среда выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="8dcff-126">The WinRT APIs will appear to be unknown because the Visual Studio project doesn't reference the Windows Runtime.</span></span> <span data-ttu-id="8dcff-127">Директива **ENABLE_WINMD_SUPPORT** не определена, и любой переданный *#if* код пропускается до тех пор, пока проект не будет построен в решении Visual Studio UWP.</span><span class="sxs-lookup"><span data-stu-id="8dcff-127">The **ENABLE_WINMD_SUPPORT** directive is undefined and any *#if* wrapped code is ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="8dcff-128">См. также</span><span class="sxs-lookup"><span data-stu-id="8dcff-128">See also</span></span>
* [<span data-ttu-id="8dcff-129">Экспорт и разработка решения Visual Studio для Unity</span><span class="sxs-lookup"><span data-stu-id="8dcff-129">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="8dcff-130">среда выполнения Windows поддержки Unity</span><span class="sxs-lookup"><span data-stu-id="8dcff-130">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)