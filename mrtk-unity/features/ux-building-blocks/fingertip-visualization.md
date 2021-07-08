---
title: Удобное графическое представление
description: Обзор поправной визуализации в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, мртк, под рукой
ms.openlocfilehash: af23fdb9b618e276b7442405e54b7dccd141e4ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177536"
---
# <a name="fingertip-visualization"></a><span data-ttu-id="5c225-104">Удобное графическое представление</span><span class="sxs-lookup"><span data-stu-id="5c225-104">Fingertip visualization</span></span>

![Основной визуальный образ](../images/fingertip/MRTK_FingertipVisualization_Main.png)

<span data-ttu-id="5c225-106">Это позволяет пользователю распознать расстояние от целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="5c225-106">The fingertip affordance helps the user recognize the distance from the target object.</span></span> <span data-ttu-id="5c225-107">Визуальный элемент «Форма кольца» корректирует свой размер на основе расстояния от прочего до объекта.</span><span class="sxs-lookup"><span data-stu-id="5c225-107">The ring shape visual adjusts its size based on the distance from the fingertip to the object.</span></span> <span data-ttu-id="5c225-108">Эта визуализация в основном управляется компонентом `FingerCursor` (Assets/мртк/SDK/Features/UX/Prefabs/курсоры/финжеркурсор. prefab) (и script), который порождается как курсор prefab *покепоинтер*.</span><span class="sxs-lookup"><span data-stu-id="5c225-108">The fingertip visualization is primarily controlled by the `FingerCursor` (Assets/MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab) (and script) which is spawned as the cursor prefab of the *PokePointer*.</span></span> <span data-ttu-id="5c225-109">К другим компонентам визуализации относятся сценарий *проксимитилигхт* и шейдер *микседреалитистандард* .</span><span class="sxs-lookup"><span data-stu-id="5c225-109">Other components of the visualization include the *ProximityLight* script, and *MixedRealityStandard* shader.</span></span>

## <a name="how-to-use-the-fingertip-visualization"></a><span data-ttu-id="5c225-110">Как использовать удобное графическое представление</span><span class="sxs-lookup"><span data-stu-id="5c225-110">How to use the fingertip visualization</span></span>

<span data-ttu-id="5c225-111">По умолчанию с помощью высокодоступной визуализации будет работать в любой сцене Unity, настроенной на порождение Финжеркурсор.</span><span class="sxs-lookup"><span data-stu-id="5c225-111">By default the fingertip visualization will work in any Unity scene that is configured to spawn a FingerCursor.</span></span> <span data-ttu-id="5c225-112">Порождение Финжеркурсор происходит в *дефаултмикседреалититулкитконфигуратионпрофиле* в разделе:</span><span class="sxs-lookup"><span data-stu-id="5c225-112">Spawning of the FingerCursor occurs in the *DefaultMixedRealityToolkitConfigurationProfile* under:</span></span>

<span data-ttu-id="5c225-113">*Дефаултмикседреалитинпутсистемпрофиле > Дефаултмикседреалитинпутпоинтерпрофиле > PokePointer > FingerCursor*</span><span class="sxs-lookup"><span data-stu-id="5c225-113">*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*</span></span>

<span data-ttu-id="5c225-114">На высоком уровне высокопроизводительная визуализация работает с помощью светлого цвета для проецирования цветного градиента на всех ближайших поверхностях, принимающих индикаторы близости.</span><span class="sxs-lookup"><span data-stu-id="5c225-114">At a high level the fingertip visualization works by using a proximity light to project a colored gradient on any nearby surfaces that accept proximity lights.</span></span> <span data-ttu-id="5c225-115">Затем курсор пальца ищет соседние взаимодействующие поверхности, которые определяются родительским объектом `IMixedRealityNearPointer(s)` , чтобы выстроить круг с помощью пальца по мере перемещения пальца к поверхности.</span><span class="sxs-lookup"><span data-stu-id="5c225-115">The finger cursor then looks for any nearby interactable surfaces, which are determined by parent `IMixedRealityNearPointer(s)`, to align the finger ring with a surface as the finger moves towards a surface.</span></span> <span data-ttu-id="5c225-116">Когда палец приближается к поверхности, он также динамически анимируется с помощью свойств скругленного угла Микседреалитистандард шейдера.</span><span class="sxs-lookup"><span data-stu-id="5c225-116">As a finger approaches a surface the finger ring is also dynamically animated using the round corner properties of the MixedRealityStandard shader.</span></span>

## <a name="example-scene"></a><span data-ttu-id="5c225-117">Пример сцены</span><span class="sxs-lookup"><span data-stu-id="5c225-117">Example scene</span></span>

