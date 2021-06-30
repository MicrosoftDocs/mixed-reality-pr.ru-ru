---
title: Платформа и среда выполнения
description: Сведения, связанные с платформой и средой выполнения в МРТК.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121612"
---
# <a name="framework-and-runtime"></a><span data-ttu-id="0f2c8-104">Платформа и среда выполнения</span><span class="sxs-lookup"><span data-stu-id="0f2c8-104">Framework and runtime</span></span>

## <a name="changes-to-the-scene"></a><span data-ttu-id="0f2c8-105">Изменения сцены</span><span class="sxs-lookup"><span data-stu-id="0f2c8-105">Changes to the scene</span></span>

<span data-ttu-id="0f2c8-106">Чтобы использовать набор средств, экземпляр скрипта Микседреалититулкит должен находиться в сцене.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-106">To use the toolkit an instance of the MixedRealityToolkit script must be in your scene.</span></span>
<span data-ttu-id="0f2c8-107">Чтобы добавить его, используйте пункт меню: набор средств для смешанной реальности — > добавить в сцену и настроить.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-107">To add one use the menu option: Mixed Reality Toolkit -> Add to Scene and Configure.</span></span> <span data-ttu-id="0f2c8-108">Этот экземпляр отвечает за регистрацию, обновление и уничтожение служб.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-108">This instance is responsible for registering, updating and tearing down services.</span></span> <span data-ttu-id="0f2c8-109">Здесь также выбран профиль конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-109">It's also where your configuration profile is chosen.</span></span>

<span data-ttu-id="0f2c8-110">Помимо добавления МРТК GameObject к сцене, команда меню также будет:</span><span class="sxs-lookup"><span data-stu-id="0f2c8-110">Apart from adding the MRTK GameObject to the scene the menu option will also:</span></span>

- <span data-ttu-id="0f2c8-111">Добавьте Микседреалитиплайспаце, который используется многими другими компонентами МРТК, чтобы задать причину для преобразований мира и локального пространства.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-111">Add the MixedRealityPlayspace, which is used by many other MRTK components to reason over world and local space transformations.</span></span>
- <span data-ttu-id="0f2c8-112">Переместите основную камеру в качестве дочернего элемента Микседреалитиплайспаце (а также добавьте некоторые входные и посчитать связанные сценарии на главную камеру, которые помогут Унитюи и взгляните на связанные входные функции).</span><span class="sxs-lookup"><span data-stu-id="0f2c8-112">Move the main Camera as a child of the MixedRealityPlayspace (and also adding some input and gaze related scripts to the main Camera, which help power UnityUI and gaze related input functionality).</span></span>

## <a name="mixedrealitytoolkit-object-and-runtime"></a><span data-ttu-id="0f2c8-113">Объект Микседреалититулкит и среда выполнения</span><span class="sxs-lookup"><span data-stu-id="0f2c8-113">MixedRealityToolkit object and runtime</span></span>

<span data-ttu-id="0f2c8-114">МРТК имеет несколько основных служб.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-114">The MRTK has several core services.</span></span> <span data-ttu-id="0f2c8-115">Немного координировать друг друга; другие являются независимыми.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-115">Some coordinate with one another; others are independent.</span></span>
<span data-ttu-id="0f2c8-116">Все используют один и тот же жизненный цикл — запуск, регистрация, обновление и уничтожение. Этот жизненный цикл не отличается от жизненного цикла Unity.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-116">All share the same life cycle - startup, registration, update and teardown - and this life cycle stands apart from Unity's MonoBehaviour life cycle.</span></span> <span data-ttu-id="0f2c8-117">Эта [средняя запись](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) описывает некоторую часть фона и мотивации при этом подходе.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-117">This [medium post](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explains some of the background and motivation behind this approach.</span></span> <span data-ttu-id="0f2c8-118">МРТК содержит один объект, который управляет жизненным циклом и средой выполнения своих служб.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-118">MRTK has a single object that manages life and runtime of its services.</span></span>

<span data-ttu-id="0f2c8-119">Эта сущность гарантирует следующее.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-119">This entity ensures that:</span></span>

- <span data-ttu-id="0f2c8-120">При запуске игры обнаружение и инициализация служб выполняются в заранее определенном порядке.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-120">when the game starts, discovery and initialization of services happens in a pre-defined order.</span></span>
- <span data-ttu-id="0f2c8-121">Она предоставляет механизм для регистрации служб (т. е. «я поддерживал эту службу!») и другие вызывающие методы для хранения этих служб.</span><span class="sxs-lookup"><span data-stu-id="0f2c8-121">it provides a mechanism for services to register themselves (i.e. “I support this service!”) and for other callers to get a hold of those services.</span></span>
- <span data-ttu-id="0f2c8-122">Он предоставляет вызовы Update ()/Латеупдате () и пересылает их различным службам (т. е. через Упдатеаллсервицес/Латеупдатеаллсервицес).</span><span class="sxs-lookup"><span data-stu-id="0f2c8-122">it provides the Update()/LateUpdate() calls and forwards them onto the various services (i.e. via UpdateAllServices/LateUpdateAllServices).</span></span>
