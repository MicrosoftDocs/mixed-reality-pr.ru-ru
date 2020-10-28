---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638736"
---
# <a name="all-platforms"></a>[<span data-ttu-id="1ab20-101">Все платформы</span><span class="sxs-lookup"><span data-stu-id="1ab20-101">All platforms</span></span>](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a><span data-ttu-id="1ab20-102">Включение подключаемого модуля контроллера движения HP</span><span class="sxs-lookup"><span data-stu-id="1ab20-102">Enabling HP Motion Controller Plugin</span></span> 

<span data-ttu-id="1ab20-103">Профили взаимодействия и сопоставления контроллеров находятся в подключаемом модуле контроллера HP Motion, который должен быть включен, чтобы предоставлять сопоставления контроллеров для системы ввода в нереальном виде.</span><span class="sxs-lookup"><span data-stu-id="1ab20-103">The interaction profile and controller mappings are in the HP Motion Controller plugin, which must be enabled to expose the controller mappings to Unreal’s input system.</span></span>

![Включение подключаемого модуля Опенксрхпконтроллер](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[<span data-ttu-id="1ab20-105">SteamVR</span><span class="sxs-lookup"><span data-stu-id="1ab20-105">SteamVR</span></span>](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a><span data-ttu-id="1ab20-106">Настройка запуска и Хмдплугинприорити</span><span class="sxs-lookup"><span data-stu-id="1ab20-106">Configuring Startup and HMDPluginPriority</span></span>

<span data-ttu-id="1ab20-107">Входные данные в нереальном использовании Стеамвр имеют несколько отличий.</span><span class="sxs-lookup"><span data-stu-id="1ab20-107">Input in Unreal using SteamVR has a few differences.</span></span>  <span data-ttu-id="1ab20-108">При настройке проекта сначала убедитесь, что он использует новую входную систему Стеамвр, добавив **VR. Стеамвр. Енаблевринпут = 1** в раздел **Startup** в **Engine/config/ConsoleVariables.ini** .</span><span class="sxs-lookup"><span data-stu-id="1ab20-108">When setting up the project, first ensure it is using SteamVR’s new input system by adding **vr.SteamVR.EnableVRInput=1** to the **Startup** section in **Engine/Config/ConsoleVariables.ini** .</span></span>  <span data-ttu-id="1ab20-109">Этот ini-каталог находится в каталоге установки Engine, а не в каталоге проекта.</span><span class="sxs-lookup"><span data-stu-id="1ab20-109">This ini is found in the engine install directory, not the project directory.</span></span>

![Обновление конфигурации запуска](../images/reverb-g2-img-07.png)

<span data-ttu-id="1ab20-111">Подключаемый модуль контроллера движения HP включит Опенкср.</span><span class="sxs-lookup"><span data-stu-id="1ab20-111">The HP Motion Controller plugin will enable OpenXR.</span></span>  <span data-ttu-id="1ab20-112">Если вы не используете Опенкср, необходимо изменить Хмдплугинприорити Стеамвр в BaseEngine.ini в том же каталоге, что и ConsoleVariables.ini.</span><span class="sxs-lookup"><span data-stu-id="1ab20-112">If you're not using OpenXR, you will need to edit the HMDPluginPriority of SteamVR in BaseEngine.ini in the same directory as ConsoleVariables.ini.</span></span>  <span data-ttu-id="1ab20-113">Измените значение Стеамвр, чтобы оно было больше значения Опенксрхмд.</span><span class="sxs-lookup"><span data-stu-id="1ab20-113">Change the SteamVR value to be greater than the OpenXRHMD value.</span></span>

![Обновление конфигурации Хмдплугинприорити](../images/reverb-g2-img-08.png)


