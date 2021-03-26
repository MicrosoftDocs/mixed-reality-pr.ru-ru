---
title: Установка инструментов
description: Здесь вы найдете последние версии Unity, Visual Studio и инструментов, рекомендуемых для разработки для HoloLens и виртуальной реальности.
author: thetuvix
ms.author: alexturn
ms.date: 02/09/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: ac8e4dab8b9d9021c834e0a9d673c81ac3b7f1dc
ms.sourcegitcommit: f74d33d50c1fbfebe8571695d631ce78dd599f74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881241"
---
# <a name="install-the-tools"></a>Установка инструментов

Получите инструменты, необходимые для создания приложений для иммерсивных гарнитур (гарнитур виртуальной реальности) Microsoft HoloLens и Windows Mixed Reality. Для разработки решений для Windows Mixed Reality не существует отдельного пакета SDK. Вы будете использовать Visual Studio с пакетом SDK для Windows 10.

У вас нет устройства смешанной реальности? Вы можете установить [эмулятор HoloLens](platform-capabilities-and-apis/using-the-hololens-emulator.md), чтобы протестировать отдельные функции приложений смешанной реальности без HoloLens. Вы также можете использовать [симулятор Windows Mixed Reality](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md), чтобы протестировать приложения смешанной реальности для иммерсивных гарнитур. 

Рекомендуем установить игровой модуль Unity или Unreal. Это самый простой способ приступить к созданию приложений смешанной реальности. Кроме того, вы можете воспользоваться DirectX, если захотите использовать собственный модуль.

Если вы работаете с Unity, вы можете использовать имитацию ввода, предлагаемую [Набором средств для Смешанной реальности для Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), чтобы протестировать разные типы взаимодействий ввода, например с помощью отслеживания взгляда или движений рук. Для проектов Unreal используйте [подключаемый модуль UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), чтобы проверить общие взаимодействия ввода и возможности взаимодействия с пользователем.

>[!TIP]
>Добавьте эту страницу в закладки и регулярно просматривайте ее, чтобы быть в курсе самых последних версий каждого инструмента, рекомендованного для разработки приложений смешанной реальности.

<br>

## <a name="installation-checklist"></a>Контрольный список установки

| Средство | Примечания |
|---------|---------|
| ![Логотип Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (ссылка для установки вручную)</a><br><br>Установите самую последнюю версию Windows 10, чтобы операционная система вашего компьютера соответствовала платформе, для которой вы создаете приложения смешанной реальности.  | **Установка Windows 10** <br> Вы можете установить последнюю версию Windows 10 с помощью клиентского компонента Центра обновления Windows, к которому можно перейти в разделе параметров, или путем создания установочного носителя (открыв ссылку, указанную в левом столбце). <br><br>Сведения о новых функциях смешанной реальности, доступных в каждом выпуске Windows 10, см. в [заметках о текущем выпуске](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md). **Включите режим разработчика на компьютере** в разделе "Параметры > Обновление и безопасность > Для разработчиков". <br><br> **Примечание, касающееся корпоративных компьютеров**<br>Если вашим компьютером управляет ИТ-отдел вашей организации, возможно, вам потребуется связаться с его сотрудниками для обновления. <br><br> **N-версии Windows**<br> Иммерсивные гарнитуры (виртуальная реальность) Windows Mixed Reality не поддерживаются в N-версиях Windows. |
| ![Изображение с логотипом Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (версии 16.8 или выше)** (ссылка для установки)</a> <br><br>Полнофункциональная интегрированная среда разработки (IDE) для Windows и многое другое. Вы будете использовать Visual Studio для написания кода, отладки, тестирования и развертывания. | **Установка Visual Studio 2019** <br> Установите следующие рабочие нагрузки: <br><br>*● Разработка классических приложений на C++*<br>*● Разработка приложений универсальной платформы Windows (UWP)*<br><br>В рабочей нагрузке UWP обязательно проверьте следующий дополнительный компонент, если вы выполняете разработку для HoloLens:<br><br>*● Подключение USB-устройств*<br><br>**Примечание о подключении через USB**<br>Обязательно установите флажок **IP по USB** во время установки (он не установлен по умолчанию). Это необходимо для обмена данными с HoloLens через USB.<br><br>**Примечание, касающееся Unity**<br>Если вам не нужно устанавливать более новую (не LTS) версию Unity, рекомендуем *не* устанавливать рабочую нагрузку Unity в составе установки Visual Studio, а вместо этого установить поток **Unity 2019 LTS**.<br><br>**Известные проблемы**<br>Сейчас в Visual Studio 2019 (версия 16.0) существует ряд известных проблем с отладкой приложений смешанной реальности.  Обновите **Visual Studio 2019 до версии не ниже 16.8**. |
| ![Логотип Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Пакет SDK для Windows 10 (10.0.18362.0)** (ссылка для установки вручную)</a> <br><br>Содержит новейшие заголовки, библиотеки, метаданные и средства для создания приложений для Windows 10 в HoloLens 2. | **Для создания приложений HoloLens 2 потребуется установить пакет Windows SDK сборки 18362 или более поздней.**<br> <br> Если вы разрабатываете приложения только для настольных гарнитур Windows Mixed Reality или HoloLens (1-го поколения), можно использовать пакет SDK для Windows, установленный в Visual Studio 2017. |
| ![Логотип Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2156684" target="_blank">**Эмулятор HoloLens 2 (Windows Holographic, версия 20H2 с обновлением за март 2021 г.)** (ссылка для установки: 10.0.19041.1140)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Эмулятор HoloLens (1-го поколения)** (ссылка для установки: 10.0.17763.134)</a> <br><br>Эмулятор позволяет запускать приложения с помощью образа виртуальной машины HoloLens без физического устройства HoloLens.<br> <br> | Дополнительные сведения об использовании эмулятора HoloLens см. в [этой статье](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md).<br> <br> Для успешной установки эмулятора **ваша система должна поддерживать Hyper-V**. Подробные сведения см. в разделе о системных требованиях. <br> <br> **Примечание по эмулятору HoloLens (1-го поколения)** <br>  Для успешной установки необходимо решение Visual Studio 2017. Если вы устанавливаете эмулятор HoloLens (1-го поколения) с Visual Studio 2019, вам необходимо отменить выбор шаблонов VS и [установить их из Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="install-your-engine-of-choice"></a>Установка предпочтительного движка

Теперь, когда вы настроили Windows 10, Visual Studio и Windows 10 SDK для работы, мы установим и настроим движок по вашему выбору. 

Если вы еще не выбрали движок, см. статью [Введение в разработку приложений смешанной реальности](https://docs.microsoft.com/windows/mixed-reality/develop/development?tabs=unity#what-technology-path-are-you-interested-in). 

[!INCLUDE[](includes/tools-overview.md)]

