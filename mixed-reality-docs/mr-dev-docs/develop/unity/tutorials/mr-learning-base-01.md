---
title: Введение в учебники по MRTK
description: Из этого курса вы узнаете, как с помощью набора Mixed Reality Toolkit (MRTK) создавать приложения смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, решатели, отслеживание взгляда, голосовые команды
ms.localizationpriority: high
ms.openlocfilehash: abee2163c3b92897396ea35cc43ae025e8e7b804
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175482"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a>1. Введение в учебники по MRTK

Приветствуем вас в серии руководств по началу работы! Из этих руководств вы узнаете о наборе средств для смешанной реальности (MRTK) и некоторых его функциях. Кроме того, вы создадите взаимодействие в смешанной реальности, чтобы пользователи могли рассмотреть голограмму, созданную по модели марсохода NASA Curiosity. Пройдя эту серию, вы сможете уверенно работать с MRTK и ускорите процесс разработки.

Руководства в этой серии идут последовательно, поэтому изучайте их в следующем порядке:

1. [Введение](mr-learning-base-01.md) (вы уже здесь)
2. [Инициализация проекта и развертывание первого приложения](mr-learning-base-02.md)
3. [Настройка профилей MRTK](mr-learning-base-03.md)
4. [Размещение объектов в сцене](mr-learning-base-04.md)
5. [Создание динамического содержимого с помощью решателей](mr-learning-base-05.md)
6. [Создание пользовательских взаимодействий](mr-learning-base-06.md)
7. [Взаимодействие с трехмерными объектами](mr-learning-base-07.md)
8. [Использование функции отслеживания взгляда](mr-learning-base-08.md)
9. [Использование голосовых команд](mr-learning-base-09.md)

## <a name="objectives"></a>Задачи

* Узнать, как настроить Unity для MRTK.
* Узнать, как выполнять сборку и развертывание на устройстве.
* Узнать, как использовать некоторые из основных функций MRTK.
* Создать полное взаимодействие смешанной реальности.

## <a name="prerequisites"></a>Предварительные условия

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).
* [Пакет SDK для Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) версии 10.0.18362.0 и выше.
* Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).

* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2020.3 LTS или Unity 2019.4 LTS (**для исправной работы OpenXR требуется версия 2020.3.8 или более поздняя**).

При установке Unity обязательно проверьте следующие компоненты в разделе **Platforms** (Платформы):

* **поддержка сборки для универсальной платформы Windows**;
* **поддержка сборки для Windows (IL2CPP)** .

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

Если вы установили Unity без этих параметров, вы можете добавить их с помощью меню **Add Modules** (Добавить модули) в Unity Hub.

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> Для работы с этой серии руководств рекомендуется MRTK 2.7.2

> [!Important]
> В этой серии руководств учитывается поддержка Unity 2020 LTS (в настоящее время 2020.3.x), если вы используете Open XR или подключаемый модуль Windows XR, а также Unity 2019 LTS (в настоящее время 2019.4.x), если вы используете устаревшую версию WSA или подключаемый модуль Windows XR. Это заменяет все требования к версии Unity, указанные выше.

> [!div class="nextstepaction"]
> [Следующее руководство: 2. Инициализация проекта и развертывание первого приложения](mr-learning-base-02.md)
