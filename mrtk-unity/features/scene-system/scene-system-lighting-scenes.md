---
title: Система сцен — сцены освещения
description: Документация по освещению в сцене.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 407813f52044d3405e5045f64817d87c4f3e4b59ddfd87308586ac2d81924674
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202572"
---
# <a name="lighting-scene-operations"></a>Операции освещения сцены

Сцена освещения по умолчанию, определенная в профиле, загружается при запуске. Эта сцена освещения остается загруженной до `SetLightingScene` вызова метода.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a>Переходы параметров освещения

`transitionType` управляет стилем перехода к новой сцене освещения.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

Доступны следующие стили:

Тип | Описание | Duration
--- | --- | ---
None | Предыдущая сцена освещения выгружена, будет загружена новая сцена освещения. Нет перехода. | Не учитывается
фадетоблакк | Предыдущая сцена освещения плавно уменьшается до черного цвета. Загружается новая сцена освещения, затем она проявляется черным. Полезно для плавного перехода между расположениями. | Используется
Плавное переход | Предыдущая сцена освещения постепенно исчезает по мере появления новой сцены освещения. Полезно для плавного перехода между настройками освещения в одном и том же расположении. | Используется

Обратите внимание, что некоторые параметры освещения не могут быть интерполяции во время переходов. Если требуется плавное визуальное переход, эти параметры должны оставаться согласованными между сценой освещения.

Параметр | Плавный переход Фадетоблакк | Плавный плавный переход
--- | --- | ---
скибокс | Нет | Нет
Пользовательские отражения | Нет | Нет
Тени в режиме реального времени Sun | Да | Нет
