---
title: Отслеживание взгляда — глаза и руки
description: Как использовать глаз в качестве основного указателя в сочетании с движением руки в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, Эйетраккинг,
ms.openlocfilehash: c9d5f23610d821aa1e50a3217a4be736601dc14d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143997"
---
# <a name="eyes--hand-interaction"></a><span data-ttu-id="0ac8e-104">Глаза + руки</span><span class="sxs-lookup"><span data-stu-id="0ac8e-104">Eyes + hand interaction</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="0ac8e-105">Как поддержать _движения вида + руки_ (взгляд глаз & руки)</span><span class="sxs-lookup"><span data-stu-id="0ac8e-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="0ac8e-106">На этой странице объясняется, как использовать глаз в качестве основного указателя в сочетании с движением руки.</span><span class="sxs-lookup"><span data-stu-id="0ac8e-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="0ac8e-107">В [мртк демонстрации отслеживания взглядов](../../example-scenes/eye-tracking-examples-overview.md)мы рассмотрим несколько примеров использования глаз + руки, например:</span><span class="sxs-lookup"><span data-stu-id="0ac8e-107">In our [MRTK eye tracking demos](../../example-scenes/eye-tracking-examples-overview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="0ac8e-108">[Выбор](eye-tracking-target-selection.md): взгляд на отдаленную кнопку и просто выполнение жеста сжатия для быстрого выбора.</span><span class="sxs-lookup"><span data-stu-id="0ac8e-108">[Selection](eye-tracking-target-selection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="0ac8e-109">**Размещение (в этой статье)**: свободно перемещайте голограмму на сцене, просто взглянув на нее, сжимает указатель пальца и палец, чтобы захватить его, а затем перемещайте его с помощью руки.</span><span class="sxs-lookup"><span data-stu-id="0ac8e-109">**Positioning (this article)**: Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="0ac8e-110">[Навигация](eye-tracking-navigation.md): просто взгляните на расположение, в котором вы хотите увеличить масштаб, продвигайтесь пальцем указателя и палец и изучите _свой руку, чтобы_ увеличить масштаб.</span><span class="sxs-lookup"><span data-stu-id="0ac8e-110">[Navigation](eye-tracking-navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="0ac8e-111">Обратите внимание, что в настоящее время МРТК разрабатывается так, что на расстоянии с расстоянием от руки в качестве приоритетных указателей фокуса выступает.</span><span class="sxs-lookup"><span data-stu-id="0ac8e-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="0ac8e-112">Это означает, что указатели взгляда на заголовки и глаза будут автоматически подавляться после обнаружения руки и снова станут видимыми после того, как будет говорить "Select".</span><span class="sxs-lookup"><span data-stu-id="0ac8e-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected and will become visible again after saying "Select".</span></span>
<span data-ttu-id="0ac8e-113">Однако это может быть не так, как вы хотели бы взаимодействовать на расстоянии, а вместо простого взаимодействия _"взгляд и фиксация"_ не зависит от наличия рук в представлении.</span><span class="sxs-lookup"><span data-stu-id="0ac8e-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="0ac8e-114">Как отключить руку</span><span class="sxs-lookup"><span data-stu-id="0ac8e-114">How to disable the hand ray</span></span>

<span data-ttu-id="0ac8e-115">Чтобы отключить указатель в виде луча, просто удалите _"дефаултконтроллерпоинтер"_ в параметре мртк _указателя на входные >_ .</span><span class="sxs-lookup"><span data-stu-id="0ac8e-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="0ac8e-116">Чтобы использовать глаза и руки, как описано выше в приложении, также убедитесь, что выполнены все [требования к использованию отслеживания взгляда](eye-tracking-basic-setup.md).</span><span class="sxs-lookup"><span data-stu-id="0ac8e-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](eye-tracking-basic-setup.md).</span></span>

![Удаление руки](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="0ac8e-118">Кроме того, вы можете узнать, как _эйетраккингдемопоинтерпрофиле_ входной профиль из образца пакета отслеживания взгляда будет настроен в качестве ссылки.</span><span class="sxs-lookup"><span data-stu-id="0ac8e-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

### <a name="how-to-keep-gaze-pointer-always-on"></a><span data-ttu-id="0ac8e-119">Как всегда оставаться указателем на указатель «взгляд»</span><span class="sxs-lookup"><span data-stu-id="0ac8e-119">How to keep gaze pointer always on</span></span>

<span data-ttu-id="0ac8e-120">Чтобы избежать автоматического подавления указателей на указатель или глаз при обнаружении руки, [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) можно указать, должно ли оно быть включено или отключено.</span><span class="sxs-lookup"><span data-stu-id="0ac8e-120">To avoid having the head or eye gaze pointers automatically suppressed once a hand is detected, the gaze [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) can be specified to control whether it should be on or off.</span></span>

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="0ac8e-121">См. [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span><span class="sxs-lookup"><span data-stu-id="0ac8e-121">See [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span></span>

---
[<span data-ttu-id="0ac8e-122">Вернуться к "Отслеживание взглядов в Микседреалититулкит"</span><span class="sxs-lookup"><span data-stu-id="0ac8e-122">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
