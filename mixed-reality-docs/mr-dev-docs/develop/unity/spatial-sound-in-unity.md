---
title: Пространственный звук в Unity
description: Узнайте, как воспроизводить и ослабление пространственных звуков из определенной трехмерной точки в сцене Unity с помощью примеров.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, Пространственный звук, ХРТФ, размер комнаты, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств смешанной реальности, спатиализер, переглагол
ms.openlocfilehash: ec2703aa89925cb68860670f574a1e43f672e247
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009274"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="5572c-104">Пространственный звук в Unity</span><span class="sxs-lookup"><span data-stu-id="5572c-104">Spatial sound in Unity</span></span>

<span data-ttu-id="5572c-105">Эта страница содержит ссылки на ресурсы для пространственного звука в Unity.</span><span class="sxs-lookup"><span data-stu-id="5572c-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="5572c-106">Параметры спатиализер</span><span class="sxs-lookup"><span data-stu-id="5572c-106">Spatializer options</span></span>

<span data-ttu-id="5572c-107">Параметры спатиализер для приложений смешанной реальности включают:</span><span class="sxs-lookup"><span data-stu-id="5572c-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="5572c-108">Unity предоставляет *Спатиализер MS хртф* в составе дополнительного пакета *Windows Mixed Reality* .</span><span class="sxs-lookup"><span data-stu-id="5572c-108">Unity provides the *MS HRTF Spatializer* as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="5572c-109">Работает на ЦП в архитектуре с одним источником с более высоким значением.</span><span class="sxs-lookup"><span data-stu-id="5572c-109">Runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="5572c-110">Предоставляется для обеспечения обратной совместимости с исходными приложениями HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5572c-110">Provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="5572c-111">*Microsoft спатиализер* доступен в [репозитории Microsoft спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="5572c-111">The *Microsoft Spatializer* is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="5572c-112">Использует более экономичную архитектуру с несколькими источниками.</span><span class="sxs-lookup"><span data-stu-id="5572c-112">Uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="5572c-113">Разгружается на аппаратный ускоритель в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5572c-113">Offloaded to a hardware accelerator on the HoloLens 2.</span></span> 

<span data-ttu-id="5572c-114">Для новых приложений мы рекомендуем использовать *Microsoft спатиализер*.</span><span class="sxs-lookup"><span data-stu-id="5572c-114">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="5572c-115">Включить пространственность</span><span class="sxs-lookup"><span data-stu-id="5572c-115">Enable spatialization</span></span>

<span data-ttu-id="5572c-116">Используйте [NuGet для Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) , чтобы установить _Microsoft. спатиалаудио. спатиализер. Unity_ , и выберите **Microsoft спатиализер** в параметрах звука проекта.</span><span class="sxs-lookup"><span data-stu-id="5572c-116">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="5572c-117">Затем сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="5572c-117">Then:</span></span>
* <span data-ttu-id="5572c-118">Присоединение **звукового источника** к объекту в иерархии</span><span class="sxs-lookup"><span data-stu-id="5572c-118">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="5572c-119">Установите флажок " **включить пространственность** "</span><span class="sxs-lookup"><span data-stu-id="5572c-119">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="5572c-120">Переместить ползунок **пространственного смешения** в "1"</span><span class="sxs-lookup"><span data-stu-id="5572c-120">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="5572c-121">Убедитесь, что на рабочей станции разработчика включен Пространственный звук.</span><span class="sxs-lookup"><span data-stu-id="5572c-121">Ensure spatial audio is enabled on your developer workstation.</span></span> 
    * <span data-ttu-id="5572c-122">Щелкните значок тома на панели задач правой кнопкой мыши и убедитесь, что для пространственного звука задано значение, отличное от "Выкл.".</span><span class="sxs-lookup"><span data-stu-id="5572c-122">Right-click on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off".</span></span> 
    * <span data-ttu-id="5572c-123">Выберите **Windows Sonic для наушников** , чтобы получить лучшее представление о том, что вы услышите в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5572c-123">Choose **Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

>[!NOTE]
><span data-ttu-id="5572c-124">Если в Unity появляется сообщение об отсутствии возможности загрузить подключаемый модуль Microsoft. Спатиалаудио. Спатиализер. Unity, поскольку отсутствует одна из его зависимостей, убедитесь, что на компьютере установлена последняя версия [распространяемого Microsoft Visual C++](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) .</span><span class="sxs-lookup"><span data-stu-id="5572c-124">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="5572c-125">Дополнительные сведения см. в разделе:</span><span class="sxs-lookup"><span data-stu-id="5572c-125">For more information, see:</span></span>
* [<span data-ttu-id="5572c-126">Репозиторий Microsoft спатиализер GitHub</span><span class="sxs-lookup"><span data-stu-id="5572c-126">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="5572c-127">Руководство Майкрософт по спатиализер</span><span class="sxs-lookup"><span data-stu-id="5572c-127">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="5572c-128">Документация по источнику аудио в Unity</span><span class="sxs-lookup"><span data-stu-id="5572c-128">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="5572c-129">Документация по спатиализер Unity</span><span class="sxs-lookup"><span data-stu-id="5572c-129">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="5572c-130">Затухание, связанное с расстоянием</span><span class="sxs-lookup"><span data-stu-id="5572c-130">Distance-based attenuation</span></span>

<span data-ttu-id="5572c-131">По умолчанию Unity на основе расстояния Decay имеет минимальное расстояние в 1 метра и максимальное расстояние 500 метров с логарифмической роллоффой.</span><span class="sxs-lookup"><span data-stu-id="5572c-131">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="5572c-132">Эти параметры могут работать в вашем сценарии, или вы обнаружите, что источники слишком быстро или слишком медленные.</span><span class="sxs-lookup"><span data-stu-id="5572c-132">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="5572c-133">Дополнительные сведения см. в разделе:</span><span class="sxs-lookup"><span data-stu-id="5572c-133">For more information, see:</span></span>
* <span data-ttu-id="5572c-134">[Создание звука в смешанной реальности](../../design/spatial-sound-design.md) для рекомендуемых параметров.</span><span class="sxs-lookup"><span data-stu-id="5572c-134">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="5572c-135">В [документации по источнику аудио в Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) приведены инструкции по установке этих кривых.</span><span class="sxs-lookup"><span data-stu-id="5572c-135">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="5572c-136">Переглагол</span><span class="sxs-lookup"><span data-stu-id="5572c-136">Reverb</span></span>

<span data-ttu-id="5572c-137">По умолчанию _Microsoft спатиализер_ отключает эффекты после спатиализер.</span><span class="sxs-lookup"><span data-stu-id="5572c-137">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="5572c-138">Для включения переглагола и других эффектов для пространственных источников:</span><span class="sxs-lookup"><span data-stu-id="5572c-138">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="5572c-139">Присоединение компонента **уровня отправки "воздействие комнаты** " к каждому источнику</span><span class="sxs-lookup"><span data-stu-id="5572c-139">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="5572c-140">Настройте кривую на уровне отправки для каждого источника, чтобы управлять усилением звука, отправляемого обратно в граф для обработки эффектов.</span><span class="sxs-lookup"><span data-stu-id="5572c-140">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="5572c-141">Дополнительные сведения см. [в главе 5 руководства по спатиализер](tutorials/unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="5572c-141">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="5572c-142">Примеры пространственных звуков Unity</span><span class="sxs-lookup"><span data-stu-id="5572c-142">Unity spatial sound examples</span></span>

<span data-ttu-id="5572c-143">Примеры пространственного звука в Unity см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="5572c-143">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="5572c-144">Демонстрации МРТК</span><span class="sxs-lookup"><span data-stu-id="5572c-144">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="5572c-145">[Пример проекта Microsoft спатиализер](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="5572c-145">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="5572c-146">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="5572c-146">Next Development Checkpoint</span></span>

<span data-ttu-id="5572c-147">Если вы пойдете из процесса разработки Unity, который мы собрали, то будете изучать основные строительные блоки в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5572c-147">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="5572c-148">Отсюда вы можете перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="5572c-148">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5572c-149">Текстовые</span><span class="sxs-lookup"><span data-stu-id="5572c-149">Text</span></span>](text-in-unity.md)

<span data-ttu-id="5572c-150">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="5572c-150">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="5572c-151">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="5572c-151">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="5572c-152">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="5572c-152">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="5572c-153">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5572c-153">See also</span></span>

* [<span data-ttu-id="5572c-154">Оформление звука в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="5572c-154">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="5572c-155">Руководство Майкрософт по спатиализер</span><span class="sxs-lookup"><span data-stu-id="5572c-155">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
