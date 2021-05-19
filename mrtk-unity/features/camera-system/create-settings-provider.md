---
title: Создание поставщика параметров
description: поставщик данных для параметров камеры в МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 6ec3fc1c88c1a32334cb2869ad1994863e55bf9a
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144896"
---
# <a name="creating-a-camera-settings-provider"></a><span data-ttu-id="aa214-104">Создание поставщика параметров камеры</span><span class="sxs-lookup"><span data-stu-id="aa214-104">Creating a camera settings provider</span></span>

<span data-ttu-id="aa214-105">Система камеры является расширяемой системой для обеспечения поддержки конфигураций камер, зависящих от платформы.</span><span class="sxs-lookup"><span data-stu-id="aa214-105">The Camera system is an extensible system for providing support for platform specific camera configurations.</span></span> <span data-ttu-id="aa214-106">Чтобы добавить поддержку новой конфигурации камеры, может потребоваться поставщик настраиваемых параметров.</span><span class="sxs-lookup"><span data-stu-id="aa214-106">To add support for a new camera configuration, a custom settings provider may be required.</span></span>

> [!NOTE]
> <span data-ttu-id="aa214-107">Полный исходный код, используемый в этом примере, можно найти в папке **мртк/providers/унитяр** .</span><span class="sxs-lookup"><span data-stu-id="aa214-107">The complete source code used in this example can be found in the **MRTK/Providers/UnityAR** folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="aa214-108">Пространство имен и структура папок</span><span class="sxs-lookup"><span data-stu-id="aa214-108">Namespace and folder structure</span></span>

<span data-ttu-id="aa214-109">Поставщики данных могут распространяться одним из двух способов:</span><span class="sxs-lookup"><span data-stu-id="aa214-109">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="aa214-110">Сторонние надстройки</span><span class="sxs-lookup"><span data-stu-id="aa214-110">Third party add-ons</span></span>
1. <span data-ttu-id="aa214-111">Часть набора средств Microsoft Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="aa214-111">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="aa214-112">Процесс утверждения для отправки новых поставщиков данных в МРТК будет изменяться в зависимости от конкретного случая и будет передан на момент начального предложения.</span><span class="sxs-lookup"><span data-stu-id="aa214-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="aa214-113">Предложения можно отправлять, создавая новый [тип *запроса функции*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="aa214-113">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-ons"></a><span data-ttu-id="aa214-114">Сторонние надстройки</span><span class="sxs-lookup"><span data-stu-id="aa214-114">Third party add-ons</span></span>

<span data-ttu-id="aa214-115">**Пространство имен**</span><span class="sxs-lookup"><span data-stu-id="aa214-115">**Namespace**</span></span>

<span data-ttu-id="aa214-116">Поставщики данных должны иметь пространство имен для устранения потенциальных конфликтов имен.</span><span class="sxs-lookup"><span data-stu-id="aa214-116">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="aa214-117">Рекомендуется, чтобы пространство имен включало следующие компоненты.</span><span class="sxs-lookup"><span data-stu-id="aa214-117">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="aa214-118">Название компании, создающее надстройку</span><span class="sxs-lookup"><span data-stu-id="aa214-118">Company name producing the add-on</span></span>
- <span data-ttu-id="aa214-119">Область применения компонента</span><span class="sxs-lookup"><span data-stu-id="aa214-119">Feature area</span></span>

<span data-ttu-id="aa214-120">Например, поставщик параметров камеры, созданный и поставляемый компанией Contoso, может иметь значение *"contoso. микседреалити. Toolkit. Camera"*.</span><span class="sxs-lookup"><span data-stu-id="aa214-120">For example, a camera settings provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.Camera"*.</span></span>

<span data-ttu-id="aa214-121">**Структура папок**</span><span class="sxs-lookup"><span data-stu-id="aa214-121">**Folder structure**</span></span>

<span data-ttu-id="aa214-122">Рекомендуется расположены исходный код для поставщиков данных в иерархии папок, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="aa214-122">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Пример структуры папок](../images/camera-system/ExampleProviderFolderStructure.png)

