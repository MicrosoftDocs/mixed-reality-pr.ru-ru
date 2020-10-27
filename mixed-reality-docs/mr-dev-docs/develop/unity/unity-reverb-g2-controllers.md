---
title: HP reverbы G2 Controllers в Unity
description: Инструкции по использованию контроллеров HP REVERB G2 в Стеамвр и Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, переглагол, переглаголы G2, HP reverbы G2, Mixed Reality, разработка, контроллеры движения, ввод данных, функции, новый проект, эмулятор, документация, руководства, функции, голограммы, Разработка игр
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638391"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>HP reverbы G2 Controllers в Unity

## <a name="getting-started"></a>Начало работы

Если вы разрабатываете для Стеамвр или используете входной API Windows Mixed Reality (XR), дополнительная настройка не требуется для использования контроллера HP reverbа G2. Головк. Входные данные). Однако кнопки A, B, X, Y и триггера сжатие в настоящее время недоступны через диспетчер ввода, если не используется Стеамвр. Поддержка дополнительных входных данных G2 будет доступна в ближайшем будущем, поэтому обязательно выполните проверку.

## <a name="porting-existing-applications"></a>Перенос существующих приложений

Если у вас уже есть приложение, разрабатываемое для впечатляющих головных телефонов Windows Mixed Reality, ознакомьтесь с нашим [руководством по переносу](../porting-apps/porting-guides.md) и [параметрами проекта](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) , чтобы получить общие рекомендации.

## <a name="mapping-input"></a>Вход сопоставления

Когда вы будете готовы приступить к подключению входных данных для новых контроллеров, начните работу с раздела " [Сопоставление входных данных](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) " в пошаговом руководством по переносу. Инструкции по настройке входных данных в Unity подробно описаны в разделе [жесты и контроллеры движения](gestures-and-motion-controllers-in-unity.md), а также полная [Таблица сопоставления кнопок и осей](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) для справки.

## <a name="see-also"></a>См. также статью
* [Обновление для SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)