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
# <a name="winrt-apis-with-unity-for-hololens"></a>API-интерфейсы WinRT с Unity для HoloLens

На этой странице описывается, как использовать API-интерфейсы WinRT в проекте Unity для HoloLens.

## <a name="mixed-reality-apis"></a>Интерфейсы API смешанной реальности

Подмножество Windows SDK, сосредоточенное на смешанной реальности, было доступно в проекции, совместимой с .NET Standard 2,0, которую можно использовать в проекте без директив препроцессора. Большинство интерфейсов API в Windows. В будущем включены восприятие и Windows. UI. input. пространственные пространства имен. их можно расширить, чтобы включить дополнительные API. Планируемые API-интерфейсы можно использовать во время работы в редакторе, что позволяет использовать [режим воспроизведения](/windows/mixed-reality/unity-play-mode). Чтобы использовать эту проекцию, внесите в проект следующие изменения:

1) Добавьте ссылку на пакет NuGet [Microsoft. Windows. микседреалити. дотнетвинрт](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) с помощью [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity).
2) Префикс ссылается на `Windows` пространство имен с помощью `Microsoft.` :
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Замените приведение собственных указателей на `FromNativePtr` :
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Условно включить вызовы API WinRT

Вы также можете использовать API-интерфейсы WinRT в проектах Unity, созданных для универсальная платформа Windows и платформы Xbox с помощью директив препроцессора. Любой код, написанный в скриптах Unity, предназначенных для API-интерфейсов WinRT, должен включаться в условия только для этих сборок. 

Это можно сделать с помощью двух шагов в Unity:
1) Уровень совместимости API должен иметь значение **.net 4,6** или **.NET Standard 2,0** в параметрах проигрывателя.
    - **Изменить**  >  **Параметры проекта**  >  **Проигрыватель**  >  **Конфигурация**  >  **Уровень совместимости API** для **.net 4,6** или **.NET Standard 2,0**
2) Директива препроцессора **ENABLE_WINMD_SUPPORT** должна быть заключена в оболочку любого кода, использующего WinRT

Следующий фрагмент кода находится на странице ручного письма Unity для [универсальная платформа Windows: WINRT API в скриптах C#](https://docs.unity3d.com/Manual/windowsstore-scripts.html). В этом примере возвращается идентификатор объявления, но только для UWP и одной сборки Xbox:

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Редактирование скриптов в проекте C# для Unity

При двойном щелчке скрипта в редакторе Unity он по умолчанию запускает скрипт в проекте редактора. Интерфейсы API WinRT будут неизвестны, так как проект Visual Studio не ссылается на среда выполнения Windows. Директива **ENABLE_WINMD_SUPPORT** не определена, и любой переданный *#if* код пропускается до тех пор, пока проект не будет построен в решении Visual Studio UWP.

## <a name="see-also"></a>См. также
* [Экспорт и разработка решения Visual Studio для Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [среда выполнения Windows поддержки Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)