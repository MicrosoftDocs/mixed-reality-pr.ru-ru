---
title: Знакомство с MRTK для Unreal
description: Сведения, позволяющие новым разработчикам решений смешанной реальности начать работу с набором Mixed Reality Toolkit для Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, тестирование, Mixed Reality Toolkit, MRTK версии 2, MRTK, инструменты, пакет SDK, HoloLens, HoloLens 2, Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, кросс-платформенность
ms.openlocfilehash: 4aa21cbee75c4c362abfd609add922ad9c922682
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584833"
---
# <a name="introducing-mrtk-for-unreal"></a>Знакомство с MRTK для Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Что такое набор средств для смешанной реальности (MRTK)?

MRTK — это превосходный набор инструментов с открытым кодом, ведущий свою историю еще с момента выпуска HoloLens. Своей широкой функциональностью он обязан упорной работе сообщества разработчиков. 

Mixed Reality Toolkit для Unreal (MRTK-Unreal) представляет собой набор таких компонентов, как подключаемые модули, примеры и документы, созданных для помощи в разработке приложений смешанной реальности с использованием Unreal Engine. В настоящее время этот набор средств включает следующие компоненты:
* [UX Tools для Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) — предоставляет код, схемы и примеры для реализации функций взаимодействия с пользователем в приложениях Hololens 2.
* [Graphics Tools для Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal) — помогают улучшить графику для приложений смешанной реальности с минимальным влиянием на производительность.

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

Изучите [документацию по MRTK на GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) и воспользуйтесь руководствами по установке для [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) и [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md).

### <a name="modular"></a>Модульность

MRTK для Unreal является модульным, поэтому нет необходимости добавлять его в проект целиком. Вы можете выбрать и установить только необходимые подключаемые модули, а позднее добавлять или удалять их по мере надобности. Такой подход помогает поддерживать небольшой объем проекта и упрощает управление им.  

### <a name="performant"></a>Высокая производительность

Помня об ограничениях мобильных платформ, при создании MRTK Unreal мы ориентировались на производительность. Это очень важный фактор, и мы стремились сделать инструменты максимально полезными.

## <a name="see-also"></a>См. также статью

* [Установка средств](../install-the-tools.md)
* [Разработка с помощью MRTK для Unreal](unreal-development-overview.md)
* [Руководство по установке UX Tools (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [Домашняя страница документации по UX Tools (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [Руководство по установке Graphics Tools (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [Домашняя страница документации по Graphics Tools (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)