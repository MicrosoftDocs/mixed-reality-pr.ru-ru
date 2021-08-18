---
title: Знакомство с MRTK для Unreal
description: Сведения, позволяющие новым разработчикам решений смешанной реальности начать работу с набором Mixed Reality Toolkit для Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, тестирование, Mixed Reality Toolkit, MRTK версии 2, MRTK, инструменты, пакет SDK, HoloLens, HoloLens 2, Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, кросс-платформенность
ms.openlocfilehash: 06eacac245c80f16ab48dbda4b5aca740ffdfd66a0266beafac5e46b39a9d109
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221834"
---
# <a name="introducing-mrtk-for-unreal"></a>Знакомство с MRTK для Unreal

![Изображение баннера MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Что такое набор средств для смешанной реальности (MRTK)?

MRTK — это превосходный набор инструментов с открытым кодом, ведущий свою историю еще с момента выпуска HoloLens. Своей широкой функциональностью он обязан упорной работе сообщества разработчиков. 

Mixed Reality Toolkit для Unreal (MRTK-Unreal) представляет собой набор таких компонентов, как подключаемые модули, примеры и документы, созданных для помощи в разработке приложений смешанной реальности с использованием Unreal Engine. В настоящее время этот набор средств включает следующие компоненты:
* [UX Tools для Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) — предоставляет код, схемы и примеры для реализации функций взаимодействия с пользователем в приложениях Hololens 2.
* [Graphics Tools для Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal) — помогают улучшить графику для приложений смешанной реальности с минимальным влиянием на производительность.

Изучите [документацию по MRTK на GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) и воспользуйтесь руководствами по установке для [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) и [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md).

### <a name="modular"></a>Модульность

MRTK для Unreal является модульным, поэтому нет необходимости добавлять его в проект целиком. Вы можете выбрать и установить только необходимые подключаемые модули, а позднее добавлять или удалять их по мере надобности. Такой подход помогает поддерживать небольшой объем проекта и упрощает управление им.  

### <a name="performant"></a>Высокая производительность

Помня об ограничениях мобильных платформ, при создании MRTK Unreal мы ориентировались на производительность. Это очень важный фактор, и мы стремились сделать инструменты максимально полезными.

## <a name="project-setup"></a>Настройка проекта

> [!div class="nextstepaction"]
> [Скачивание Unreal Engine и MRTK](unreal-project-setup.md)

## <a name="see-also"></a>См. также статью

* [Установка средств](../install-the-tools.md)
* [Разработка с помощью MRTK для Unreal](unreal-development-overview.md)
* [Руководство по установке UX Tools (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [Домашняя страница документации по UX Tools (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [Руководство по установке Graphics Tools (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [Домашняя страница документации по Graphics Tools (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)