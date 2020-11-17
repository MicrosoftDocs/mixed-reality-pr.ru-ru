---
title: Обзор разработки для собственной платформы
description: Создайте модуль смешанной реальности на основе DirectX, используя интерфейсы API Windows Mixed Reality напрямую.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, holographic-визуализация, собственное, собственное приложение, WinRT, приложение WinRT, API платформы, настраиваемое ядро, промежуточное по, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 0d5e364fdb4faac73f28649f5c009823a74ac595
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679653"
---
# <a name="native-development-overview"></a>Обзор разработки для собственной платформы

![Эмблема собственного баннера](../images/native_logo_banner.png)

Трехмерные модули, такие как [Unity](../unity/unity-development-overview.md) или [Real](../unreal/unreal-development-overview.md) , не являются открытыми для вас путями к разработке смешанной реальности. Приложения смешанной реальности также можно создавать путем непосредственного программирования на API-интерфейсы Windows Mixed Reality с помощью DirectX 11 или DirectX 12. Используя платформу напрямую, вы сами создаете собственное по промежуточного слоя или платформу. 

> [!IMPORTANT]
> Если у вас есть проект WinRT, который вы хотите поддерживать, перейдите к нашей основной [документации по WinRT](creating-a-holographic-directx-project.md). 

## <a name="development-checkpoints"></a>Этапы разработки

Используйте следующие контрольные точки, чтобы реализовать свои игры и приложения Unity в мире смешанной реальности.

### <a name="1-getting-started"></a>1. Начало работы

Windows Mixed Reality поддерживает [два типа приложений](../../design/app-views.md):
* **Приложения смешанной реальности** (UWP или Win32), использующие [API Холографикспаце](getting-a-holographicspace.md) или [API опенкср](openxr.md) для визуализации [иммерсивного представления](../../design/app-views.md) пользователю, заполняющему отображение гарнитуры
* **2D-приложения** (UWP), использующие DirectX, XAML или другую платформу для отрисовки [2D-представлений](../../design/app-views.md#2d-views) на планшетах в домашней среде Windows Mixed Reality

Различия между разработкой DirectX для [2D-представлений и иммерсивное представление](../../design/app-views.md) в основном связаны с более holographic и пространственными входными данными. [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) приложения UWP или HWND приложения Win32 являются обязательными и остаются в основном одинаковыми. Это справедливо и для API-интерфейсов WinRT, доступных для приложения. Однако для использования преимуществ holographic необходимо использовать другое подмножество этих API-интерфейсов. Например, имеющуюся цепочку буферов и Frame находятся под управлением системы для holographic приложений с целью включения циклического цикла кадров.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Основные компоненты

Приложения Windows Mixed Reality используют следующие API для создания [смешанных](../../discover/mixed-reality.md) возможностей для HoloLens и других впечатляющих головных телефонов:

|  Компонент  |  Возможностями.  |
| --- | --- |
| [Взгляд](../../design/gaze-and-commit.md) | Предоставление пользователям возможности выбирать голограммы взглядом |
| [жесты](../../design/gaze-and-commit.md#composite-gestures) | Добавление пространственных действий в приложения |
| [Голографическая отрисовка](../platform-capabilities-and-apis/rendering.md) | Нарисуйте голограмму в точном месте вокруг пользователей |
| [Контроллер движения](../../design/motion-controllers.md) | Разрешить пользователям предпринимать действия в средах смешанной реальности |
| [Пространственное сопоставление](../../design/spatial-mapping.md) | Сопоставление физического пространства с наложением виртуальной сетки для определения границ среды |
| [Голосовая связь](../../design/voice-input.md) | Захват произнесенных слов, фраз и диктовка со стороны пользователей |
 
> [!NOTE]
> В документации по Опенкср [Путеводитель](openxr.md#roadmap) можно найти предстоящие и встроенные основные функции.

### <a name="3-deploying-and-testing"></a>3. Развертывание и тестирование

Вы можете разрабатывать приложения, используя OpenXR с HoloLens 2 или иммерсивную гарнитуру Windows Mixed Reality с компьютером.  Если у вас нет доступа к гарнитуре, можно использовать [эмулятор HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) или [симулятор Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) .

## <a name="whats-next"></a>Дальнейшие действия

Разработчику всегда будет чем заняться, особенно при изучении нового инструмента или пакета SDK. В приведенных ниже разделах вы найдете информацию для более опытных разработчиков, а также полезные ресурсы, которые помогут вам, если у вас возникнут трудности. Учтите, что эти темы и ресурсы не имеют определенного порядка, поэтому вы можете изучать их в любой последовательности.

### <a name="additional-resources"></a>Дополнительные ресурсы

Если вы хотите выровнять игру Опенкср, ознакомьтесь с приведенными ниже ссылками.

* [Рекомендации по работе с OpenXR](openxr-best-practices.md)
* [Производительность OpenXR](openxr-performance.md)
* [Устранение неполадок с OpenXR](openxr-troubleshooting.md)

## <a name="see-also"></a>См. также
* [Модель приложений](../../design/app-model.md)
* [Представления приложений](../../design/app-views.md)
