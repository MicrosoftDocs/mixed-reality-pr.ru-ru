---
title: MRTK и удаление управляемого кода
description: Удаление кода в МРТК и Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 09e5140fd9585c19eacac5ba937eaf4ea8f2a8ea
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143738"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a><span data-ttu-id="58a1a-104">Удаление управляемого кода МРТК и Unity</span><span class="sxs-lookup"><span data-stu-id="58a1a-104">MRTK and Unity managed code stripping</span></span>

<span data-ttu-id="58a1a-105">При использовании серверной части скриптов IL2CPP для Unity (необязательно в Unity 2018,4, обязательное в 2019 и более поздних версиях) происходит удаление [управляемого кода](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) .</span><span class="sxs-lookup"><span data-stu-id="58a1a-105">When using Unity's IL2CPP scripting backend (optional in Unity 2018.4, required in 2019 and newer), [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) occurs.</span></span>
<span data-ttu-id="58a1a-106">Компоновщик Unity выполняет этот процесс для уменьшения двоичного размера, а также для уменьшения времени сборки.</span><span class="sxs-lookup"><span data-stu-id="58a1a-106">Unity's linker performs this process to reduce binary size as well as to decrease build times.</span></span>

<span data-ttu-id="58a1a-107">Набор средств Mixed Reality использует файл, `link.xml` чтобы влиять на то, как компоновщик Unity обрабатывает сборки мртк.</span><span class="sxs-lookup"><span data-stu-id="58a1a-107">The Mixed Reality Toolkit uses a file, `link.xml`, to influence how Unity's linker processes MRTK assemblies.</span></span> <span data-ttu-id="58a1a-108">Этот файл, описанный в [документации Unity](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), содержит инструкции по сохранению кода, когда его использование не может быть определено (например, используется через отражение).</span><span class="sxs-lookup"><span data-stu-id="58a1a-108">This file, described in full in [Unity's documentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), provides the linker with instructions on how to preserve code when its usage cannot be inferred (ex: used via reflection).</span></span>

<span data-ttu-id="58a1a-109">Как гибкая и настраиваемая платформа, МРТК создает `link.xml` файл в при `Assets/MixedRealityToolkit.Generated` импорте, если он найден, если он не существует.</span><span class="sxs-lookup"><span data-stu-id="58a1a-109">As a flexible and customizable platform, MRTK creates the `link.xml` file in `Assets/MixedRealityToolkit.Generated` on import, if it is found to not exist.</span></span> <span data-ttu-id="58a1a-110">Существовавшие ранее файлы link.xml не перезаписываются.</span><span class="sxs-lookup"><span data-stu-id="58a1a-110">Pre-existing link.xml files are not overwritten.</span></span> <span data-ttu-id="58a1a-111">Его рекомендуется `link.xml` `link.xml.meta` Добавить в систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="58a1a-111">It is recommended that `link.xml` and `link.xml.meta` be added to version control.</span></span> <span data-ttu-id="58a1a-112">Разработчики должны иметь возможность настроить `Assets/MixedRealityToolkit.Generated/link.xml` в соответствии с потребностями проекта.</span><span class="sxs-lookup"><span data-stu-id="58a1a-112">Developers should feel free to customize `Assets/MixedRealityToolkit.Generated/link.xml` to meet the needs of the project.</span></span>

<span data-ttu-id="58a1a-113">По умолчанию файл link.xml, созданный МРТК, сохраняет все сборки, показанные в следующих данных.</span><span class="sxs-lookup"><span data-stu-id="58a1a-113">By default, the link.xml file created by MRTK preserves the entirety of the assemblies shown in the following data.</span></span>

``` xml
<linker> 
  <!-- 
    This link.xml file is provided to prevent MRTK code from being optimized away 
    during IL2CPP builds.More details on when this is needed and why this is needed 
    can be found here: https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5273 
    If your application doesn't use some specific services (for example, if teleportation system is 
    disabled in the profile), it is possible to remove their corresponding lines down 
    below(in the previous example, we would remove the TeleportSystem below). 
    It's recommended to start with this list and narrow down if you want to ensure 
    specific bits of code get optimized away. 
  --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.SDK" preserve="all"/> 
  <!-- Core systems --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.BoundarySystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.CameraSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.InputSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SceneSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.TeleportSystem" preserve="all"/> 
  <!-- Data providers --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.LeapMotion" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenVR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.UnityAR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.Shared" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK" preserve="all"/> 
  <!-- Extension services --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.HandPhysics" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.Tracking" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.SceneTransitionService" preserve="all"/> 
</linker>
```

<span data-ttu-id="58a1a-114">Дополнительные сведения о link.xml формате файлов см. в документации по Unity.</span><span class="sxs-lookup"><span data-stu-id="58a1a-114">For more information on the link.xml file format, please refer to the Unity documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="58a1a-115">См. также</span><span class="sxs-lookup"><span data-stu-id="58a1a-115">See also</span></span>

- [<span data-ttu-id="58a1a-116">Unity: обрезает управляемый код</span><span class="sxs-lookup"><span data-stu-id="58a1a-116">Unity: Managed Code Stripping</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [<span data-ttu-id="58a1a-117">Unity: компоновка XML-файла</span><span class="sxs-lookup"><span data-stu-id="58a1a-117">Unity: Link XML file</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
