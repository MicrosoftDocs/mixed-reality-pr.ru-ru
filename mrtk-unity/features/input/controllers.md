---
title: Контроллеры
description: Использование контроллеров в МРТК
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, контроллеры,
ms.openlocfilehash: c92ad099d770cc52467918053af02e7bebab928d
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850340"
---
# <a name="controllers"></a>Контроллеры

Контроллеры создаются и уничтожаются автоматически [**поставщиками входных данных**](input-providers.md). Каждый тип контроллера имеет ряд *физических входов* , определенных *типом оси*, указывая тип данных входного значения (цифровые, одинарную ось, двойную ось, шесть ДОФ,...) и *тип ввода* (нажатие кнопки, триггер, закрепление, пространственный указатель,...), описывающий источник входных данных. Физические входные данные сопоставлены с *входными действиями* через **профиль сопоставления входных данных контроллера** в *системном профиле входных* данных в компоненте набора средств Mixed Reality.

МРТК будет автоматически обнаруживать контроллеры ВМР и отображать их при установке пакета [**Microsoft. микседреалити. Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) . Модели контроллеров отображаются в редакторе только при использовании конвейера Опенкср. Для визуализации моделей контроллеров Окулус следуйте инструкциям по [развертыванию Окулус Quest](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md) .

![Сопоставление входных данных контроллера](../images/input/ControllerInputMapping.png)