<span data-ttu-id="aa214-124">Где папка *контосокамера* содержит реализацию поставщика данных, папка *редактора* содержит инспектор (и любой другой код, относящийся к редактору Unity), а папка *Profiles* содержит один или несколько предварительно подготовленных объектов Profile.</span><span class="sxs-lookup"><span data-stu-id="aa214-124">Where the *ContosoCamera* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="aa214-125">Отправка МРТК</span><span class="sxs-lookup"><span data-stu-id="aa214-125">MRTK submission</span></span>

<span data-ttu-id="aa214-126">**Пространство имен**</span><span class="sxs-lookup"><span data-stu-id="aa214-126">**Namespace**</span></span>

<span data-ttu-id="aa214-127">Если поставщик параметров камеры отправляется в [репозиторий Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity), пространство имен **должно** начинаться с Microsoft. микседреалити. Toolkit (ex: *Microsoft. микседреалити. Toolkit. камерасистем*).</span><span class="sxs-lookup"><span data-stu-id="aa214-127">If a camera settings provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.CameraSystem*).</span></span>

<span data-ttu-id="aa214-128">**Структура папок**</span><span class="sxs-lookup"><span data-stu-id="aa214-128">**Folder structure**</span></span>

<span data-ttu-id="aa214-129">Весь код должен находиться в папке под МРТК или поставщиками (например: МРТК/providers/Унитяр).</span><span class="sxs-lookup"><span data-stu-id="aa214-129">All code must be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/UnityAR).</span></span>

## <a name="define-the-camera-settings-object"></a><span data-ttu-id="aa214-130">Определение объекта параметров камеры</span><span class="sxs-lookup"><span data-stu-id="aa214-130">Define the camera settings object</span></span>