<span data-ttu-id="5c225-118">Вы можете найти проладонные примеры в практически любой сцене, которая работает с формулировками, но выделена в [сцене хандинтерактионексампле](../example-scenes/hand-interaction-examples.md).</span><span class="sxs-lookup"><span data-stu-id="5c225-118">You can find fingertip visualization examples in almost any scene that works with articulated hands, but is prominent in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md).</span></span>

![Состояния зрительных визуализаций](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a><span data-ttu-id="5c225-120">Свойства инспектора</span><span class="sxs-lookup"><span data-stu-id="5c225-120">Inspector properties</span></span>

<span data-ttu-id="5c225-121">**Финжеркурсор** Многие свойства курсора пальца наследуются от базового класса курсора.</span><span class="sxs-lookup"><span data-stu-id="5c225-121">**FingerCursor** Many of the finger cursor properties are inherited from the base cursor class.</span></span> <span data-ttu-id="5c225-122">К важным свойствам относятся крайние или соседние поля и ширина, которые обозначают анимацию круга в шейдере Микседреалитистандард.</span><span class="sxs-lookup"><span data-stu-id="5c225-122">Important properties include the far / near surface margins and widths which drive the finger ring animation in the MixedRealityStandard shader.</span></span> <span data-ttu-id="5c225-123">Для других свойств наведите указатель мыши на советы средства инспектора.</span><span class="sxs-lookup"><span data-stu-id="5c225-123">For other properties please hover over the inspector tool tips.</span></span>

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

<span data-ttu-id="5c225-124">**Проксимитилигхт** Параметры светлого расположения управляют тем, как светло выглядит при приближении к поверхности.</span><span class="sxs-lookup"><span data-stu-id="5c225-124">**ProximityLight** The proximity light settings control how the light looks when near and far from a surface.</span></span> <span data-ttu-id="5c225-125">Центрированный, средний и внешний цвета определяют градиентный вид освещения и могут быть настроены для цветовой палитры приложения.</span><span class="sxs-lookup"><span data-stu-id="5c225-125">The center, middle, and outer colors control the gradient look of the light and can be custom tailored for the color palette of your application.</span></span> <span data-ttu-id="5c225-126">Обратите внимание, что цвета — HDR (старший динамический диапазон), что позволяет пользователям допустить интенсивность близости к значениям, превышающим один.</span><span class="sxs-lookup"><span data-stu-id="5c225-126">Note, the colors are HDR (High Dynamic Range) to allow users to brighten the proximity light to values above one.</span></span> <span data-ttu-id="5c225-127">Для других свойств наведите указатель мыши на советы средства инспектора.</span><span class="sxs-lookup"><span data-stu-id="5c225-127">For other properties please hover over the inspector tool tips.</span></span>

<span data-ttu-id="5c225-128">**Шейдер микседреалитистандард** Шейдер Микседреалитистандард используется для многих эффектов в МРТК.</span><span class="sxs-lookup"><span data-stu-id="5c225-128">**MixedRealityStandard Shader** The MixedRealityStandard shader is used for many effects in the MRTK.</span></span> <span data-ttu-id="5c225-129">Два параметра, важные для проправной визуализации, — «близкое выцветание» и «освещение».</span><span class="sxs-lookup"><span data-stu-id="5c225-129">The two settings important for fingertip visualization are "Near Fade" and "Proximity Light."</span></span> <span data-ttu-id="5c225-130">Близкое выцветание позволяет объектам заменять или исчезать в виде камеры или освещения.</span><span class="sxs-lookup"><span data-stu-id="5c225-130">Near Fade allows objects to fade in / out as a camera or light nears them.</span></span> <span data-ttu-id="5c225-131">Убедитесь, что установлен флажок "освещение", чтобы индикаторы близости применялись к исчезновению (а не камере).</span><span class="sxs-lookup"><span data-stu-id="5c225-131">Make sure to check "Light" to allow proximity lights to drive the fade (rather than the camera).</span></span> <span data-ttu-id="5c225-132">Можно изменить значения параметров «начать появление» и «выцветание», чтобы обратить эффект от исчезновения.</span><span class="sxs-lookup"><span data-stu-id="5c225-132">You can reverse the values of "Fade Begin" and "Fade Complete" to reverse a fade.</span></span> <span data-ttu-id="5c225-133">Установите флажок "светлое близость" для любой поверхности, которую вы хотите сделать светлой.</span><span class="sxs-lookup"><span data-stu-id="5c225-133">Check "Proximity Light" for any surface you would like the proximity light to brighten.</span></span> <span data-ttu-id="5c225-134">Для других свойств наведите указатель мыши на советы средства инспектора.</span><span class="sxs-lookup"><span data-stu-id="5c225-134">For other properties please hover over the inspector tool tips.</span></span>

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">