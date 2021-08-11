---
title: Обзор разработки для собственной платформы
description: узнайте, как создать модуль смешанной реальности на основе DirectX с помощью интерфейсов api Windows Mixed Reality напрямую.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, holographic-визуализация, собственное, собственное приложение, WinRT, приложение WinRT, API платформы, настраиваемое ядро, промежуточное по, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 056cb0c07002cb319e8acadf66e7f59650f5e00413440d6ad0103aa8ee936400
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200181"
---
# <a name="native-development-overview"></a>Обзор разработки для собственной платформы

![Эмблема собственного баннера](../images/native_logo_banner.png)

Трехмерные модули, такие как [Unity](../unity/unity-development-overview.md) или [Real](../unreal/unreal-development-overview.md) , не являются открытыми для вас путями к разработке смешанной реальности. вы также можете создавать приложения смешанной реальности с помощью Windows Mixed Reality api-интерфейсов с directx 11 или directx 12. Перейдя к источнику платформы, вы сами создаете собственное по промежуточного слоя или платформу. 

> [!IMPORTANT]
> Если у вас есть проект WinRT, который вы хотите поддерживать, перейдите к нашей основной [документации по WinRT](creating-a-holographic-directx-project.md). 

## <a name="development-checkpoints"></a>Этапы разработки

Используйте следующие контрольные точки, чтобы реализовать свои игры и приложения Unity в мире смешанной реальности.

### <a name="1-getting-started"></a>1. Начало работы

Windows Mixed Reality поддерживает [два типа приложений](../../design/app-views.md):
* Приложения UWP или Win32 **Mixed Reality** , использующие [API Холографикспаце](getting-a-holographicspace.md) или [API опенкср](openxr.md) для визуализации [иммерсивного представления](../../design/app-views.md) , которое заполняет отображение гарнитуры
* **двумерные приложения** (UWP), использующие DirectX, XAML или другую платформу для отрисовки [2d-представлений](../../design/app-views.md#2d-views) на планшетах в Windows Mixed Reality home

Различия между разработкой DirectX для [2D-представлений и иммерсивное представление](../../design/app-views.md) в основном связаны с более holographic и пространственными входными данными. [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) приложения UWP или HWND приложения Win32 являются обязательными и остаются в основном одинаковыми. Это справедливо и для API-интерфейсов WinRT, доступных для приложения. Однако для использования преимуществ holographic необходимо использовать другое подмножество этих API-интерфейсов. Например, система для holographic приложений управляет имеющуюся цепочку буферов и Frame on для реализации циклического цикла кадров.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Основные компоненты

Windows Mixed Reality приложения используют следующие api для создания [смешанных](../../discover/mixed-reality.md) возможностей для HoloLens и других впечатляющих головных телефонов:

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

вы можете разрабатывать приложения на настольном компьютере, используя опенкср HoloLens 2 или Windows Mixed Reality иммерсивное гарнитуру.  если у вас нет доступа к гарнитуре, вы можете использовать [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) или [симулятор Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) .

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