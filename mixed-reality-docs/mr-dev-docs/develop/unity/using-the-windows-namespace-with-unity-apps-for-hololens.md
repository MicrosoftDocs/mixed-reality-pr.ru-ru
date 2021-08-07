---
title: API-интерфейсы WinRT с Unity для HoloLens
description: использование api-интерфейсов WinRT и пространства имен Windows в проектах Unity mixed reality для HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, пошаговое руководство, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, интерфейсы API смешанной реальности
ms.openlocfilehash: 158c28d9186269108442226bbfcfc90a3c235a71336fdab9dbf9eadc21a309a1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215610"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>API-интерфейсы WinRT с Unity для HoloLens

На этой странице описано, как использовать API-интерфейсы WinRT в проекте Unity для HoloLens.

## <a name="mixed-reality-apis"></a>Интерфейсы API смешанной реальности

подмножество Windows SDK, сосредоточенное на смешанной реальности, было доступно в проекции, совместимой с .NET Standard 2,0, которую можно использовать в проекте без директив препроцессора. Большинство интерфейсов API в Windows. Восприятие и Windows. Интерфейса. Входные и пространственные пространства имен включены и могут расширяться для включения дополнительных API в будущем. Планируемые API-интерфейсы можно использовать во время работы в редакторе, что позволяет использовать [режим воспроизведения](/windows/mixed-reality/unity-play-mode). Чтобы использовать эту проекцию, внесите в проект следующие изменения:

1) Добавьте ссылку на [Microsoft. Windows. микседреалити. дотнетвинрт](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet пакет с использованием [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity).
2) Префикс ссылается на `Windows` пространство имен с помощью `Microsoft.` :
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Замените приведение собственных указателей на `FromNativePtr` :
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Условно включить вызовы API WinRT

вы также можете использовать api-интерфейсы WinRT в проектах Unity, созданных для платформы универсальная платформа Windows и Xbox One, используя директивы препроцессора. Любой код, написанный в скриптах Unity, предназначенных для API-интерфейсов WinRT, должен включаться в условия только для этих сборок. 

Это можно сделать с помощью двух шагов в Unity:
1) Уровень совместимости API должен иметь значение **.net 4,6** или **.NET Standard 2,0** в параметрах проигрывателя.
    - **Изменить**  >  **Project Параметры**  >  **Проигрыватель**  >  **Конфигурация**  >  **Уровень совместимости API** для **.net 4,6** или **.NET Standard 2,0**
2) Директива препроцессора **ENABLE_WINMD_SUPPORT** должна быть заключена в оболочку любого кода, использующего WinRT

следующий фрагмент кода находится на странице ручного письма Unity для [универсальная платформа Windows: WinRT API в скриптах C#](https://docs.unity3d.com/Manual/windowsstore-scripts.html). в этом примере возвращается идентификатор объявления, но только для сборок UWP и Xbox One:

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

При двойном щелчке скрипта в редакторе Unity он по умолчанию запускает скрипт в проекте редактора. интерфейсы api WinRT будут неизвестны, так как проект Visual Studio не ссылается на среда выполнения Windows. директива **ENABLE_WINMD_SUPPORT** не определена, и любой переданный *#if* код пропускается до тех пор, пока проект не будет построен в решении Visual Studio UWP.

## <a name="see-also"></a>См. также раздел
* [Экспорт и разработка решения Visual Studio для Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows Поддержка среды выполнения Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)