---
ms.openlocfilehash: e79b14c19a452b5b78c6f8cf7ea24bd65bfa0eaa
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98605253"
---
# <a name="426"></a>[<span data-ttu-id="c298b-101">4.26</span><span class="sxs-lookup"><span data-stu-id="c298b-101">4.26</span></span>](#tab/426) 

## <a name="pv-camera-feed-setup"></a><span data-ttu-id="c298b-102">Настройка потока данных с фотовидеокамеры</span><span class="sxs-lookup"><span data-stu-id="c298b-102">PV Camera Feed Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c298b-103">Фото- и видеокамера реализована в подключаемых модулях для Windows Mixed Reality и OpenXR.</span><span class="sxs-lookup"><span data-stu-id="c298b-103">PV camera is implemented in both Windows Mixed Reality and OpenXR plugins.</span></span> <span data-ttu-id="c298b-104">Но для работы OpenXR необходимо установить [подключаемый модуль Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="c298b-104">However OpenXR needs [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) to be installed.</span></span> <span data-ttu-id="c298b-105">Кроме того, OpenXR имеет ограничение: камера может работать только с DirectX11 RHI.</span><span class="sxs-lookup"><span data-stu-id="c298b-105">Also OpenXR has current limitation, camera can work with DirectX11 RHI.</span></span> <span data-ttu-id="c298b-106">Это ограничение будет устранено в будущей версии Unreal.</span><span class="sxs-lookup"><span data-stu-id="c298b-106">This limitation will be fixed in a further Unreal version.</span></span> 

- <span data-ttu-id="c298b-107">В разделе **Project Settings > HoloLens** (Параметры проекта > HoloLens) включите возможность **Webcam** (Веб-камера):</span><span class="sxs-lookup"><span data-stu-id="c298b-107">In **Project Settings > HoloLens**, enable the **Webcam** capability:</span></span>

![Снимок экрана: параметры проекта HoloLens с выделенным свойством Webcam](../images/unreal-pvc-img-01.png)

- <span data-ttu-id="c298b-109">Создайте субъект с именем CamCapture и добавьте плоскость для визуализации данных с камеры:</span><span class="sxs-lookup"><span data-stu-id="c298b-109">Create a new actor called “CamCapture” and add a plane to render the camera feed:</span></span>

![Снимок экрана: субъект с добавленной плоскостью](../images/unreal-pvc-img-02.png)

- <span data-ttu-id="c298b-111">Добавьте субъект в сцену, создайте материал с именем CamTextureMaterial с параметром объекта текстуры и пример текстуры.</span><span class="sxs-lookup"><span data-stu-id="c298b-111">Add the actor to your scene, create a new material called CamTextureMaterial with a Texture Object Parameter, and a texture sample.</span></span>  <span data-ttu-id="c298b-112">Отправьте RGB-данные текстуры в выходной излучаемый цвет:</span><span class="sxs-lookup"><span data-stu-id="c298b-112">Send the texture’s rgb data to the output emissive color:</span></span>

