---
title: Система сцен — сцены освещения
description: Документация по освещению в сцене.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144410"
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

Тип | Описание: | Duration
--- | --- | ---
None | Предыдущая сцена освещения выгружена, будет загружена новая сцена освещения. Нет перехода. | Не учитывается
фадетоблакк | Предыдущая сцена освещения плавно уменьшается до черного цвета. Загружается новая сцена освещения, затем она проявляется черным. Полезно для плавного перехода между расположениями. | Используется
Плавное переход | Предыдущая сцена освещения постепенно исчезает по мере появления новой сцены освещения. Полезно для плавного перехода между настройками освещения в одном и том же расположении. | Используется

Обратите внимание, что некоторые параметры освещения не могут быть интерполяции во время переходов. Если требуется плавное визуальное переход, эти параметры должны оставаться согласованными между сценой освещения.

Параметр | Плавный переход Фадетоблакк | Плавный плавный переход
--- | --- | ---
скибокс | нет | нет
Пользовательские отражения | нет | нет
Тени в режиме реального времени Sun | Да | нет
