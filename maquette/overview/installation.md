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
# <a name="installing-maquette"></a><span data-ttu-id="9359f-104">Установка Макуетте</span><span class="sxs-lookup"><span data-stu-id="9359f-104">Installing Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text. -->
<span data-ttu-id="9359f-105">![Установка логотипа ](../images/MaquetteIcon.png) макуеттескрипт</span><span class="sxs-lookup"><span data-stu-id="9359f-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Installation</span></span>

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
<span data-ttu-id="9359f-106">Разработка Макуеттескрипт в основном выполняется в VSCode.</span><span class="sxs-lookup"><span data-stu-id="9359f-106">MaquetteScript development is primarily done within VSCode.</span></span> <span data-ttu-id="9359f-107">Макуеттескрипт может выполняться из скрипта, содержащегося в `.mqjs` файлах, а также через специальный интерфейс расширения VSCode.</span><span class="sxs-lookup"><span data-stu-id="9359f-107">MaquetteScript can run from script contained in `.mqjs` files and also via a special VSCode extension interface.</span></span> <span data-ttu-id="9359f-108">Интеграция между VSCode и Макуетте для включения интерфейса расширения осуществляется с помощью расширения Макуеттескрипт VSCode.</span><span class="sxs-lookup"><span data-stu-id="9359f-108">Integration between VSCode and Maquette to enable the extension interface is accomplished with a MaquetteScript VSCode extension.</span></span>

## <a name="installing-the-vscode-extension"></a><span data-ttu-id="9359f-109">Установка расширения VSCode</span><span class="sxs-lookup"><span data-stu-id="9359f-109">Installing the VSCode Extension</span></span>

* <span data-ttu-id="9359f-110">Скачайте и установите [VSCode](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="9359f-110">Download and install [VSCode](https://code.visualstudio.com).</span></span> 

<span data-ttu-id="9359f-111">Расширение JavaScript Макуетте находится в [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="9359f-111">The Maquette javascript extension is in [the Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span></span>

* <span data-ttu-id="9359f-112">Запустите [процедуру установки расширения](vscode:extension/ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="9359f-112">Run the [installation procedure for the extension](vscode:extension/ms-maquette.vscode-maquette-javascript).</span></span>

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a><span data-ttu-id="9359f-113">Включение сценариев</span><span class="sxs-lookup"><span data-stu-id="9359f-113">Enabling Scripting</span></span>

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

<span data-ttu-id="9359f-114">Чтобы сделать скрипты доступными во время предварительного выпуска, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="9359f-114">To make scripting accessible during pre-release:</span></span>

* <span data-ttu-id="9359f-115">Добавьте файл с именем `scripting.enabled` в каталог документов пользователей для макуетте в папке: `~/Documents/Maquette/Settings` .</span><span class="sxs-lookup"><span data-stu-id="9359f-115">Put a file with the name `scripting.enabled` in the Users Documents directory for Maquette in: `~/Documents/Maquette/Settings`.</span></span>

<span data-ttu-id="9359f-116">После установки скрипты по умолчанию будут отключены по соображениям безопасности.</span><span class="sxs-lookup"><span data-stu-id="9359f-116">After installation, scripting will be disabled by default for security reasons.</span></span>

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* <span data-ttu-id="9359f-117">Чтобы включить выполнение скрипта, включите его на вкладке Главная окна помощника или в файле параметров JSON.</span><span class="sxs-lookup"><span data-stu-id="9359f-117">To enable execution of script, turn it ON in the main tab of the companion window or in the json settings file.</span></span>

![Включение сценариев в VS Code](images/IntroductionEnableScripting.png)


