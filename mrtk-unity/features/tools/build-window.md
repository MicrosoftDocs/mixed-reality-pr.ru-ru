---
title: Окно сборки МРТК
description: Документация по использованию окна сборки в МРТК для Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, сборка, окно сборки, инструменты
ms.openlocfilehash: 00ccbc5cfbb3b034771585a1263c624309b08465
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196871"
---
# <a name="build-window"></a><span data-ttu-id="55b8e-104">Окно сборки</span><span class="sxs-lookup"><span data-stu-id="55b8e-104">Build window</span></span>
![Создание последовательности развертывания &](images/MRTK_BuildWindow0.png)

<span data-ttu-id="55b8e-106">Окно сборки МРТК упрощает создание & развертывания проектов MRTK-Unity.</span><span class="sxs-lookup"><span data-stu-id="55b8e-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="55b8e-107">При нажатии одной кнопки можно создать проект Unity и создать решение Visual Studio (. SLN), пакет приложения UWP (. APPX) и установить пакет приложения на устройстве.</span><span class="sxs-lookup"><span data-stu-id="55b8e-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="55b8e-108">Параметры сборки Unity</span><span class="sxs-lookup"><span data-stu-id="55b8e-108">Unity Build Options</span></span>
![Окно сборки — параметры сборки Unity 1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="55b8e-110">Эти сцены относятся к параметрам сборки Unity.</span><span class="sxs-lookup"><span data-stu-id="55b8e-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="55b8e-111">Тип целевого устройства можно изменить с помощью раскрывающегося меню.</span><span class="sxs-lookup"><span data-stu-id="55b8e-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="55b8e-112">Параметры сборки Appx</span><span class="sxs-lookup"><span data-stu-id="55b8e-112">Appx Build Options</span></span>
![Параметры сборки в окне сборки-appx 2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="55b8e-114">На этой вкладке показана конфигурация решения Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55b8e-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="55b8e-115">Чтобы включить возможность ввода отслеживания взгляда HoloLens 2, установите флажок для параметра **возможность ввода** .</span><span class="sxs-lookup"><span data-stu-id="55b8e-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="55b8e-116">Вы можете назначить файл. GLBA в поле **Модель средства запуска приложений 3D** для настраиваемого значка запуска 3D-приложения.</span><span class="sxs-lookup"><span data-stu-id="55b8e-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="55b8e-117">Дополнительные сведения см. в статье [руководство по проектированию средства запуска приложений 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) .</span><span class="sxs-lookup"><span data-stu-id="55b8e-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="55b8e-118">По умолчанию в параметрах управления версиями проверяется **автоматическое приращение** .</span><span class="sxs-lookup"><span data-stu-id="55b8e-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="55b8e-119">Версии AppX будут автоматически увеличиваться.</span><span class="sxs-lookup"><span data-stu-id="55b8e-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="55b8e-120">Параметры развертывания</span><span class="sxs-lookup"><span data-stu-id="55b8e-120">Deploy Options</span></span>
![Окно сборки — варианты развертывания 3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="55b8e-122">На этой вкладке можно подключиться к устройству, введя имя пользователя и пароль для портала устройства.</span><span class="sxs-lookup"><span data-stu-id="55b8e-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="55b8e-123">В нижней части страницы можно найти список созданных пакетов приложений.</span><span class="sxs-lookup"><span data-stu-id="55b8e-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

