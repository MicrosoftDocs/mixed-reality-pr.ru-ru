---
title: MRTK и удаление управляемого кода
description: Удаление кода в МРТК и Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 4348adf1d9cb2e7fc74cf5258e3272baaac96a5fc34565873cf35ae93225bdbe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221874"
---
# <a name="mrtk-and-managed-code-stripping"></a>MRTK и удаление управляемого кода

При использовании серверной части скриптов IL2CPP для Unity (необязательно в Unity 2018,4, обязательное в 2019 и более поздних версиях) происходит удаление [управляемого кода](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) .
Компоновщик Unity выполняет этот процесс для уменьшения двоичного размера, а также для уменьшения времени сборки.

набор средств смешанной реальности использует файл, `link.xml` чтобы влиять на то, как компоновщик Unity обрабатывает сборки мртк. Этот файл, описанный в [документации Unity](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), содержит инструкции по сохранению кода, когда его использование не может быть определено (например, используется через отражение).

Как гибкая и настраиваемая платформа, МРТК создает `link.xml` файл в при `Assets/MixedRealityToolkit.Generated` импорте, если он найден, если он не существует. Существовавшие ранее файлы link.xml не перезаписываются. Его рекомендуется `link.xml` `link.xml.meta` Добавить в систему управления версиями. Разработчики должны иметь возможность настроить `Assets/MixedRealityToolkit.Generated/link.xml` в соответствии с потребностями проекта.

По умолчанию файл link.xml, созданный МРТК, сохраняет все сборки, показанные в следующих данных.

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

Дополнительные сведения о link.xml формате файлов см. в документации по Unity.

## <a name="see-also"></a>См. также раздел

- [Unity: обрезает управляемый код](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity: компоновка XML-файла](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
