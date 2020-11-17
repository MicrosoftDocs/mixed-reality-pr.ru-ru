---
title: Точка фокусировки в Unity
description: Ручная настройка стабильности в Unity путем установки точки фокусировки
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, точка фокусировки, плоскость фокусировки, стабилизации плоскость, стабилизации точка, репроект, ЛСР, буфер глубины, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 48c0d26e89124b9dbfc1d108354fb6e751e51783
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678693"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="ba2b8-104">Точка фокусировки в Unity</span><span class="sxs-lookup"><span data-stu-id="ba2b8-104">Focus point in Unity</span></span>

<span data-ttu-id="ba2b8-105">**Пространство имен:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="ba2b8-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="ba2b8-106">**Тип**: *холографиксеттингс*</span><span class="sxs-lookup"><span data-stu-id="ba2b8-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="ba2b8-107">[Точка фокусировки](../platform-capabilities-and-apis/hologram-stability.md#reprojection) может быть настроена таким образом, чтобы предоставлять HoloLens указание о том, как лучше выполнять стабилизации на отображаемых в данный момент голограммах.</span><span class="sxs-lookup"><span data-stu-id="ba2b8-107">The [focus point](../platform-capabilities-and-apis/hologram-stability.md#reprojection) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="ba2b8-108">Если вы хотите задать точку фокусировки в Unity, необходимо задать каждый кадр с помощью *холографиксеттингс. сетфокуспоинтфорфраме ()*.</span><span class="sxs-lookup"><span data-stu-id="ba2b8-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="ba2b8-109">Если точка фокусировки не задана для рамки, будет использоваться плоскость стабилизации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ba2b8-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="ba2b8-110">По умолчанию в новых проектах Unity установлен параметр "включить совместное использование буфера глубины".</span><span class="sxs-lookup"><span data-stu-id="ba2b8-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="ba2b8-111">С помощью этого параметра приложение Unity, работающее на высококлассной гарнитуре или на HoloLens под управлением Windows 10 2018 апреля Update (RS4) или более поздней версии, будет отправлять в Windows буфер глубины, чтобы автоматически оптимизировать стабильность, без приложения, указывающего на точку фокусировки:</span><span class="sxs-lookup"><span data-stu-id="ba2b8-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="ba2b8-112">На увлекательной гарнитуре настольной системы это позволит репроектировать на основе глубины на уровне точек.</span><span class="sxs-lookup"><span data-stu-id="ba2b8-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="ba2b8-113">В HoloLens с обновлением Windows 10 от апреля 2018 или более поздней версии будет проанализирован буфер глубины, чтобы автоматически выбрать оптимальную плоскость стабилизации.</span><span class="sxs-lookup"><span data-stu-id="ba2b8-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="ba2b8-114">Любой из этих подходов должен обеспечить еще более высокое качество изображения без явной работы приложения, чтобы выбрать точку фокусировки для каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="ba2b8-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="ba2b8-115">Обратите внимание, что если вы предложит точку фокусировки вручную, это переопределит автоматическое поведение, описанное выше, и обычно снизит стабильность.</span><span class="sxs-lookup"><span data-stu-id="ba2b8-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="ba2b8-116">Как правило, при выполнении приложения на HoloLens, который еще не обновлялся до обновления Windows 10 апреля 2018, следует указывать только точку фокусировки вручную.</span><span class="sxs-lookup"><span data-stu-id="ba2b8-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="ba2b8-117">Пример</span><span class="sxs-lookup"><span data-stu-id="ba2b8-117">Example</span></span>

<span data-ttu-id="ba2b8-118">Существует множество способов задать точку фокусировки, как предлагается перегрузки, доступные в статической функции *сетфокуспоинтфорфраме* .</span><span class="sxs-lookup"><span data-stu-id="ba2b8-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="ba2b8-119">Ниже приведен простой пример для установки плоскости фокусировки на предоставленный объект для каждого кадра:</span><span class="sxs-lookup"><span data-stu-id="ba2b8-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

<span data-ttu-id="ba2b8-120">Обратите внимание, что приведенный выше простой код может привести к снижению стабильной стабильности, если объект, на который он нацелен, заканчивается за пользователем.</span><span class="sxs-lookup"><span data-stu-id="ba2b8-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="ba2b8-121">Именно поэтому следует установить флажок "включить совместное использование буфера глубины" вместо того, чтобы вручную указывать точку фокусировки.</span><span class="sxs-lookup"><span data-stu-id="ba2b8-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="ba2b8-122">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="ba2b8-122">Next Development Checkpoint</span></span>

<span data-ttu-id="ba2b8-123">Если вы используете точку контрольной точки разработки Unity, которую мы собрали, вы находитесь в процессе изучения возможностей платформы смешанной реальности и интерфейсов API.</span><span class="sxs-lookup"><span data-stu-id="ba2b8-123">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="ba2b8-124">Отсюда вы можете перейти к следующей теме:</span><span class="sxs-lookup"><span data-stu-id="ba2b8-124">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="ba2b8-125">[потеря слежения](tracking-loss-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="ba2b8-125">[Tracking loss](tracking-loss-in-unity.md)</span></span>

<span data-ttu-id="ba2b8-126">Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:</span><span class="sxs-lookup"><span data-stu-id="ba2b8-126">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ba2b8-127">Развертывание в HoloLens или в виде впечатляющих головных телефонов Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ba2b8-127">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="ba2b8-128">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#3-platform-capabilities-and-apis).</span><span class="sxs-lookup"><span data-stu-id="ba2b8-128">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

### <a name="see-also"></a><span data-ttu-id="ba2b8-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ba2b8-129">See also</span></span>
* [<span data-ttu-id="ba2b8-130">Плоскость стабилизации</span><span class="sxs-lookup"><span data-stu-id="ba2b8-130">Stabilization plane</span></span>](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