![Схема материала и пример текстуры](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a><span data-ttu-id="c298b-114">Визуализация потока данных с фотовидеокамеры</span><span class="sxs-lookup"><span data-stu-id="c298b-114">Rendering the PV Camera Feed</span></span>

- <span data-ttu-id="c298b-115">В схеме CamCapture включите фотовидеокамеру:</span><span class="sxs-lookup"><span data-stu-id="c298b-115">In the CamCapture blueprint, turn on the PV Camera:</span></span>

![Схема функции Toggle ARCapture с включенной фотовидеокамерой](../images/unreal-pvc-img-04.png)

- <span data-ttu-id="c298b-117">Создайте экземпляр динамического материала из CamTextureMaterial и назначьте этот материал плоскости субъекта:</span><span class="sxs-lookup"><span data-stu-id="c298b-117">Create a dynamic material instance from CamTextureMaterial and assign this material to the actor’s plane:</span></span>

![Схема функции Create Dynamic Material Instance](../images/unreal-pvc-img-05.png)

- <span data-ttu-id="c298b-119">Получите текстуру из потока данных камеры и назначьте ее динамическому материалу (если она допустимая).</span><span class="sxs-lookup"><span data-stu-id="c298b-119">Get the texture from the camera feed and assign it to the dynamic material if it's valid.</span></span>  <span data-ttu-id="c298b-120">Если текстура не является допустимой, запустите таймер и повторите попытку после его истечения:</span><span class="sxs-lookup"><span data-stu-id="c298b-120">If the texture isn't valid, start a timer and try again after the timeout:</span></span>

![Схема текстуры из потока данных камеры, назначенной динамическому материалу](../images/unreal-pvc-img-06.png)

- <span data-ttu-id="c298b-122">Наконец, масштабируйте плоскость по пропорциям изображения камеры:</span><span class="sxs-lookup"><span data-stu-id="c298b-122">Finally, scale the plane by the camera image’s aspect ratio:</span></span>

![Схема плоскости, масштабированная относительно пропорций изображения с камеры](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a><span data-ttu-id="c298b-124">Поиск позиций камеры в мировом пространстве</span><span class="sxs-lookup"><span data-stu-id="c298b-124">Find Camera Positions in World Space</span></span>

<span data-ttu-id="c298b-125">Камера на HoloLens 2 смещена вертикально по отношению к позиции отслеживания головы на устройстве.</span><span class="sxs-lookup"><span data-stu-id="c298b-125">The camera on the HoloLens 2 is offset vertically from the device’s head tracking.</span></span>  <span data-ttu-id="c298b-126">Для компенсации такого смещения доступно несколько функций, которые позволяют определить положение камеры в абсолютном пространстве.</span><span class="sxs-lookup"><span data-stu-id="c298b-126">A few functions exist to locate the camera in world space to account for the offset.</span></span>

<span data-ttu-id="c298b-127">GetPVCameraToWorldTransform получает преобразование в абсолютном пространстве фотовидеокамеры, располагаясь на линзе камеры:</span><span class="sxs-lookup"><span data-stu-id="c298b-127">GetPVCameraToWorldTransform gets the transform in world space of the PV Camera and will be positioned on the camera lens:</span></span>

![Схема функции Get PVCamera to World Transform](../images/unreal-pvc-img-08.png)

<span data-ttu-id="c298b-129">GetWorldSpaceRayFromCameraPoint пускает луч из объектива камеры в сцену в абсолютном пространстве Unreal, чтобы определить содержимое пикселя в кадре камеры:</span><span class="sxs-lookup"><span data-stu-id="c298b-129">GetWorldSpaceRayFromCameraPoint casts a ray from the camera lens into the scene in Unreal world space to find a pixel's content in the camera frame:</span></span>

![Схема функции Get World Space Ray from Camera Point](../images/unreal-pvc-img-09.png)

<span data-ttu-id="c298b-131">GetPVCameraIntrinsics возвращает характерные значения камеры, которые можно использовать при обработке кадра камеры с помощью компьютерного зрения:</span><span class="sxs-lookup"><span data-stu-id="c298b-131">GetPVCameraIntrinsics returns the camera intrinsic values, which can be used when doing computer vision processing on a camera frame:</span></span>

![Схема функций Get PVCamera Intrinsics](../images/unreal-pvc-img-10.png)

<span data-ttu-id="c298b-133">Чтобы определить, что находится в реальном пространстве по определенной пиксельной координате, используйте трассировку линии с помощью луча абсолютного пространства:</span><span class="sxs-lookup"><span data-stu-id="c298b-133">To find what exists in world space at a particular pixel coordinate, use a line trace with the world space ray:</span></span>

![Схема луча мирового пространства, используемого для определения того, что находится в мировом пространстве по определенной координате](../images/unreal-pvc-img-11.png)

<span data-ttu-id="c298b-135">Здесь мы выпускаем из объектива камеры луч длиной 2 метра в верхнюю левую четверть кадра камеры.</span><span class="sxs-lookup"><span data-stu-id="c298b-135">Here we cast a 2-meter ray from the camera lens to the camera-space position ¼ from the top left of the frame.</span></span>  <span data-ttu-id="c298b-136">Затем мы используем результат попадания для визуализации той позиции, в которой существует объект в мировом пространстве:</span><span class="sxs-lookup"><span data-stu-id="c298b-136">Then use the hit result to render something where the object exists in world space:</span></span>

![Схема выпуска из объектива камеры луча длиной 2 метра в верхнюю левую четверть кадра камеры](../images/unreal-pvc-img-12.png)

<span data-ttu-id="c298b-138">При использовании пространственного сопоставления такая позиция попадания будет соответствовать поверхности, которую видит камера.</span><span class="sxs-lookup"><span data-stu-id="c298b-138">When using spatial mapping, this hit position will match the surface that the camera is seeing.</span></span>

## <a name="rendering-the-pv-camera-feed-in-c"></a><span data-ttu-id="c298b-139">Визуализация потока данных с фотовидеокамеры в C++</span><span class="sxs-lookup"><span data-stu-id="c298b-139">Rendering the PV Camera Feed in C++</span></span>

- <span data-ttu-id="c298b-140">Создание нового субъекта C++ с именем CamCapture</span><span class="sxs-lookup"><span data-stu-id="c298b-140">Create a new C++ actor called CamCapture</span></span>
- <span data-ttu-id="c298b-141">В файле build.cs проекта добавьте AugmentedReality в список PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="c298b-141">In the project’s build.cs, add “AugmentedReality” to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "AugmentedReality"
});
```

- <span data-ttu-id="c298b-142">в файле CamCapture.h включите ARBlueprintLibrary.h:</span><span class="sxs-lookup"><span data-stu-id="c298b-142">In CamCapture.h, include ARBlueprintLibrary.h</span></span>

```cpp
#include "ARBlueprintLibrary.h"
```

- <span data-ttu-id="c298b-143">Вам также нужно добавить локальные переменные для сетки и материала:</span><span class="sxs-lookup"><span data-stu-id="c298b-143">You also need to add local variables for the mesh and material:</span></span>

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- <span data-ttu-id="c298b-144">В файле CamCapture.cpp обновите конструктор для добавления статической сетки в сцену:</span><span class="sxs-lookup"><span data-stu-id="c298b-144">In CamCapture.cpp, update the constructor to add a static mesh to the scene:</span></span>

```cpp
ACamCapture::ACamCapture()
{
    PrimaryActorTick.bCanEverTick = true;

    // Load a mesh from the engine to render the camera feed to.
    StaticMesh = LoadObject<UStaticMesh>(nullptr, TEXT("/Engine/EngineMeshes/Cube.Cube"), nullptr, LOAD_None, nullptr);

    // Create a static mesh component to render the static mesh
    StaticMeshComponent = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CameraPlane"));
    StaticMeshComponent->SetStaticMesh(StaticMesh);

    // Scale and add to the scene
    StaticMeshComponent->SetWorldScale3D(FVector(0.1f, 1, 1));
    this->SetRootComponent(StaticMeshComponent);
}
```

<span data-ttu-id="c298b-145">В BeginPlay создайте экземпляр динамического материала из материала камеры в проекте, примените его к компоненту статической сетки и запустите камеру HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c298b-145">In BeginPlay create a dynamic material instance from the project’s camera material, apply it to the static mesh component, and start the HoloLens camera.</span></span> 
 
<span data-ttu-id="c298b-146">В редакторе щелкните CamTextureMaterial в обозревателе содержимого и выберите Copy Reference (Копировать ссылку), чтобы получить строку для CameraMatPath.</span><span class="sxs-lookup"><span data-stu-id="c298b-146">In the editor, right-click on the CamTextureMaterial in the content browser and select “Copy Reference” to get the string for CameraMatPath.</span></span>

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMaterial = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

<span data-ttu-id="c298b-147">В Tick получите текстуру с камеры, сопоставьте ее с параметром текстуры в материале CamTextureMaterial и масштабируйте компонент статической сетки по пропорциям кадра камеры:</span><span class="sxs-lookup"><span data-stu-id="c298b-147">In Tick get the texture from the camera, set it to the texture parameter in the CamTextureMaterial material, and scale the static mesh component by the camera frame’s aspect ratio:</span></span>

```cpp
void ACamCapture::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    // Dynamic material instance only needs to be set once.
    if(IsTextureParamSet)
    {
        return;
    }

    // Get the texture from the camera.
    UARTexture* ARTexture = UARBlueprintLibrary::GetARTexture(EARTextureType::CameraImage);
    if(ARTexture != nullptr)
    {
        // Set the shader's texture parameter (named "Param") to the camera image.
        DynamicMaterial->SetTextureParameterValue("Param", ARTexture);
        IsTextureParamSet = true;

        // Get the camera instrincs
        FARCameraIntrinsics Intrinsics;
        UARBlueprintLibrary::GetCameraIntrinsics(Intrinsics);

        // Scale the camera mesh by the aspect ratio.
        float R = (float)Intrinsics.ImageResolution.X / (float)Intrinsics.ImageResolution.Y;
        StaticMeshComponent->SetWorldScale3D(FVector(0.1f, R, 1));
    }
}
```

# <a name="425"></a>[<span data-ttu-id="c298b-148">4.25</span><span class="sxs-lookup"><span data-stu-id="c298b-148">4.25</span></span>](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="c298b-149">Отрисовка с фото- и видеокамеры для MRC</span><span class="sxs-lookup"><span data-stu-id="c298b-149">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="c298b-150">Для этого требуется **Unreal Engine версии 4.25** и выше.</span><span class="sxs-lookup"><span data-stu-id="c298b-150">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="c298b-151">Системные и пользовательские средства MRC выполняют съемку смешанной реальности, совмещая изображение с фотовидеокамеры и голограммы, которые отрисовываются приложением.</span><span class="sxs-lookup"><span data-stu-id="c298b-151">The system and custom MRC recorders create mixed reality captures by combining the PV Camera with holograms rendered by the app.</span></span>

<span data-ttu-id="c298b-152">По умолчанию для съемки смешанной реальности используется голографический вывод правого глаза.</span><span class="sxs-lookup"><span data-stu-id="c298b-152">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="c298b-153">В иммерсивном приложении вместо этого можно выбрать [отрисовку с фотовидеокамеры](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in).</span><span class="sxs-lookup"><span data-stu-id="c298b-153">If an immersive app chooses to [render from the PV Camera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), then that will be used instead.</span></span> <span data-ttu-id="c298b-154">Это улучшает соответствие между реальным миром и голограммами в видео MRC.</span><span class="sxs-lookup"><span data-stu-id="c298b-154">Rendering from the PV Camera improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="c298b-155">Чтобы включить отрисовку с фотовидеокамеры, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="c298b-155">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="c298b-156">Вызовите функции **SetEnabledMixedRealityCamera** и **ResizeMixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="c298b-156">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="c298b-157">Задайте размеры видеоизображения с помощью параметров **Size X** (Размер по X) и **Size Y** (Размер по Y).</span><span class="sxs-lookup"><span data-stu-id="c298b-157">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Третья камера](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="c298b-159">После этого Unreal будет обрабатывать запросы от MRC на отрисовку с точки зрения фото- и видеокамеры.</span><span class="sxs-lookup"><span data-stu-id="c298b-159">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="c298b-160">Приложению будет даваться команда на отрисовку с точки зрения фото- и видеокамеры только в том случае, если активирована [съемка смешанной реальности](/hololens/holographic-photos-and-videos).</span><span class="sxs-lookup"><span data-stu-id="c298b-160">Only when [Mixed Reality Capture](/hololens/holographic-photos-and-videos) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="c298b-161">Использование фото- и видеокамеры</span><span class="sxs-lookup"><span data-stu-id="c298b-161">Using the PV Camera</span></span>

<span data-ttu-id="c298b-162">Текстуру с веб-камеры можно получить в игре во время выполнения, но эту возможность необходимо включить в разделе **Edit > Project Settings** (Правка > Параметры проекта) редактора:</span><span class="sxs-lookup"><span data-stu-id="c298b-162">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="c298b-163">Выберите **Platforms > HoloLens > Capabilities** (Платформы > HoloLens > Возможности) и установите флажок **Webcam** (Веб-камера).</span><span class="sxs-lookup"><span data-stu-id="c298b-163">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="c298b-164">Чтобы начать запись с веб-камеры во время выполнения, вызовите функцию **StartCameraCapture**, а чтобы остановить запись, вызовите функцию **StopCameraCapture**.</span><span class="sxs-lookup"><span data-stu-id="c298b-164">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Запуск и остановка камеры](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="c298b-166">Отрисовка изображения</span><span class="sxs-lookup"><span data-stu-id="c298b-166">Rendering an image</span></span>
<span data-ttu-id="c298b-167">Для отрисовки изображения с камеры:</span><span class="sxs-lookup"><span data-stu-id="c298b-167">To render the camera image:</span></span>
1. <span data-ttu-id="c298b-168">Создайте динамический экземпляр материала на основе материала **PVCamMat** из проекта (см. снимок экрана ниже).</span><span class="sxs-lookup"><span data-stu-id="c298b-168">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="c298b-169">Сохраните новый динамический экземпляр материала в переменной **Material Instance Dynamic Object Reference** (Ссылка на динамический объект экземпляра материала).</span><span class="sxs-lookup"><span data-stu-id="c298b-169">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="c298b-170">Выберите этот динамический экземпляр материала в качестве материала объекта в сцене, где будет отрисовываться изображение с камеры.</span><span class="sxs-lookup"><span data-stu-id="c298b-170">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="c298b-171">Запустите таймер, по которому будет выполняться привязка изображения с камеры будет к материалу.</span><span class="sxs-lookup"><span data-stu-id="c298b-171">Start a timer that will be used to bind the camera image to the material.</span></span>

![Отрисовка камеры](../images/unreal-camera-render.PNG)

4. <span data-ttu-id="c298b-173">Создайте для этого таймера новую функцию (в нашем примере это **MaterialTimer**) и вызовите функцию **GetARCameraImage**, чтобы получить текстуру с веб-камеры.</span><span class="sxs-lookup"><span data-stu-id="c298b-173">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="c298b-174">Если эта текстура допустима, установите это изображение в качестве значения параметра текстуры в шейдере.</span><span class="sxs-lookup"><span data-stu-id="c298b-174">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="c298b-175">В противном случае снова запустите таймер обновления материала.</span><span class="sxs-lookup"><span data-stu-id="c298b-175">Otherwise, start the material timer again.</span></span>

![Текстура камеры с веб-камеры](../images/unreal-camera-texture.PNG)

5. <span data-ttu-id="c298b-177">У материала должен быть параметр с таким же именем, как имя параметра функции **SetTextureParameterValue**, привязанное к записи о цвете.</span><span class="sxs-lookup"><span data-stu-id="c298b-177">Make sure the material has a parameter that matches the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="c298b-178">Без этого параметра изображение с камеры не отобразится правильно.</span><span class="sxs-lookup"><span data-stu-id="c298b-178">Without the parameter, the camera image can't be displayed properly.</span></span>

![Текстура от камеры](../images/unreal-camera-material.PNG)