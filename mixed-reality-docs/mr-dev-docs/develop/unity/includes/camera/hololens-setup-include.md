---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636320"
---
# <a name="mrtk"></a>[<span data-ttu-id="ade6a-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="ade6a-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ade6a-102">Следуйте этому пошаговому [руководству, чтобы](../../tutorials/mr-learning-base-01.md) добавить и автоматически настроить набор средств смешанной реальности в проекте Unity.</span><span class="sxs-lookup"><span data-stu-id="ade6a-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="ade6a-103">Кроме того, можно напрямую работать с классом [микседреалитиплайспаце](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) из Мртк для Unity и задать для **целевого масштаба** значение **World**:</span><span class="sxs-lookup"><span data-stu-id="ade6a-103">It's also possible to work directly with the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![Окно параметров МРТК](../../images/mrtk-target-scale.png)

<span data-ttu-id="ade6a-105">МРТК должен автоматически управлять положением плайспаце и камеры, но рекомендуется дважды проверить следующее:</span><span class="sxs-lookup"><span data-stu-id="ade6a-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![МРТК плайспаце](../../images/mrtk-playspace.png)

1. <span data-ttu-id="ade6a-107">На панели **Иерархия** разверните узел **микседреалитиплайспаце** GameObject и найдите основной дочерний объект **Camera** .</span><span class="sxs-lookup"><span data-stu-id="ade6a-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="ade6a-108">На панели **инспектора** найдите компонент **Преобразование** и измените его **Расположение** на **(X: 0, Y: 0, Z: 0)** .</span><span class="sxs-lookup"><span data-stu-id="ade6a-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="ade6a-109">Пакет SDK для XR</span><span class="sxs-lookup"><span data-stu-id="ade6a-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ade6a-110">Задайте режим источника отслеживания для [ксринпутсубсистем](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="ade6a-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="ade6a-111">После получения подсистемы вызовите [трисеттраккингоригинмоде](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="ade6a-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="ade6a-112">[Арсессион](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) можно использовать для приложений HoloLens, которые работают лучше с привязками и ARKit/Аркоре.</span><span class="sxs-lookup"><span data-stu-id="ade6a-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![Сеанс AR в иерархии](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="ade6a-114">Для сеанса AR и связанных компонентов требуется установка AR Foundation.</span><span class="sxs-lookup"><span data-stu-id="ade6a-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="ade6a-115">Можно также применить изменения камеры вручную, не используя Арсессион:</span><span class="sxs-lookup"><span data-stu-id="ade6a-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="ade6a-116">На панели **Иерархия** выберите **Главная камера** .</span><span class="sxs-lookup"><span data-stu-id="ade6a-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="ade6a-117">На панели **инспектора** найдите компонент **Преобразование** и измените его **Расположение** на **(X: 0, Y: 0, Z: 0)** .</span><span class="sxs-lookup"><span data-stu-id="ade6a-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="ade6a-118">![Камера на панели инспектора в Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="ade6a-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="ade6a-119">*Камера на панели инспектора в Unity*</span><span class="sxs-lookup"><span data-stu-id="ade6a-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="ade6a-120">Добавление **траккедпоседривер** к **основной камере**</span><span class="sxs-lookup"><span data-stu-id="ade6a-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="ade6a-121">Устаревший WSA</span><span class="sxs-lookup"><span data-stu-id="ade6a-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="ade6a-122">На панели **Иерархия** выберите **Главная камера** .</span><span class="sxs-lookup"><span data-stu-id="ade6a-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="ade6a-123">На панели **инспектора** найдите компонент **Преобразование** и измените его **Расположение** на **(X: 0, Y: 0, Z: 0)** .</span><span class="sxs-lookup"><span data-stu-id="ade6a-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="ade6a-124">![Камера на панели инспектора в Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="ade6a-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="ade6a-125">*Камера на панели инспектора в Unity*</span><span class="sxs-lookup"><span data-stu-id="ade6a-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="ade6a-126">В разделе " **другие параметры** " окна " **Параметры проигрывателя магазина Windows** "</span><span class="sxs-lookup"><span data-stu-id="ade6a-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="ade6a-127">Выберите **Windows Mixed Reality** в качестве устройства, которое может быть указано как **Windows holographic** в более ранних версиях Unity.</span><span class="sxs-lookup"><span data-stu-id="ade6a-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="ade6a-128">Выбрать **поддерживаемую виртуальную реальность**</span><span class="sxs-lookup"><span data-stu-id="ade6a-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="ade6a-129">Так как основной объект Camera автоматически помечается как камера, Unity перемещает все движения и перевод.</span><span class="sxs-lookup"><span data-stu-id="ade6a-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="ade6a-130">Эти параметры должны применяться к камере в каждой сцене приложения.</span><span class="sxs-lookup"><span data-stu-id="ade6a-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="ade6a-131">По умолчанию при создании новой сцены в Unity она будет содержать главную GameObject камеры в иерархии, которая включает компонент камеры, но может не иметь правильно примененных параметров.</span><span class="sxs-lookup"><span data-stu-id="ade6a-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>