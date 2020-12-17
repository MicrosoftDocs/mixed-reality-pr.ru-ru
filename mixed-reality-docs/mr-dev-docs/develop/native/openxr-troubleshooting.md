---
title: Устранение неполадок с OpenXR
description: Устранение неполадок в приложениях Опенкср.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя, устранение неполадок
ms.openlocfilehash: ddfe548d689d84576ad0ac06bda46d7c2757859c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612938"
---
# <a name="openxr-troubleshooting"></a>Устранение неполадок с OpenXR

Ниже приведены некоторые советы по устранению неполадок при разработке приложения Опенкср с использованием среды выполнения Опенкср Windows Mixed Reality.  Если у вас есть вопросы о <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">спецификации опенкср 1,0</a>, посетите <a href="https://community.khronos.org/c/openxr" target="_blank">форумы Кхронос опенкср</a> или <a href="https://khr.io/slack" target="_blank">резервный #openxr канал</a>.

>[!NOTE]
>Существуют известные проблемы в текущей среде выполнения Windows Mixed Reality Опенкср с приложениями x86.  В данный момент следует создать классические приложения Опенкср для x64.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Приложение Опенкср не запускает Windows Mixed Reality

Если приложение Опенкср не запускает Windows Mixed Reality при запуске, то среда выполнения Windows Mixed Reality Опенкср может быть не установлена в качестве активной среды выполнения. Чтобы устранить эту проблему, следуйте инструкциям по [началу работы с опенкср для головных телефонов Windows Mixed Reality](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) .

Вы также можете запустить [средства для разработчиков опенкср для Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) , чтобы получить справку по устранению неполадок в состоянии систем среды выполнения Windows Mixed Reality опенкср.