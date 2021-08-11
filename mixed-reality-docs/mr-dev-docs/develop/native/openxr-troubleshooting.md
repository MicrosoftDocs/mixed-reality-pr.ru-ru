---
title: Устранение неполадок с OpenXR
description: найдите ресурсы и ответы на распространенные проблемы устранения неполадок в приложениях Windows Mixed Reality опенкср.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя, устранение неполадок
ms.openlocfilehash: 456dcf927c70aaaebc8dda1338d24acc910a1e801cf29e8880048d44f9432718
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219208"
---
# <a name="openxr-troubleshooting"></a>Устранение неполадок с OpenXR

ниже приведены некоторые советы по устранению неполадок при разработке приложения опенкср с помощью среды выполнения Windows Mixed Reality опенкср.  Если у вас есть вопросы о <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">спецификации опенкср 1,0</a>, посетите <a href="https://community.khronos.org/c/openxr" target="_blank">форумы Кхронос опенкср</a> или <a href="https://khr.io/slack" target="_blank">резервный #openxr канал</a>.

>[!NOTE]
>в текущей Windows Mixed Reality среды выполнения опенкср с приложениями x86 существуют известные проблемы.  В данный момент следует создать классические приложения Опенкср для x64.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Приложение Опенкср не запускается Windows Mixed Reality

если приложение опенкср не запускается Windows Mixed Reality при его запуске, среда выполнения Windows Mixed Reality опенкср может быть не установлена в качестве активной среды выполнения. чтобы устранить эту проблему, следуйте инструкциям по [началу работы с опенкср для Windows Mixed Reality гарнитуры](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) .

вы также можете запустить [Средства для разработчиков опенкср для Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) , чтобы получить справку по устранению неполадок в состоянии систем Windows Mixed Reality среды выполнения опенкср.