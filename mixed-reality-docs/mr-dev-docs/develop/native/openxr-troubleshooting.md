---
title: Устранение неполадок с OpenXR
description: Найдите ресурсы и ответы на распространенные проблемы, связанные с устранением неполадок в приложениях Windows Mixed Reality Опенкср.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя, устранение неполадок
ms.openlocfilehash: 6e1696bca4f31f70af10c32087400ed56efa3c11
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006734"
---
# <a name="openxr-troubleshooting"></a>Устранение неполадок с OpenXR

Ниже приведены некоторые советы по устранению неполадок при разработке приложения Опенкср с использованием среды выполнения Опенкср Windows Mixed Reality.  Если у вас есть вопросы о <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">спецификации опенкср 1,0</a>, посетите <a href="https://community.khronos.org/c/openxr" target="_blank">форумы Кхронос опенкср</a> или <a href="https://khr.io/slack" target="_blank">резервный #openxr канал</a>.

>[!NOTE]
>Существуют известные проблемы в текущей среде выполнения Windows Mixed Reality Опенкср с приложениями x86.  В данный момент следует создать классические приложения Опенкср для x64.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Приложение Опенкср не запускает Windows Mixed Reality

Если приложение Опенкср не запускает Windows Mixed Reality при запуске, то среда выполнения Windows Mixed Reality Опенкср может быть не установлена в качестве активной среды выполнения. Чтобы устранить эту проблему, следуйте инструкциям по [началу работы с опенкср для головных телефонов Windows Mixed Reality](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) .

Вы также можете запустить [средства для разработчиков опенкср для Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) , чтобы получить справку по устранению неполадок в состоянии систем среды выполнения Windows Mixed Reality опенкср.