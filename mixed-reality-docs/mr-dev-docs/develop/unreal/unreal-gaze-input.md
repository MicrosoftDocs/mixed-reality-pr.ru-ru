---
title: Взгляните на входные данные в нереальном режиме
description: Руководство по настройке входных данных взгляда для HoloLens и нереального модуля
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, HoloLens 2, отслеживание взгляда, ввод с экрана, подключенный головной дисплей, нереалный механизм, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679053"
---
# <a name="gaze-input"></a><span data-ttu-id="5bb1e-104">Входные данные взгляда</span><span class="sxs-lookup"><span data-stu-id="5bb1e-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="5bb1e-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="5bb1e-105">Overview</span></span>

<span data-ttu-id="5bb1e-106">[Подключаемый модуль Windows Mixed Reality](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) не предоставляет встроенных функций для ввода данных, но HoloLens 2 поддерживает отслеживание глаз.</span><span class="sxs-lookup"><span data-stu-id="5bb1e-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="5bb1e-107">Фактические функции отслеживания предоставляются в виде интерфейсов API **монитора** и **отслеживания взгляда** в режиме реального времени и включают:</span><span class="sxs-lookup"><span data-stu-id="5bb1e-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="5bb1e-108">Сведения об устройстве</span><span class="sxs-lookup"><span data-stu-id="5bb1e-108">Device information</span></span>
- <span data-ttu-id="5bb1e-109">Датчики отслеживания</span><span class="sxs-lookup"><span data-stu-id="5bb1e-109">Tracking sensors</span></span>
- <span data-ttu-id="5bb1e-110">Ориентация и положение</span><span class="sxs-lookup"><span data-stu-id="5bb1e-110">Orientation and position</span></span>
- <span data-ttu-id="5bb1e-111">Области обрезки</span><span class="sxs-lookup"><span data-stu-id="5bb1e-111">Clipping panes</span></span>
- <span data-ttu-id="5bb1e-112">Взгляните на данные и сведения об отслеживании</span><span class="sxs-lookup"><span data-stu-id="5bb1e-112">Gaze data and tracking information</span></span>

<span data-ttu-id="5bb1e-113">Полный список функций см. в документации по нереальному [подключению](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) и [отслеживания взглядов](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) .</span><span class="sxs-lookup"><span data-stu-id="5bb1e-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="5bb1e-114">В дополнение к нереальным API-интерфейсам ознакомьтесь с документацией по [взаимодействию на основе взгляда](../../design/eye-gaze-interaction.md) для hololens 2 и прочитайте о работе [отслеживания взгляда в hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) .</span><span class="sxs-lookup"><span data-stu-id="5bb1e-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](../../design/eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5bb1e-115">Отслеживание взгляда поддерживается только в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5bb1e-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="5bb1e-116">Включение отслеживания взгляда</span><span class="sxs-lookup"><span data-stu-id="5bb1e-116">Enabling eye tracking</span></span>
<span data-ttu-id="5bb1e-117">Необходимо включить входные данные для параметров проекта HoloLens, прежде чем можно будет использовать интерфейсы API нереального времени.</span><span class="sxs-lookup"><span data-stu-id="5bb1e-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="5bb1e-118">При запуске приложения появится запрос на согласие, показанный на снимке экрана ниже.</span><span class="sxs-lookup"><span data-stu-id="5bb1e-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="5bb1e-119">Выберите **Да** , чтобы задать разрешение и получить доступ к вводу с помощью взгляда.</span><span class="sxs-lookup"><span data-stu-id="5bb1e-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="5bb1e-120">Если необходимо изменить этот параметр в любое время, его можно найти в приложении " **Параметры** ".</span><span class="sxs-lookup"><span data-stu-id="5bb1e-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![Разрешения на вход с глазами](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="5bb1e-122">Отслеживание глаз HoloLens в нереальном режиме имеет один луч для обоих глаз, а не два луча, необходимых для отслеживания стереоскопик, что не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="5bb1e-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="5bb1e-123">Это все, что необходимо для того, чтобы добавить входные данные взгляда в приложения HoloLens 2 в нереальном виде.</span><span class="sxs-lookup"><span data-stu-id="5bb1e-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="5bb1e-124">Дополнительные сведения о вводе и том, как он влияет на пользователей в смешанной реальности, можно найти по ссылкам ниже.</span><span class="sxs-lookup"><span data-stu-id="5bb1e-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="5bb1e-125">Не забудьте подумать об этих возможностях при создании интерактивных интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="5bb1e-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="5bb1e-126">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="5bb1e-126">Next Development Checkpoint</span></span>

<span data-ttu-id="5bb1e-127">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении основных стандартных блоков MRTK.</span><span class="sxs-lookup"><span data-stu-id="5bb1e-127">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="5bb1e-128">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="5bb1e-128">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="5bb1e-129">Отслеживание рук</span><span class="sxs-lookup"><span data-stu-id="5bb1e-129">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="5bb1e-130">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="5bb1e-130">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5bb1e-131">Камера HoloLens</span><span class="sxs-lookup"><span data-stu-id="5bb1e-131">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="5bb1e-132">Вы можете в любой момент вернуться к [этапам разработки для Unreal](unreal-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="5bb1e-132">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bb1e-133">См. также статью</span><span class="sxs-lookup"><span data-stu-id="5bb1e-133">See also</span></span>
* [<span data-ttu-id="5bb1e-134">Калибровка</span><span class="sxs-lookup"><span data-stu-id="5bb1e-134">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="5bb1e-135">Комфорт</span><span class="sxs-lookup"><span data-stu-id="5bb1e-135">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="5bb1e-136">Взгляд и фиксация</span><span class="sxs-lookup"><span data-stu-id="5bb1e-136">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="5bb1e-137">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="5bb1e-137">Voice input</span></span>](../../out-of-scope/voice-design.md)
