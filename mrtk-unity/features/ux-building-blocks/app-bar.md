---
title: Панель приложения
description: Общие сведения о панели приложений в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, панель приложений,
ms.openlocfilehash: 1ecb43d25a4353ff4c3bd8350efaab877900a5b979cd42d2c8d1cb91ce32ae0c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198281"
---
# <a name="app-bar"></a>Панель приложения

![Панель приложения](../images/app-bar/MRTK_AppBar_Main.png)

Панель приложений — это компонент пользовательского интерфейса, который используется вместе с сценарием [элемента управления Bounds](bounds-control.md) . Он добавляет элементы управления "Кнопка" в объект с намерением управлять им. С помощью кнопки "настроить" можно отменить или активировать интерфейс управления границами для объекта. Кнопка "Удалить" должна удалить объект из сцены.

## <a name="how-to-use-app-bar"></a>Использование панели приложений

Перетащите `AppBar` (Assets/мртк/SDK/Features/UX/Prefabs/панель приложений/панель приложений. prefab) в иерархию сцены. На панели инспектора компонента назначьте любой объект с элементом управления Bounds в качестве *целевого ограничивающего прямоугольника* , чтобы добавить в него панель приложений.

**Важно.** Параметр активации элемента управления boundss для целевого объекта должен иметь значение "активировать вручную".

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
