---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748545"
---
# <a name="mrtk"></a>[<span data-ttu-id="93109-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="93109-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="93109-102">Используйте класс [микседреалитиплайспаце](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) из Мртк для Unity и задайте **масштаб целевого объекта** **:** </span><span class="sxs-lookup"><span data-stu-id="93109-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![Окно параметров МРТК](../../images/mrtk-target-scale.png)

<span data-ttu-id="93109-104">МРТК должен автоматически управлять положением плайспаце и камеры, но рекомендуется дважды проверить следующее:</span><span class="sxs-lookup"><span data-stu-id="93109-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![МРТК плайспаце](../../images/mrtk-playspace.png)

1. <span data-ttu-id="93109-106">На панели **Иерархия** разверните узел **микседреалитиплайспаце** GameObject и найдите основной дочерний объект **Camera** .</span><span class="sxs-lookup"><span data-stu-id="93109-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="93109-107">На панели **инспектора** найдите компонент **Преобразование** и измените его **Расположение** на **(X: 0, Y: 0, Z: 0)** .</span><span class="sxs-lookup"><span data-stu-id="93109-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="93109-108">Пакет SDK для XR</span><span class="sxs-lookup"><span data-stu-id="93109-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="93109-109">Задайте режим источника отслеживания для [ксринпутсубсистем](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="93109-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="93109-110">После получения подсистемы вызовите [трисеттраккингоригинмоде](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="93109-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="93109-111">И работать с [Ксрриг](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)Unity.</span><span class="sxs-lookup"><span data-stu-id="93109-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![XRная платформа в иерархии](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="93109-113">Устаревшая версия WSA</span><span class="sxs-lookup"><span data-stu-id="93109-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="93109-114">В разделе " **другие параметры** " окна " **Параметры проигрывателя магазина Windows** "</span><span class="sxs-lookup"><span data-stu-id="93109-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="93109-115">Выберите **Windows Mixed Reality** в качестве устройства, которое может быть указано как **Windows holographic** в более ранних версиях Unity.</span><span class="sxs-lookup"><span data-stu-id="93109-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="93109-116">Выбрать **поддерживаемую виртуальную реальность**</span><span class="sxs-lookup"><span data-stu-id="93109-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="93109-117">Так как основной объект Camera автоматически помечается как камера, Unity перемещает все движения и перевод.</span><span class="sxs-lookup"><span data-stu-id="93109-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="93109-118">Эти параметры должны применяться к камере в каждой сцене приложения.</span><span class="sxs-lookup"><span data-stu-id="93109-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="93109-119">По умолчанию при создании новой сцены в Unity она будет содержать главную GameObject камеры в иерархии, которая включает компонент камеры, но не имеет правильно примененных параметров.</span><span class="sxs-lookup"><span data-stu-id="93109-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="93109-120">**Пространство имен:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="93109-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="93109-121">**Тип:** *ксрдевице*</span><span class="sxs-lookup"><span data-stu-id="93109-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="93109-122">Для работы с фиксированным **масштабированием** или **комнатным масштабированием** необходимо разместить содержимое относительно основания.</span><span class="sxs-lookup"><span data-stu-id="93109-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="93109-123">Вы указываете на этаж пользователя с помощью **[пространственного этапа](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, который представляет определенное пользователем происхождение на уровне пола и дополнительную границу комнаты, настраивается во время первого запуска.</span><span class="sxs-lookup"><span data-stu-id="93109-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="93109-124">Чтобы обеспечить работу Unity с своей мировой системой координат на уровне пола, можно установить и проверить, что Unity использует тип пространства отслеживания Румскале:</span><span class="sxs-lookup"><span data-stu-id="93109-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* <span data-ttu-id="93109-125">Если Сеттраккингспацетипе возвращает значение true, Unity успешно переключил свою систему координат мира для мониторинга [промежуточного кадра ссылки](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="93109-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="93109-126">Если Сеттраккингспацетипе возвращает значение false, Unity не смог переключиться на промежуточный кадр ссылки, скорее всего потому, что пользователь не настроил этаж в своей среде.</span><span class="sxs-lookup"><span data-stu-id="93109-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="93109-127">Хотя возвращаемое значение false не является распространенным, оно может произойти, если этап настраивается в другой комнате, и устройство перемещается в текущую комнату без настройки нового этапа пользователем.</span><span class="sxs-lookup"><span data-stu-id="93109-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="93109-128">После того как приложение успешно установит тип пространства отслеживания Румскале, на этаж будут отображаться содержимое, помещенное на плоскости y = 0.</span><span class="sxs-lookup"><span data-stu-id="93109-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="93109-129">Источник 0, 0, 0 будет определять конкретное место в этаже, где пользователь стояли во время настройки комнаты, с параметром-Z, который соответствует направлению вперед во время установки.</span><span class="sxs-lookup"><span data-stu-id="93109-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>