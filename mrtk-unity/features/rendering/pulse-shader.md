---
title: Шейдер импульсов
description: Описание для импульсных шейдеров в МРТК.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: e03c021689b6701b86ae25ba9fa253ece1368428
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144941"
---
# <a name="pulse-shader"></a><span data-ttu-id="8b84b-104">Импульсный шейдер</span><span class="sxs-lookup"><span data-stu-id="8b84b-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="8b84b-106">Используйте шейдер импульсов для анимации визуального влияния на реконструкция поверхности, сетку с выделенной рукой или любой другой сетки.</span><span class="sxs-lookup"><span data-stu-id="8b84b-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="8b84b-107">Шейдер и материал</span><span class="sxs-lookup"><span data-stu-id="8b84b-107">Shader and material</span></span>

<span data-ttu-id="8b84b-108">В следующих материалах используется **SR_Triangles** шейдер.</span><span class="sxs-lookup"><span data-stu-id="8b84b-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="8b84b-109">Можно настроить различные параметры, такие как цвет заливки, цвет линии и импульсный цвет.</span><span class="sxs-lookup"><span data-stu-id="8b84b-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="8b84b-110">**MRTK_Pulse_SpatialMeshBlue.**</span><span class="sxs-lookup"><span data-stu-id="8b84b-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="8b84b-111">**MRTK_Pulse_SpatialMeshPurple.**</span><span class="sxs-lookup"><span data-stu-id="8b84b-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="8b84b-112">**MRTK_Pulse_ArticulatedHandMeshBlue.**</span><span class="sxs-lookup"><span data-stu-id="8b84b-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="8b84b-113">**MRTK_Pulse_ArticulatedHandMeshPurple.**</span><span class="sxs-lookup"><span data-stu-id="8b84b-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="8b84b-114">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="8b84b-114">Prerequisites</span></span>

<span data-ttu-id="8b84b-115">Для примера пространственной сетки убедитесь, что MRTK_Pulse_ArticulatedHandMeshBlue. Material или MRTK_Pulse_ArticulatedHandMeshPurple. Material назначены в разделе Параметры МРТК-> пространственной осведомленности > параметры отображения — > видимый материал.</span><span class="sxs-lookup"><span data-stu-id="8b84b-115">For the spatial mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned under MRTK Settings -> Spatial Awareness -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="8b84b-116">В примере с сеткой в виде руки убедитесь, MRTK_Pulse_SpatialMeshPurple MRTK_Pulse_SpatialMeshBlue что в Артикулатедхандмеш. prefab назначено, что оно должно быть назначено в МРТК Settings-> input-> Tracking-> prefab.</span><span class="sxs-lookup"><span data-stu-id="8b84b-116">For the hand mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="8b84b-117">Принцип работы</span><span class="sxs-lookup"><span data-stu-id="8b84b-117">How it works</span></span>

<span data-ttu-id="8b84b-118">Шейдер сетки «рука» использует UVs для отображения импульса вдоль сетки, а также для появления ладоней.</span><span class="sxs-lookup"><span data-stu-id="8b84b-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="8b84b-119">Шейдер реконструкции поверхности использует позиции вершин для отображения импульса.</span><span class="sxs-lookup"><span data-stu-id="8b84b-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="8b84b-120">Пример пространственного сетки — Пулсешадерспатиалмешексампле. Unity</span><span class="sxs-lookup"><span data-stu-id="8b84b-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="8b84b-121">Как и в случае с оболочкой HoloLens 2, вы можете нажимать и воздушный поток с помощью руки, чтобы создать пулсинг воздействие на пространственной сети.</span><span class="sxs-lookup"><span data-stu-id="8b84b-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="8b84b-122">Пример сцены содержит объект Ексамплеспатиалмеш, который является тестом данных пространственной сетки для игрового режима Unity.</span><span class="sxs-lookup"><span data-stu-id="8b84b-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="8b84b-123">Этот объект будет отключен и скрыт на устройстве.</span><span class="sxs-lookup"><span data-stu-id="8b84b-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="8b84b-124">Сценарий **пулсешадерспатиалмешхандлер. CS** создает импульсный результат для пространственной сетки в позиции точки попадания, если `PulseOnSelect` имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="8b84b-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="8b84b-125">`Auto Pulse`Свойству также можно присвоить значение true в самом материале для повторяющейся анимации.</span><span class="sxs-lookup"><span data-stu-id="8b84b-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="8b84b-126">В примере сцены этот скрипт прикрепляется к Пулсешадерспатиалмешпарент prefab.</span><span class="sxs-lookup"><span data-stu-id="8b84b-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="8b84b-127">На этот prefab есть ссылка в профиле пространственного расположения с помощью свойства prefab пространственной сетки времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="8b84b-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="8b84b-128">Во время выполнения экземпляр Пулсешадерспатиалмешпарент prefab и добавляется в иерархию пространственной сетки (только на устройстве, это поведение нельзя наблюдать в редакторе).</span><span class="sxs-lookup"><span data-stu-id="8b84b-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="8b84b-129">Пример сетки с поддержкой руки — Пулсешадерхандмешексампле. Unity</span><span class="sxs-lookup"><span data-stu-id="8b84b-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="8b84b-130">В этом примере сцены демонстрируется визуализация сетки с помощью шейдера Pulse.</span><span class="sxs-lookup"><span data-stu-id="8b84b-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="8b84b-131">Когда устройство HoloLens обнаруживает руку, импульсная анимация запускается один раз.</span><span class="sxs-lookup"><span data-stu-id="8b84b-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="8b84b-132">Эта визуальная обратная связь может повысить уверенность в взаимодействии пользователя.</span><span class="sxs-lookup"><span data-stu-id="8b84b-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="8b84b-133">Сценарий **пулсешадерхандмешхандлер. CS** создает импульсный результат для назначенного материала.</span><span class="sxs-lookup"><span data-stu-id="8b84b-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="8b84b-134">По умолчанию флажок "обнаружено импульсное состояние" установлен.</span><span class="sxs-lookup"><span data-stu-id="8b84b-134">By default, 'Pulse On Hand Detected' is checked.</span></span>
