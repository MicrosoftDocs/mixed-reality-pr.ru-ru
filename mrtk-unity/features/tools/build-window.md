---
title: Окно сборки
description: Документация по использованию окна сборки в МРТК для Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, сборка, окно сборки, средства
ms.openlocfilehash: b0b2bb1d06a561f5f647d01145fe88f562c53017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176150"
---
# <a name="build-window"></a><span data-ttu-id="f05d7-104">Окно сборки</span><span class="sxs-lookup"><span data-stu-id="f05d7-104">Build window</span></span>
![Создание последовательности развертывания &](images/MRTK_BuildWindow0.png)

<span data-ttu-id="f05d7-106">Окно сборки МРТК упрощает создание & развертывания проектов MRTK-Unity.</span><span class="sxs-lookup"><span data-stu-id="f05d7-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="f05d7-107">при нажатии одной кнопки можно создать проект Unity и создать Visual Studio решение (. SLN), пакет приложения UWP (. APPX) и установить пакет приложения на устройстве.</span><span class="sxs-lookup"><span data-stu-id="f05d7-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="f05d7-108">Параметры сборки Unity</span><span class="sxs-lookup"><span data-stu-id="f05d7-108">Unity Build Options</span></span>
![Окно сборки — параметры сборки Unity 1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="f05d7-110">эти сцены относятся к Параметры сборки Unity.</span><span class="sxs-lookup"><span data-stu-id="f05d7-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="f05d7-111">Тип целевого устройства можно изменить с помощью раскрывающегося меню.</span><span class="sxs-lookup"><span data-stu-id="f05d7-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="f05d7-112">Параметры сборки Appx</span><span class="sxs-lookup"><span data-stu-id="f05d7-112">Appx Build Options</span></span>
![Параметры сборки в окне сборки-appx 2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="f05d7-114">на этой вкладке показана конфигурация решения Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f05d7-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="f05d7-115">чтобы включить возможность ввода данных отслеживания взгляда HoloLens 2, установите флажок для параметра **возможность ввода** .</span><span class="sxs-lookup"><span data-stu-id="f05d7-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="f05d7-116">Вы можете назначить файл. GLBA в поле **Модель средства запуска приложений 3D** для настраиваемого значка запуска 3D-приложения.</span><span class="sxs-lookup"><span data-stu-id="f05d7-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="f05d7-117">Дополнительные сведения см. в статье [руководство по проектированию средства запуска приложений 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) .</span><span class="sxs-lookup"><span data-stu-id="f05d7-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="f05d7-118">По умолчанию в параметрах управления версиями проверяется **автоматическое приращение** .</span><span class="sxs-lookup"><span data-stu-id="f05d7-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="f05d7-119">Версии AppX будут автоматически увеличиваться.</span><span class="sxs-lookup"><span data-stu-id="f05d7-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="f05d7-120">Параметры развертывания</span><span class="sxs-lookup"><span data-stu-id="f05d7-120">Deploy Options</span></span>
![Окно сборки — варианты развертывания 3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="f05d7-122">На этой вкладке можно подключиться к устройству, введя имя пользователя и пароль для портала устройства.</span><span class="sxs-lookup"><span data-stu-id="f05d7-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="f05d7-123">В нижней части страницы можно найти список созданных пакетов приложений.</span><span class="sxs-lookup"><span data-stu-id="f05d7-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