<span data-ttu-id="aa214-131">Первым шагом в создании поставщика параметров камеры является определение типа данных (например, сеток или плоскостей), которые будут предоставляться приложениям.</span><span class="sxs-lookup"><span data-stu-id="aa214-131">The first step in creating a camera settings provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="aa214-132">Все объекты пространственных данных должны реализовывать [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="aa214-132">All spatial data objects must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.</span></span>

## <a name="implement-the-settings-provider"></a><span data-ttu-id="aa214-133">Реализация поставщика параметров</span><span class="sxs-lookup"><span data-stu-id="aa214-133">Implement the settings provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="aa214-134">Укажите наследование интерфейса и/или базового класса</span><span class="sxs-lookup"><span data-stu-id="aa214-134">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="aa214-135">Все поставщики параметров камеры должны реализовывать [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) интерфейс, который указывает минимальную функциональность, требуемую для системы камеры.</span><span class="sxs-lookup"><span data-stu-id="aa214-135">All camera settings providers must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, which specifies the minimum functionality required by the camera system.</span></span> <span data-ttu-id="aa214-136">МРТК Foundation включает класс, [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) который предоставляет реализацию требуемой функциональности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aa214-136">The MRTK foundation includes the [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) class which provides a default implementation of the required functionality.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="aa214-137">Применение атрибута Микседреалитидатапровидер</span><span class="sxs-lookup"><span data-stu-id="aa214-137">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="aa214-138">Ключевым шагом при создании поставщика параметров камеры является применение [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) атрибута к классу.</span><span class="sxs-lookup"><span data-stu-id="aa214-138">A key step in creating a camera settings provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="aa214-139">Этот шаг позволяет задать профиль и платформы по умолчанию для поставщика данных, если он выбран в профиле системы камеры, а также имя, путь к папке и т. д.</span><span class="sxs-lookup"><span data-stu-id="aa214-139">This step enables setting the default profile and platform(s) for the data provider, when selected in the Camera System profile as well as name, folder path, and more.</span></span>

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="aa214-140">Реализация методов Имикседреалитидатапровидер</span><span class="sxs-lookup"><span data-stu-id="aa214-140">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="aa214-141">После определения класса следующим шагом является предоставление реализации [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="aa214-141">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="aa214-142">[`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1)Класс через [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) класс предоставляет пустые реализации для [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) методов.</span><span class="sxs-lookup"><span data-stu-id="aa214-142">The [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="aa214-143">Сведения об этих методах обычно относятся к конкретному поставщику данных.</span><span class="sxs-lookup"><span data-stu-id="aa214-143">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="aa214-144">Поставщик данных должен реализовать следующие методы:</span><span class="sxs-lookup"><span data-stu-id="aa214-144">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> <span data-ttu-id="aa214-145">Не все поставщики параметров потребует реализации всех этих методов.</span><span class="sxs-lookup"><span data-stu-id="aa214-145">Not all settings providers will require implementations for all of these methods.</span></span> <span data-ttu-id="aa214-146">Настоятельно рекомендуется `Destroy()` и `Initialize()` реализовывать как минимум.</span><span class="sxs-lookup"><span data-stu-id="aa214-146">It is highly recommended that `Destroy()` and `Initialize()` be implemented at a minimum.</span></span>

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="aa214-147">Реализация логики поставщика данных</span><span class="sxs-lookup"><span data-stu-id="aa214-147">Implement the data provider logic</span></span>

<span data-ttu-id="aa214-148">Следующим шагом является добавление логики поставщика параметров путем реализации [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) .</span><span class="sxs-lookup"><span data-stu-id="aa214-148">The next step is to add the logic of the settings provider by implementing [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider).</span></span> <span data-ttu-id="aa214-149">Эта часть поставщика данных, как правило, зависит от конфигурации камеры.</span><span class="sxs-lookup"><span data-stu-id="aa214-149">This portion of the data provider will typically be camera configuration specific.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="aa214-150">Создание профиля и инспектора</span><span class="sxs-lookup"><span data-stu-id="aa214-150">Create the profile and inspector</span></span>

<span data-ttu-id="aa214-151">В наборе средств для смешанной реальности поставщики данных настраиваются с помощью [профилей](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="aa214-151">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="aa214-152">Определение профиля</span><span class="sxs-lookup"><span data-stu-id="aa214-152">Define the profile</span></span>

<span data-ttu-id="aa214-153">Содержимое профиля должно отражать параметры конфигурации, выбираемые разработчиком.</span><span class="sxs-lookup"><span data-stu-id="aa214-153">Profile contents should mirror the developer selectable configuration options.</span></span> <span data-ttu-id="aa214-154">Все настраиваемые пользователем свойства, определенные в каждом интерфейсе, также должны содержаться в профиле.</span><span class="sxs-lookup"><span data-stu-id="aa214-154">Any user configurable properties defined in each interface should also be contained with the profile.</span></span>

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

<span data-ttu-id="aa214-155">`CreateAssetMenu`Атрибут можно применить к классу Profile, чтобы клиенты могли создавать экземпляры профиля с помощью меню **Создание**  >    >  **профилей набора средств Mixed Reality**  >   .</span><span class="sxs-lookup"><span data-stu-id="aa214-155">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="aa214-156">Реализация инспектора</span><span class="sxs-lookup"><span data-stu-id="aa214-156">Implement the inspector</span></span>

<span data-ttu-id="aa214-157">Инспекторы профилей — это пользовательский интерфейс для настройки и просмотра содержимого профиля.</span><span class="sxs-lookup"><span data-stu-id="aa214-157">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="aa214-158">Каждый инспектор профилей должен расширять [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) класс.</span><span class="sxs-lookup"><span data-stu-id="aa214-158">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="aa214-159">`CustomEditor`Атрибут информирует Unity о типе ресурса, к которому применяется инспектор.</span><span class="sxs-lookup"><span data-stu-id="aa214-159">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="aa214-160">Создание определений сборок</span><span class="sxs-lookup"><span data-stu-id="aa214-160">Create assembly definition(s)</span></span>

<span data-ttu-id="aa214-161">Набор средств Mixed Reality использует файлы определения сборки ([. асмдеф](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) для указания зависимостей между компонентами, а также для помощи Unity при сокращении времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="aa214-161">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="aa214-162">Рекомендуется создавать файлы определения сборки для всех поставщиков данных и их компонентов редактора.</span><span class="sxs-lookup"><span data-stu-id="aa214-162">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="aa214-163">Используя [структуру папок](#namespace-and-folder-structure) в предыдущем примере, для поставщика данных контосокамера требуется два асмдеф файла.</span><span class="sxs-lookup"><span data-stu-id="aa214-163">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoCamera data provider.</span></span>

<span data-ttu-id="aa214-164">Первое определение сборки предназначено для поставщика данных.</span><span class="sxs-lookup"><span data-stu-id="aa214-164">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="aa214-165">В этом примере он будет называться Контосокамера и будет находиться в папке *контосокамера* в примере.</span><span class="sxs-lookup"><span data-stu-id="aa214-165">For this example, it will be called ContosoCamera and will be located in the example's *ContosoCamera* folder.</span></span> <span data-ttu-id="aa214-166">Это определение сборки должно задавать зависимость от Microsoft. Микседреалити. Toolkit и других сборок, от которых он зависит.</span><span class="sxs-lookup"><span data-stu-id="aa214-166">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="aa214-167">В определении сборки Контосокамераедитор будет указан инспектор профилей и код конкретного редактора.</span><span class="sxs-lookup"><span data-stu-id="aa214-167">The ContosoCameraEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="aa214-168">Этот файл должен находиться в корневой папке кода редактора.</span><span class="sxs-lookup"><span data-stu-id="aa214-168">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="aa214-169">В этом примере файл будет находиться в папке *контосокамера\едитор*</span><span class="sxs-lookup"><span data-stu-id="aa214-169">In this example, the file will be located in the *ContosoCamera\Editor* folder.</span></span> <span data-ttu-id="aa214-170">Это определение сборки будет содержать ссылку на сборку Контосокамера, а также:</span><span class="sxs-lookup"><span data-stu-id="aa214-170">This assembly definition will contain a reference to the ContosoCamera assembly as well as:</span></span>

- <span data-ttu-id="aa214-171">Microsoft. Микседреалити. Toolkit</span><span class="sxs-lookup"><span data-stu-id="aa214-171">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="aa214-172">Microsoft. Микседреалити. Toolkit. Editor. Инспекторы</span><span class="sxs-lookup"><span data-stu-id="aa214-172">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="aa214-173">Microsoft. Микседреалити. Toolkit. Editor. Utilities</span><span class="sxs-lookup"><span data-stu-id="aa214-173">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="aa214-174">Регистрация поставщика данных</span><span class="sxs-lookup"><span data-stu-id="aa214-174">Register the data provider</span></span>

<span data-ttu-id="aa214-175">После создания поставщик данных можно зарегистрировать в системе камеры для использования в приложении.</span><span class="sxs-lookup"><span data-stu-id="aa214-175">Once created, the data provider can be registered with the Camera system to be used in the application.</span></span>

![Выбор поставщика параметров камеры](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="aa214-177">Упаковка и распространение</span><span class="sxs-lookup"><span data-stu-id="aa214-177">Packaging and distribution</span></span>

<span data-ttu-id="aa214-178">Поставщики данных, распространяемые в виде компонентов третьих лиц, имеют конкретные сведения о упаковке и распределении в соответствии с предпочтениями разработчика.</span><span class="sxs-lookup"><span data-stu-id="aa214-178">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="aa214-179">Скорее всего, наиболее распространенным решением будет создание. пакет unitypackage и распространение через хранилище активов Unity.</span><span class="sxs-lookup"><span data-stu-id="aa214-179">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="aa214-180">Если поставщик данных отправлен и принят как часть пакета Microsoft Mixed Reality Toolkit, группа Microsoft МРТК будет упаковывать и распространять ее в рамках предложений МРТК.</span><span class="sxs-lookup"><span data-stu-id="aa214-180">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa214-181">См. также</span><span class="sxs-lookup"><span data-stu-id="aa214-181">See also</span></span>

- [<span data-ttu-id="aa214-182">Обзор системы поддержки камер</span><span class="sxs-lookup"><span data-stu-id="aa214-182">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="aa214-183">Класс `BaseCameraSettingsProvider`</span><span class="sxs-lookup"><span data-stu-id="aa214-183">`BaseCameraSettingsProvider` class</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [<span data-ttu-id="aa214-184">`IMixedRealityCameraSettingsProvider` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="aa214-184">`IMixedRealityCameraSettingsProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [<span data-ttu-id="aa214-185">`IMixedRealityDataProvider` взаимодействия</span><span class="sxs-lookup"><span data-stu-id="aa214-185">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
