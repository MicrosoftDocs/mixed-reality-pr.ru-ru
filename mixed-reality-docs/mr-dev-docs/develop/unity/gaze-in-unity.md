---
title: Взгляд в Unity
description: Взгляд — это основной способ, с помощью которого пользователи могут ориентироваться на голограммы, создаваемые приложением в смешанной реальности.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: взгляд на глаза, головной взгляд, Unity, голограмма, Смешанная реальность, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, МРТК, набор средств смешанной реальности
ms.openlocfilehash: ca33fef5a5a761df83ed7991b366cf711a5db224
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010365"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="6db09-104">Головной взгляд в Unity</span><span class="sxs-lookup"><span data-stu-id="6db09-104">Head-gaze in Unity</span></span>

<span data-ttu-id="6db09-105">[Взгляд](../../design/gaze-and-commit.md) — это основной способ, с помощью которого пользователи могут ориентироваться на [голограммы](../../discover/hologram.md) , создаваемые приложением в [смешанной реальности](../../discover/mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="6db09-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="6db09-106">Реализация головного взгляда</span><span class="sxs-lookup"><span data-stu-id="6db09-106">Implementing head-gaze</span></span>

<span data-ttu-id="6db09-107">По сути, вы определяете [головное взгляд](../../design/gaze-and-commit.md) , выполняя проекцию луча вперед от гарнитуры пользователя, чтобы узнать, что он касается.</span><span class="sxs-lookup"><span data-stu-id="6db09-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="6db09-108">В Unity расположение и направление головного пользователя предоставляются через [камеру](camera-in-unity.md), в частности [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [преобразование. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) и [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Disposition](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="6db09-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="6db09-109">Вызов функции [физик. райкаст](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) дает вам [райкассит](https://docs.unity3d.com/ScriptReference/RaycastHit.html) , содержащий сведения о конфликте, включая трехмерную точку конфликта, а другой GameObject — попадание в голову.</span><span class="sxs-lookup"><span data-stu-id="6db09-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="6db09-110">Пример: реализация Heading-взгляда</span><span class="sxs-lookup"><span data-stu-id="6db09-110">Example: Implement head-gaze</span></span>

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a><span data-ttu-id="6db09-111">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="6db09-111">Best practices</span></span>

<span data-ttu-id="6db09-112">Хотя в приведенном выше примере в цикле обновления создается один райкаст, чтобы найти целевые точки пользователя, мы рекомендуем использовать один объект для управления всеми процессами головного взгляда.</span><span class="sxs-lookup"><span data-stu-id="6db09-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="6db09-113">Объединение логики с помощью Head-взгляда позволит сохранить ценную вычислительную мощность приложения и ограничить райкастинг на один кадр.</span><span class="sxs-lookup"><span data-stu-id="6db09-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="6db09-114">Визуализация головного взгляда</span><span class="sxs-lookup"><span data-stu-id="6db09-114">Visualizing head-gaze</span></span>

<span data-ttu-id="6db09-115">Как и в случае с указателем мыши на компьютере, необходимо реализовать [курсор](../../design/cursors.md) , представляющий голову пользователя.</span><span class="sxs-lookup"><span data-stu-id="6db09-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="6db09-116">Знание содержимого, на которое нацелен пользователь, повышает уверенность в том, с чем они взаимодействуют.</span><span class="sxs-lookup"><span data-stu-id="6db09-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="6db09-117">Руководитель-взгляд в наборе средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="6db09-117">Head-gaze in the Mixed Reality Toolkit</span></span> 
<span data-ttu-id="6db09-118">Вы можете получить доступ к Head с помощью [диспетчера ввода](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) в мртк.</span><span class="sxs-lookup"><span data-stu-id="6db09-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="6db09-119">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="6db09-119">Next Development Checkpoint</span></span>

<span data-ttu-id="6db09-120">Если вы пойдете из пути разработки Unity, мы собрались, что вы в состоянии изучить стандартные блоки МРТК Core.</span><span class="sxs-lookup"><span data-stu-id="6db09-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="6db09-121">Отсюда можно перейти к следующему стандартному блоку:</span><span class="sxs-lookup"><span data-stu-id="6db09-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6db09-122">Жесты и контроллеры движений</span><span class="sxs-lookup"><span data-stu-id="6db09-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="6db09-123">Или перейдите к возможностям и API платформы смешанной реальности:</span><span class="sxs-lookup"><span data-stu-id="6db09-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="6db09-124">[общие возможности](shared-experiences-in-unity.md);</span><span class="sxs-lookup"><span data-stu-id="6db09-124">[Shared experiences](shared-experiences-in-unity.md)</span></span>

<span data-ttu-id="6db09-125">Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#2-core-building-blocks).</span><span class="sxs-lookup"><span data-stu-id="6db09-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="6db09-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6db09-126">See also</span></span>
* [<span data-ttu-id="6db09-127">Камера</span><span class="sxs-lookup"><span data-stu-id="6db09-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="6db09-128">Курсоры</span><span class="sxs-lookup"><span data-stu-id="6db09-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="6db09-129">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="6db09-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
