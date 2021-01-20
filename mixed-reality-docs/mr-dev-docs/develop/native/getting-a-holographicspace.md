---
title: Получение HolographicSpace
description: Узнайте, как использовать API Холографикспаце для более holographic-отрисовки и пространственного ввода в приложениях смешанной реальности.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, Холографикспаце, CoreWindow, пространственный ввод, подготовка к просмотру, цепочка подкачки, ный фрейм, цикл обновления, цикл игры, кадр ссылки, локатабилити, пример кода, пошаговое руководство, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 215c3cbacd4c7975d05b3a1b3f3992c9198642f7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580918"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="c1c3c-104">Получение HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="c1c3c-104">Getting a HolographicSpace</span></span>

> [!NOTE]
> <span data-ttu-id="c1c3c-105">Эта статья связана с устаревшими собственными API-интерфейсами WinRT.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="c1c3c-106">Для новых проектов собственных приложений рекомендуется использовать **[API опенкср](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="c1c3c-107">Класс <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">холографикспаце</a> является порталом в holographic мире.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-107">The <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="c1c3c-108">Он контролирует иммерсивное визуализацию, предоставляет данные камеры и предоставляет доступ к API-интерфейсам пространственной причины.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-108">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="c1c3c-109">Вы создадите его для <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> приложения UWP или HWND приложения Win32.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-109">You'll create one for your UWP app's <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="c1c3c-110">Настройка holographic-дискового пространства</span><span class="sxs-lookup"><span data-stu-id="c1c3c-110">Set up the holographic space</span></span>

<span data-ttu-id="c1c3c-111">Создание объекта holographic — это первый шаг в создании приложения Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-111">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="c1c3c-112">Традиционные приложения Windows подготавливаются к цепочке переключения Direct3D, созданной для основного окна представления приложения.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-112">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="c1c3c-113">Эта цепочка подкачки отображается на планшете с помощью интерфейса пользователя Holographic.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-113">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="c1c3c-114">Чтобы сделать представление приложения более holographic, а не 2D-планшетом, создайте для его основного окна, а не цепочки буферов.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-114">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="c1c3c-115">Представление holographic-кадров, созданных с помощью этого holographic-места, помещает приложение в полноэкранный режим отрисовки.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-115">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="c1c3c-116">Для **приложения UWP** , [начиная с *шаблона приложения holographic DirectX 11 (Universal Windows)*](creating-a-holographic-directx-project.md), найдите этот код в методе **сетвиндов** в аппвиев. cpp:</span><span class="sxs-lookup"><span data-stu-id="c1c3c-116">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="c1c3c-117">Если вы создаете **приложение Win32** , [начиная с примера Win32 *басичолограм*](creating-a-holographic-directx-project.md#creating-a-win32-project), Взгляните на **app:: креатевиндовандхолографикспаце** для примера HWND.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-117">If you're building a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an HWND example.</span></span> <span data-ttu-id="c1c3c-118">Затем можно преобразовать его в иммерсивное окно HWND, создав связанный <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">холографикспаце</a>:</span><span class="sxs-lookup"><span data-stu-id="c1c3c-118">You can then convert it into an immersive HWND by creating an associated <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>

```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="c1c3c-119">После получения Холографикспаце для CoreWindowа UWP или Win32 HWND, Холографикспаце может работать с holographic-камерами, создавать системы координат и выполнять более holographic-рендеринг.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-119">Once you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, the HolographicSpace can handle holographic cameras, create coordinate systems, and do holographic rendering.</span></span> <span data-ttu-id="c1c3c-120">Текущий holographic-диск используется в нескольких местах шаблона DirectX:</span><span class="sxs-lookup"><span data-stu-id="c1c3c-120">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="c1c3c-121">Класс **DeviceResources** должен получить некоторую информацию из объекта холографикспаце, чтобы создать устройство Direct3D.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-121">The **DeviceResources** class needs to get some information from the HolographicSpace object to create the Direct3D device.</span></span> <span data-ttu-id="c1c3c-122">Это идентификатор адаптера DXGI, связанный с holographic-дисплеем.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-122">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="c1c3c-123">Класс <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">холографикспаце</a> использует устройство Direct3D 11 приложения для создания ресурсов на основе устройств и управления ими, например задними буферами для каждой из holographic камер.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-123">The <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="c1c3c-124">Если вы заинтересованы в том, какую функцию выполняет эта функция, вы найдете ее в DeviceResources. cpp.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-124">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="c1c3c-125">Функция **DeviceResources:: инитиализеусингхолографикспаце** показывает, как получить адаптер путем поиска LUID — и как выбрать адаптер по умолчанию, если предпочтительный адаптер не указан.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-125">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="c1c3c-126">В основном классе приложения для обновлений и отрисовки используется пространство с **аппвиев:: сетвиндов** или **app:: креатевиндовандхолографикспаце** .</span><span class="sxs-lookup"><span data-stu-id="c1c3c-126">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="c1c3c-127">В разделах ниже упоминаются имена функций из шаблона, например **аппвиев:: сетвиндов** , которые предполагают, что вы начали из шаблона приложения с шаблоном UWP, отображаемые фрагменты кода будут применяться одинаково в приложениях UWP и Win32.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-127">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="c1c3c-128">Далее мы рассмотрим процесс установки, который **сесолографикспаце** отвечает за в классе аппмаин.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-128">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="c1c3c-129">Подпишитесь на события камеры, создавайте и удаляйте ресурсы камеры.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-129">Subscribe to camera events, create, and remove camera resources</span></span>

<span data-ttu-id="c1c3c-130">Жизнь вашего приложения находится в его holographic, и просматривается с помощью одной или нескольких holographic камер, которые представляют различные перспективы сцены.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-130">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras, which represent different perspectives on the scene.</span></span> <span data-ttu-id="c1c3c-131">Теперь, когда у вас есть место, вы можете получить данные для более holographic камер.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-131">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="c1c3c-132">Приложение должно реагировать на события **камерааддед** , создавая все ресурсы, относящиеся к этой камере.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-132">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera.</span></span> <span data-ttu-id="c1c3c-133">Примером такого ресурса является представление целевого объекта отрисовки заднего буфера.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-133">An example of such a resource is your back buffer render target view.</span></span> <span data-ttu-id="c1c3c-134">Этот код можно увидеть в функции **DeviceResources:: сесолографикспаце** , вызываемой **Аппвиев:: сетвиндов** до того, как приложение создаст все holographic кадров:</span><span class="sxs-lookup"><span data-stu-id="c1c3c-134">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="c1c3c-135">Приложение также должно отвечать на события **камераремовед** , освобождая ресурсы, созданные для этой камеры.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-135">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="c1c3c-136">Из **DeviceResources:: сесолографикспаце**:</span><span class="sxs-lookup"><span data-stu-id="c1c3c-136">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="c1c3c-137">Обработчики событий должны выполнить некоторую работу, чтобы избежать плавного перетекания и отрисовки приложения.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-137">The event handlers must complete some work to keep holographic rendering flowing smoothly, and your app rendering at all.</span></span> <span data-ttu-id="c1c3c-138">Ознакомьтесь с кодом и комментариями для получения подробных сведений: в основном классе можно найти **онкамерааддед** и **онкамераремовед** , чтобы понять, как обрабатывается **m_cameraResourcesная** схема с помощью **DeviceResources**.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-138">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="c1c3c-139">Сейчас мы сосредоточены на Аппмаин и настройке, которые он делает для того, чтобы ваше приложение знало о holographic фотокамер.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-139">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="c1c3c-140">Учитывая это, важно отметить следующие два требования:</span><span class="sxs-lookup"><span data-stu-id="c1c3c-140">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="c1c3c-141">Для обработчика событий **камерааддед** приложение может работать асинхронно, чтобы завершить создание ресурсов и загрузку ресурсов для новой камеры Holographic.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-141">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="c1c3c-142">Приложения, которые используют более одного кадра для выполнения этой работы, должны запросить РБП и выполнить РБП после асинхронной загрузки.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-142">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously.</span></span> <span data-ttu-id="c1c3c-143">[Задачу PPL](/cpp/parallel/concrt/parallel-patterns-library-ppl) можно использовать для асинхронной работы.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-143">A [PPL task](/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="c1c3c-144">Приложение должно убедиться, что оно готово к отображению на этой камере сразу после выхода из обработчика событий или после завершения периода отсрочки.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-144">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="c1c3c-145">Выход из обработчика событий или завершение периода отсрочки сообщает системе, что ваше приложение готово к получению holographic с помощью включенной камеры.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-145">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="c1c3c-146">Когда приложение получает событие **камераремовед** , оно должно освободить все ссылки на задний буфер и сразу же выйти из функции.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-146">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="c1c3c-147">Сюда входят представления целевого объекта прорисовки и любой другой ресурс, который может содержать ссылку на [идксгиресаурце](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="c1c3c-147">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="c1c3c-148">Приложение также должно гарантировать, что задний буфер не прикрепляется в качестве целевого объекта отрисовки, как показано в **камераресаурцес:: релеасересаурцесфорбаккбуффер**.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-148">The app must also ensure that the back buffer isn't attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="c1c3c-149">Чтобы ускорить работу, приложение может освободить задний буфер, а затем запустить задачу для асинхронного завершения всех остальных действий по уничтожению камеры.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-149">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other tear down work for the camera.</span></span> <span data-ttu-id="c1c3c-150">Шаблон holographic App содержит задачу PPL, которую можно использовать для этой цели.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-150">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="c1c3c-151">Если вы хотите определить, когда в рамке отображается добавленная или удаленная камера, используйте свойства **холографикфраме** [аддедкамерас](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) и [ремоведкамерас](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .</span><span class="sxs-lookup"><span data-stu-id="c1c3c-151">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="c1c3c-152">Создание рамки ссылки для вашего holographic-содержимого</span><span class="sxs-lookup"><span data-stu-id="c1c3c-152">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="c1c3c-153">Содержимое вашего приложения должно быть размещено в [пространственной системе координат](coordinate-systems-in-directx.md) для подготовки к просмотру в холографикспаце.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-153">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="c1c3c-154">Система предоставляет два основных кадра справочника, которые можно использовать для создания системы координат для голограмм.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-154">The system provides two primary frames of reference, which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="c1c3c-155">В Windows holographic есть два вида опорных кадра: справочные фреймы, присоединенные к устройству, и ссылки на кадры, которые остаются стационарными при перемещении устройства через среду пользователя.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-155">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="c1c3c-156">Шаблон holographic App по умолчанию использует стационарный ссылочный фрейм. Это один из самых простых способов визуализации голограмм с блокировкой мира.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-156">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="c1c3c-157">Стационарные опорные кадры предназначены для стабилизации положений в текущем расположении устройства.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-157">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="c1c3c-158">Это означает, что координаты других устройств могут немного относиться к среде пользователя по мере того, как устройство узнает больше о пространстве вокруг него.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-158">This means that coordinates further from the device can drift slightly relative to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="c1c3c-159">Существует два способа создания стационарной рамки ссылки: получение системы координат с [пространственного этапа](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)или использование <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">спатиаллокатор</a>по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-159">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="c1c3c-160">Если вы создаете приложение Windows Mixed Reality для впечатляющих головных телефонов, рекомендуемой отправной точкой является [пространственный этап](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage).</span><span class="sxs-lookup"><span data-stu-id="c1c3c-160">If you're creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage).</span></span> <span data-ttu-id="c1c3c-161">На пространственном этапе также предоставляются сведения о возможностях надетыной гарнитуры проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-161">The spatial stage also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="c1c3c-162">Здесь мы покажем, как использовать <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">спатиаллокатор</a>по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-162">Here, we show how to use the default <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="c1c3c-163">Пространственный локатор представляет устройство Windows Mixed Reality и отслеживает движение устройства и предоставляет системы координат, которые могут быть понятны по отношению к его расположению.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-163">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="c1c3c-164">Из **аппмаин:: онхолографикдисплайисаваилаблечанжед**:</span><span class="sxs-lookup"><span data-stu-id="c1c3c-164">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="c1c3c-165">Создайте стационарный фрейм ссылки один раз при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-165">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="c1c3c-166">Это аналогично определению мировой системы координат, когда источник помещается в положение устройства при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-166">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="c1c3c-167">Этот ссылочный кадр не перемещается вместе с устройством.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-167">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="c1c3c-168">Из **аппмаин:: сесолографикспаце**:</span><span class="sxs-lookup"><span data-stu-id="c1c3c-168">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="c1c3c-169">Все ссылочные кадры имеют согласованное значение для объекта «сила притяжения», то есть ось y указывает на «up» в отношении среды пользователя.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-169">All reference frames are gravity aligned, meaning that the y-axis points "up" in relation to the user's environment.</span></span> <span data-ttu-id="c1c3c-170">Так как в Windows используются "правильные" системы координат, направление оси – z совпадает с направлением "вперед", когда создается ссылочный фрейм.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-170">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="c1c3c-171">Если для приложения требуется точное размещение отдельных голограмм, используйте <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">спатиаланчор</a> , чтобы привязать отдельную голограмму к положению в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-171">When your app requires precise placement of individual holograms, use a <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="c1c3c-172">Например, используйте пространственное привязку, когда пользователь указывает на точку, которая является специальным интересом.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-172">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="c1c3c-173">Позиции привязки не отменяют смещение, но их можно скорректировать.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-173">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="c1c3c-174">По умолчанию, когда привязка корректируется, она упрощает свою позицию в следующих нескольких кадрах после исправления.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-174">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="c1c3c-175">В зависимости от приложения, когда это происходит, может потребоваться выполнить корректировку другим способом (например, отложив его до тех пор, пока не появится голограмма).</span><span class="sxs-lookup"><span data-stu-id="c1c3c-175">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="c1c3c-176">Свойства <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">равкурдинатесистем</a> и <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">равкурдинатесистемаджустед</a> позволяют выполнять эти настройки.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-176">The <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="c1c3c-177">Реагирование на события изменения локатабилити</span><span class="sxs-lookup"><span data-stu-id="c1c3c-177">Respond to locatability changed events</span></span>

<span data-ttu-id="c1c3c-178">Для отрисовки голограмм, заблокированных в мире, устройство должно располагаться в мире.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-178">Rendering world-locked holograms requires the device to locate itself in the world.</span></span> <span data-ttu-id="c1c3c-179">Это может быть не всегда возможно из-за условий окружающей среды, и если да, то пользователь может столкнуться с визуальным индикатором прерывания отслеживания.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-179">This may not always be possible because of environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="c1c3c-180">Этот визуальный индикатор должен быть визуализирован с помощью ссылочных фреймов, присоединенных к устройству, а не по всему миру.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-180">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="c1c3c-181">Приложение может запросить уведомления, если отслеживание прервано по какой-либо причине.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-181">Your app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="c1c3c-182">Зарегистрируйтесь на событие Локатабилитичанжед, чтобы определить, когда устройство может найти себя в мире изменений.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-182">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="c1c3c-183">Из **аппмаин:: сесолографикспаце:**</span><span class="sxs-lookup"><span data-stu-id="c1c3c-183">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="c1c3c-184">Затем используйте это событие, чтобы определить, когда голограммы не могут быть отображены в нестационарном мире.</span><span class="sxs-lookup"><span data-stu-id="c1c3c-184">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1c3c-185">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c1c3c-185">See also</span></span>
* [<span data-ttu-id="c1c3c-186">Отрисовка в DirectX</span><span class="sxs-lookup"><span data-stu-id="c1c3c-186">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="c1c3c-187">Системы координат в DirectX</span><span class="sxs-lookup"><span data-stu-id="c1c3c-187">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)