---
title: Обзор разработки для собственной платформы
description: Узнайте, как создать механизм смешанной реальности на основе DirectX с помощью интерфейсов API Windows Mixed Reality напрямую.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, holographic-визуализация, собственное, собственное приложение, WinRT, приложение WinRT, API платформы, настраиваемое ядро, промежуточное по, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: b137fad12740542deb4995485201a9bd0d1d7662
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581041"
---
# <a name="native-development-overview"></a>Обзор разработки для собственной платформы

![Эмблема собственного баннера](../images/native_logo_banner.png)

Трехмерные модули, такие как [Unity](../unity/unity-development-overview.md) или [Real](../unreal/unreal-development-overview.md) , не являются открытыми для вас путями к разработке смешанной реальности. Вы также можете создавать приложения смешанной реальности с помощью интерфейсов API Windows Mixed Reality с DirectX 11 или DirectX 12. Перейдя к источнику платформы, вы сами создаете собственное по промежуточного слоя или платформу. 

> [!IMPORTANT]
> Если у вас есть проект WinRT, который вы хотите поддерживать, перейдите к нашей основной [документации по WinRT](creating-a-holographic-directx-project.md). 

## <a name="development-checkpoints"></a>Этапы разработки

Используйте следующие контрольные точки, чтобы реализовать свои игры и приложения Unity в мире смешанной реальности.

### <a name="1-getting-started"></a>1. Начало работы

Windows Mixed Reality поддерживает [два типа приложений](../../design/app-views.md):
* Приложения UWP или Win32 **Mixed Reality** , использующие [API Холографикспаце](getting-a-holographicspace.md) или [API опенкср](openxr.md) для визуализации [иммерсивного представления](../../design/app-views.md) , которое заполняет отображение гарнитуры
* **2D-приложения** (UWP), использующие DirectX, XAML или другую платформу для отрисовки [2D-представлений](../../design/app-views.md#2d-views) на планшетах в домашней среде Windows Mixed Reality

Различия между разработкой DirectX для [2D-представлений и иммерсивное представление](../../design/app-views.md) в основном связаны с более holographic и пространственными входными данными. [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) приложения UWP или HWND приложения Win32 являются обязательными и остаются в основном одинаковыми. Это справедливо и для API-интерфейсов WinRT, доступных для приложения. Однако для использования преимуществ holographic необходимо использовать другое подмножество этих API-интерфейсов. Например, система для holographic приложений управляет имеющуюся цепочку буферов и Frame on для реализации циклического цикла кадров.

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

Вы можете разрабатывать приложения на настольном компьютере, используя Опенкср на виртуальной гарнитуре HoloLens 2 или Windows Mixed Reality.  Если у вас нет доступа к гарнитуре, можно использовать [эмулятор HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) или [симулятор Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) .

## <a name="whats-next"></a>Дальнейшие действия

Разработчику всегда будет чем заняться, особенно при изучении нового инструмента или пакета SDK. В следующих разделах вы можете перейти к областям, которые выходят за пределы уже выполненных материалов. Эти разделы и ресурсы не располагаются в последовательном порядке, поэтому вы можете разоойтись и изучить!

### <a name="additional-resources"></a>Дополнительные ресурсы

Если вы хотите выровнять игру Опенкср, ознакомьтесь с приведенными ниже ссылками.

* [Рекомендации по работе с OpenXR](openxr-best-practices.md)
* [Производительность OpenXR](openxr-performance.md)
* [Устранение неполадок с OpenXR](openxr-troubleshooting.md)

## <a name="see-also"></a>См. также раздел
* [Модель приложений](../../design/app-model.md)
* [Представления приложений](../../design/app-views.md)