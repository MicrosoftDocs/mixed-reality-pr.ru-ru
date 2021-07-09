---
title: 1. Начало работы
description: Часть 1 (из 6) серии руководств по созданию приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля Mixed Reality UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, UX Tools, документация, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: efa0bc210fc20b9e639954a06e97eb78661d87e5
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712583"
---
# <a name="1-getting-started"></a>1. Начало работы

Как новичкам, так и опытным специалистам по разработке приложений смешанной реальности стоит начать работу с [HoloLens 2](../../../index.yml) и [Unreal Engine](https://www.unrealengine.com/en-US/) отсюда. В этой серии руководств даются пошаговые инструкции по созданию интерактивного приложения для игры в шахматы с помощью [подключаемого модуля средств UX](https://github.com/microsoft/MixedReality-UXTools-Unreal), входящего в состав [набора средств для смешанной реальности для Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal). Этот подключаемый модуль содержит код, схемы и примеры, которые помогут вам реализовать распространенные функции пользовательского интерфейса в своих проектах. 

![Готовая сцена в окне просмотра](images/unreal-uxt/5-endscene.PNG)

К концу этой серии руководств вы получите научитесь выполнять следующие задачи:
* создание проекта;
* настройка проекта для смешанной реальности;
* работа с пользовательским вводом;
* добавление кнопок;
* воспроизведение на эмуляторе или устройстве.

## <a name="prerequisites"></a>предварительные требования

Прежде чем приступать, убедитесь, что вы установили следующие компоненты:
* Windows 10 1809 или более поздней версии.
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.26 или более поздней версии
* Устройство Microsoft HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode), или [эмулятор](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview).
* Visual Studio 2019 с указанными ниже рабочими нагрузками

### <a name="installing-visual-studio-2019"></a>Установка Visual Studio 2019

Сначала убедитесь, что в вашей установке есть все необходимые пакеты Visual Studio:
1. Установите последнюю версию [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).
1. Установите следующие [рабочие нагрузки](/visualstudio/install/modify-visual-studio#modify-workloads):
    * "Разработка классических приложений на C++";
    * "Разработка классических приложений .NET";
    * "Разработка приложений для универсальной платформы Windows".
1. Разверните пункт "Разработка приложений для универсальной платформы Windows" и выберите следующее: 
    * Подключение USB-устройств
    * Средства универсальной платформы Windows на C++ (версия 142)

1. Установите следующие [компоненты](/visualstudio/install/modify-visual-studio#modify-individual-components):
    * компиляторы, средства сборки и среды выполнения > средства сборки MSVC v142 — VS 2019 C++ ARM64 (последняя версия).

Вы можете подтвердить установку по следующему изображению:

![Флажки, которые обязательно нужно установить при установке VS](images/unreal-uxt/1-install-the-tools.png)

Вот и все! Можно приступать к проекту по созданию шахматного приложения.

[Следующий раздел: 2. Инициализация проекта и первое приложение](unreal-uxt-ch2.md)