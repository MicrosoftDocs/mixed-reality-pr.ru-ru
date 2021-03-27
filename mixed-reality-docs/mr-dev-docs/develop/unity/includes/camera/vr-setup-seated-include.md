---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636377"
---
# <a name="mrtk"></a>[<span data-ttu-id="d8cf1-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="d8cf1-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d8cf1-102">Используйте класс [микседреалитиплайспаце](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) из Мртк для Unity и задайте для **целевого шкалы** значение **"** подключено":</span><span class="sxs-lookup"><span data-stu-id="d8cf1-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![Окно параметров МРТК](../../images/mrtk-target-scale.png)

<span data-ttu-id="d8cf1-104">МРТК должен автоматически управлять положением плайспаце и камеры, но рекомендуется дважды проверить следующее:</span><span class="sxs-lookup"><span data-stu-id="d8cf1-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![МРТК плайспаце](../../images/mrtk-playspace.png)

1. <span data-ttu-id="d8cf1-106">На панели **Иерархия** разверните узел **микседреалитиплайспаце** GameObject и найдите основной дочерний объект **Camera** .</span><span class="sxs-lookup"><span data-stu-id="d8cf1-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="d8cf1-107">На панели **инспектора** найдите компонент **Преобразование** и измените его **Расположение** на **(X: 0, Y: 0, Z: 0)** .</span><span class="sxs-lookup"><span data-stu-id="d8cf1-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="d8cf1-108">Пакет SDK для XR</span><span class="sxs-lookup"><span data-stu-id="d8cf1-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d8cf1-109">Задайте режим источника отслеживания для [ксринпутсубсистем](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="d8cf1-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="d8cf1-110">После получения подсистемы вызовите [трисеттраккингоригинмоде](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="d8cf1-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="d8cf1-111">И работать с [Ксрриг](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)Unity.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![XRная платформа в иерархии](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="d8cf1-113">Устаревший WSA</span><span class="sxs-lookup"><span data-stu-id="d8cf1-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="d8cf1-114">В разделе " **другие параметры** " окна " **Параметры проигрывателя магазина Windows** "</span><span class="sxs-lookup"><span data-stu-id="d8cf1-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="d8cf1-115">Выберите **Windows Mixed Reality** в качестве устройства, которое может быть указано как **Windows holographic** в более ранних версиях Unity.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="d8cf1-116">Выбрать **поддерживаемую виртуальную реальность**</span><span class="sxs-lookup"><span data-stu-id="d8cf1-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="d8cf1-117">Так как основной объект Camera автоматически помечается как камера, Unity перемещает все движения и перевод.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="d8cf1-118">Эти параметры должны применяться к камере в каждой сцене приложения.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="d8cf1-119">По умолчанию при создании новой сцены в Unity она будет содержать главную GameObject камеры в иерархии, которая включает компонент камеры, но не имеет правильно примененных параметров.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="d8cf1-120">**Пространство имен:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="d8cf1-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="d8cf1-121">**Тип:** *ксрдевице*</span><span class="sxs-lookup"><span data-stu-id="d8cf1-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="d8cf1-122">Чтобы создать **интерфейс с горизонтальной** **ориентацией** или с возможностями масштабирования, необходимо задать Unity как стационарный тип пространства отслеживания.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="d8cf1-123">Стационарное пространство отслеживания. устанавливает мировую систему координат Unity для отслеживания [стационарной рамки ссылки](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="d8cf1-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="d8cf1-124">В режиме нестационарного отслеживания содержимое, помещенное в редактор непосредственно перед расположением по умолчанию камеры (переадресация — Z), будет отображаться перед пользователем при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="d8cf1-125">**Пространство имен:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="d8cf1-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="d8cf1-126">**Тип:** *инпуттраккинг*</span><span class="sxs-lookup"><span data-stu-id="d8cf1-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="d8cf1-127">Для чистой **ориентации** , такой как видео-средство просмотра 360 (если позиционированные головные обновления насмарку иллюзию), можно установить [XR. Инпуттраккинг. Дисаблепоситионалтраккинг](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) имеет значение true:</span><span class="sxs-lookup"><span data-stu-id="d8cf1-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="d8cf1-128">Для **работы с возможностями масштабирования**, чтобы пользователь мог позже изменить центр исходного места, можно вызвать [XR. Метод Инпуттраккинг. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :</span><span class="sxs-lookup"><span data-stu-id="d8cf1-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="d8cf1-129">Если вы создаете [опыт](../../../../design/coordinate-systems.md)в области, вы можете изменить центр по всему миру в текущей позиции головного пользователя, вызвав **[XR. Метод Инпуттраккинг. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .</span><span class="sxs-lookup"><span data-stu-id="d8cf1-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>