---
title: Установка Макуетте
description: Узнайте, как установить и настроить Макуетте в VSCode.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Макуетте, создание прототипов, Смешанная реальность, виртуальная реальность, VR, MR, обратная связь, центр обратной связи, ошибки
ms.openlocfilehash: ba0064326e83f04b056c0baa2f86f718e41bedfe
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935553"
---
# <a name="installing-maquette"></a>Установка Макуетте

<!-- TODO(Harrison): Need consolidated logo with text. -->
![Установка логотипа ](../images/MaquetteIcon.png) макуеттескрипт

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
Разработка Макуеттескрипт в основном выполняется в VSCode. Макуеттескрипт может выполняться из скрипта, содержащегося в `.mqjs` файлах, а также через специальный интерфейс расширения VSCode. Интеграция между VSCode и Макуетте для включения интерфейса расширения осуществляется с помощью расширения Макуеттескрипт VSCode.

## <a name="installing-the-vscode-extension"></a>Установка расширения VSCode

* Скачайте и установите [VSCode](https://code.visualstudio.com). 

Расширение JavaScript Макуетте находится в [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).

* Запустите [процедуру установки расширения](vscode:extension/ms-maquette.vscode-maquette-javascript).

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>Включение сценариев

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

Чтобы сделать скрипты доступными во время предварительного выпуска, выполните следующие действия.

* Добавьте файл с именем `scripting.enabled` в каталог документов пользователей для макуетте в папке: `~/Documents/Maquette/Settings` .

После установки скрипты по умолчанию будут отключены по соображениям безопасности.

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* Чтобы включить выполнение скрипта, включите его на вкладке Главная окна помощника или в файле параметров JSON.

![Включение сценариев в VS Code](images/IntroductionEnableScripting.png)


