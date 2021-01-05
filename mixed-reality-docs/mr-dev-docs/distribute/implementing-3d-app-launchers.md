---
title: Реализация средств запуска трехмерных приложений (приложения UWP)
description: Как создать трехмерные программы запуска и логотипы для приложений и игр Windows Mixed Reality (распространяется через Microsoft Store) как на HoloLens, так и в иммерсивного (VR) гарнитурах.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, Эмблема, значок, моделирование, средство запуска, трехмерное средство запуска, плитка, динамический куб, глубокая ссылка, секондаритиле, вторичная плитка, UWP, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, XML, ограничивающий прямоугольник, Unity
ms.openlocfilehash: 38f0932f20e3660c91b87de7bcb9d66799d9a51a
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757501"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="716c3-104">Реализация средств запуска трехмерных приложений (приложения UWP)</span><span class="sxs-lookup"><span data-stu-id="716c3-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="716c3-105">Эта функция была добавлена как часть обновления 2017 в RS3 (Creator) для впечатляющих головных телефонов и поддерживается в HoloLens с обновлением Windows 10 от апреля 2018.</span><span class="sxs-lookup"><span data-stu-id="716c3-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="716c3-106">Убедитесь, что приложение предназначено для версии Windows SDK больше или равно 10.0.16299 на впечатляющих гарнитурах и 10.0.17125 в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="716c3-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="716c3-107">Последнюю Windows SDK можно найти [здесь](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="716c3-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="716c3-108">[Главная страница Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) — это отправная точка, в которой пользователи начинают работу перед запуском приложений.</span><span class="sxs-lookup"><span data-stu-id="716c3-108">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="716c3-109">При создании приложения UWP для Windows Mixed Reality приложения по умолчанию запускаются в виде двумерных планшетов с логотипом своего приложения.</span><span class="sxs-lookup"><span data-stu-id="716c3-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="716c3-110">При разработке функций для Windows Mixed Reality при необходимости можно определить трехмерное средство запуска для переопределения 2D-запуска по умолчанию для приложения.</span><span class="sxs-lookup"><span data-stu-id="716c3-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="716c3-111">Как правило, для запуска впечатляющих приложений, которые выводят пользователей из дома Windows Mixed Reality, рекомендуется использовать трехмерные запуски.</span><span class="sxs-lookup"><span data-stu-id="716c3-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home.</span></span> <span data-ttu-id="716c3-112">Если приложение активировано на месте, предпочтительнее использовать по умолчанию 2D Launcher.</span><span class="sxs-lookup"><span data-stu-id="716c3-112">The default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="716c3-113">Можно также создать [трехмерную глубину ссылки (секондаритиле)](#3d-deep-links-secondarytiles) в виде трехмерного модуля запуска для содержимого в ДВУХМЕРНОМ приложении UWP.</span><span class="sxs-lookup"><span data-stu-id="716c3-113">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="716c3-114">процесс создания средства запуска приложений 3D</span><span class="sxs-lookup"><span data-stu-id="716c3-114">3D app launcher creation process</span></span>

<span data-ttu-id="716c3-115">Создание средства запуска 3D-приложений состоит из трех этапов.</span><span class="sxs-lookup"><span data-stu-id="716c3-115">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="716c3-116">Проектирование и концепция</span><span class="sxs-lookup"><span data-stu-id="716c3-116">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="716c3-117">Моделирование и экспорт</span><span class="sxs-lookup"><span data-stu-id="716c3-117">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="716c3-118">Интеграция этого приложения в приложение (в этой статье)</span><span class="sxs-lookup"><span data-stu-id="716c3-118">Integrating it into your application (this article)</span></span>

<span data-ttu-id="716c3-119">Трехмерные ресурсы, которые будут использоваться в качестве запуска для приложения, должны быть созданы с использованием [руководств по разработке Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) для обеспечения совместимости.</span><span class="sxs-lookup"><span data-stu-id="716c3-119">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="716c3-120">Активы, которые не соответствуют этой спецификации разработки, не будут подготавливаться к просмотру на домашней странице Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="716c3-120">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="716c3-121">Настройка средства запуска 3D</span><span class="sxs-lookup"><span data-stu-id="716c3-121">Configuring the 3D launcher</span></span>

<span data-ttu-id="716c3-122">При создании нового проекта в Visual Studio создается простая стандартная плитка, которая отображает имя и логотип приложения.</span><span class="sxs-lookup"><span data-stu-id="716c3-122">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="716c3-123">Чтобы заменить это 2D-представление на настраиваемую трехмерную модель, измените манифест приложения, включив в него элемент "Микседреалитимодел" в определении плитки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="716c3-123">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="716c3-124">Чтобы вернуться к 2D-средству запуска, просто удалите определение Микседреалитимодел из манифеста.</span><span class="sxs-lookup"><span data-stu-id="716c3-124">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="716c3-125">XML</span><span class="sxs-lookup"><span data-stu-id="716c3-125">XML</span></span>

<span data-ttu-id="716c3-126">Сначала необходимо указать манифест пакета приложения в текущем проекте.</span><span class="sxs-lookup"><span data-stu-id="716c3-126">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="716c3-127">По умолчанию манифест будет называться Package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="716c3-127">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="716c3-128">Если вы используете Visual Studio, щелкните правой кнопкой мыши манифест в средстве просмотра решения и выберите **Просмотреть источник** , чтобы открыть XML-файл для редактирования.</span><span class="sxs-lookup"><span data-stu-id="716c3-128">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="716c3-129">В верхней части манифеста Добавьте схему uap5 и включите ее как игнорируемое пространство имен:</span><span class="sxs-lookup"><span data-stu-id="716c3-129">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="716c3-130">Затем укажите "Микседреалитимодел" в плитке по умолчанию для приложения:</span><span class="sxs-lookup"><span data-stu-id="716c3-130">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="716c3-131">Элемент Микседреалитимодел принимает путь к файлу, указывающий на трехмерный ресурс, хранящийся в пакете приложения.</span><span class="sxs-lookup"><span data-stu-id="716c3-131">The MixedRealityModel element accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="716c3-132">Сейчас поддерживаются только объемные модели, доставляемые с помощью формата файла GLBA и созданные в соответствии с [инструкциями по созданию трехмерных ресурсов Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) .</span><span class="sxs-lookup"><span data-stu-id="716c3-132">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="716c3-133">Ресурсы должны храниться в пакете приложения, и анимация в настоящее время не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="716c3-133">Assets must be stored in the app package and animation isn't currently supported.</span></span> <span data-ttu-id="716c3-134">Если параметр "Path" оставлен пустым, то вместо 3D-запуска будет отображаться 2D.</span><span class="sxs-lookup"><span data-stu-id="716c3-134">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="716c3-135">**Примечание** . ресурс. GLBA должен быть помечен как "Content" в параметрах сборки перед сборкой и запуском приложения.</span><span class="sxs-lookup"><span data-stu-id="716c3-135">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="716c3-136">![Выберите GLBA в обозревателе решений и в разделе "Свойства" пометьте его как "содержимое" в параметрах сборки.](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="716c3-136">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="716c3-137">*Выберите GLBA в обозревателе решений и в разделе "Свойства" пометьте его как "содержимое" в параметрах сборки.*</span><span class="sxs-lookup"><span data-stu-id="716c3-137">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="716c3-138">Ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="716c3-138">Bounding box</span></span>

<span data-ttu-id="716c3-139">Ограничивающий прямоугольник можно использовать для добавления дополнительной области буфера вокруг объекта.</span><span class="sxs-lookup"><span data-stu-id="716c3-139">A bounding box can be used to optionally add an extra buffer region around the object.</span></span> <span data-ttu-id="716c3-140">Ограничивающий прямоугольник задается с помощью центральной точки и экстентов, которые указывают расстояние от центра ограничивающего прямоугольника до его границ вдоль каждой оси.</span><span class="sxs-lookup"><span data-stu-id="716c3-140">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="716c3-141">Единицы для ограничивающего прямоугольника можно сопоставить с 1 единицей измерения.</span><span class="sxs-lookup"><span data-stu-id="716c3-141">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="716c3-142">Если ограничивающий прямоугольник не указан, он будет автоматически размещается в сетке объекта.</span><span class="sxs-lookup"><span data-stu-id="716c3-142">If a bounding box isn't provided, then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="716c3-143">Если предоставленный ограничивающий прямоугольник меньше, чем модель, размер будет изменен в соответствии с сеткой.</span><span class="sxs-lookup"><span data-stu-id="716c3-143">If the provided bounding box is smaller than the model, then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="716c3-144">Поддержка атрибута ограничивающего прямоугольника поступает вместе с обновлением Windows RS4 в качестве свойства элемента Микседреалитимодел.</span><span class="sxs-lookup"><span data-stu-id="716c3-144">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="716c3-145">Чтобы сначала определить ограничивающий прямоугольник в верхней части манифеста приложения, добавьте схему uap6 и включите ее как игнорируемые пространства имен:</span><span class="sxs-lookup"><span data-stu-id="716c3-145">To define a bounding box first at the top of the app manifest add the uap6 schema and include it as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="716c3-146">Затем на Микседреалитимодел задайте свойство Спатиалбаундингбокс, чтобы определить ограничивающий прямоугольник:</span><span class="sxs-lookup"><span data-stu-id="716c3-146">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="716c3-147">Использование Unity</span><span class="sxs-lookup"><span data-stu-id="716c3-147">Using Unity</span></span>

<span data-ttu-id="716c3-148">При работе с Unity проект должен быть создан и открыт в Visual Studio, прежде чем можно будет изменить манифест приложения.</span><span class="sxs-lookup"><span data-stu-id="716c3-148">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="716c3-149">При создании и развертывании нового решения Visual Studio из Unity необходимо переопределить трехмерное средство запуска в манифесте.</span><span class="sxs-lookup"><span data-stu-id="716c3-149">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="716c3-150">Трехмерные глубокие ссылки (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="716c3-150">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="716c3-151">Эта функция была добавлена в составе обновления 2017 (RS3) для "иммерсивное" (VR), а также в рамках обновления за Апрель 2018 (RS4) для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="716c3-151">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="716c3-152">Убедитесь, что приложение предназначено для версии Windows SDK больше или равно 10.0.16299 на наушниках (VR) и 10.0.17125 на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="716c3-152">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="716c3-153">Последнюю Windows SDK можно найти [здесь](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="716c3-153">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="716c3-154">Трехмерные глубокие ссылки (secondaryTiles) работают только с 2D-приложениями UWP.</span><span class="sxs-lookup"><span data-stu-id="716c3-154">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="716c3-155">Однако можно создать [средство запуска для 3D-приложения](implementing-3d-app-launchers.md) , чтобы запустить эксклюзивное приложение из домашней страницы Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="716c3-155">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="716c3-156">Вы можете улучшить приложения для Windows Mixed Reality, добавив возможность размещения трехмерных моделей из приложения на [домашней странице Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) в качестве глубоких ссылок на содержимое в двухмерном приложении, так же, как [2D-вторичные плитки](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) в меню "Пуск" Windows.</span><span class="sxs-lookup"><span data-stu-id="716c3-156">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="716c3-157">Например, можно создать 360 °, которые непосредственно связываются с приложением 360 ° Photo Viewer, или позволить пользователям размещать трехмерное содержимое из коллекции ресурсов, открывающей страницу сведений об авторе.</span><span class="sxs-lookup"><span data-stu-id="716c3-157">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="716c3-158">Это всего лишь два способа расширить функциональные возможности 2D-приложения с помощью трехмерного содержимого.</span><span class="sxs-lookup"><span data-stu-id="716c3-158">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="716c3-159">Создание трехмерного "Секондаритиле"</span><span class="sxs-lookup"><span data-stu-id="716c3-159">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="716c3-160">Вы можете поместить трехмерное содержимое из приложения, используя "secondaryTiles", определив модель смешанной реальности во время создания.</span><span class="sxs-lookup"><span data-stu-id="716c3-160">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="716c3-161">Модели смешанной реальности создаются путем ссылки на трехмерный ресурс в пакете приложения и при необходимости определения ограничивающего прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="716c3-161">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="716c3-162">Создание "secondaryTiles" из монопольного представления в настоящее время не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="716c3-162">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="716c3-163">Ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="716c3-163">Bounding box</span></span>

<span data-ttu-id="716c3-164">Ограничивающий прямоугольник можно использовать для добавления дополнительной области буфера вокруг объекта.</span><span class="sxs-lookup"><span data-stu-id="716c3-164">A bounding box can be used to add an extra buffer region around the object.</span></span> <span data-ttu-id="716c3-165">Ограничивающий прямоугольник задается с помощью центральной точки и экстентов, которые указывают расстояние от центра ограничивающего прямоугольника до его границ вдоль каждой оси.</span><span class="sxs-lookup"><span data-stu-id="716c3-165">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="716c3-166">Единицы для ограничивающего прямоугольника можно сопоставить с 1 единицей измерения.</span><span class="sxs-lookup"><span data-stu-id="716c3-166">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="716c3-167">Если ограничивающий прямоугольник не указан, он будет автоматически размещается в сетке объекта.</span><span class="sxs-lookup"><span data-stu-id="716c3-167">If a bounding box isn't provided, one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="716c3-168">Если предоставленный ограничивающий прямоугольник меньше, чем модель, размер будет изменен в соответствии с сеткой.</span><span class="sxs-lookup"><span data-stu-id="716c3-168">If the provided bounding box is smaller than the model, it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="716c3-169">Поведение при активации</span><span class="sxs-lookup"><span data-stu-id="716c3-169">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="716c3-170">Эта функция будет поддерживаться в рамках обновления Windows RS4.</span><span class="sxs-lookup"><span data-stu-id="716c3-170">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="716c3-171">Убедитесь, что приложение предназначено для версии Windows SDK больше или равно 10.0.17125, если вы планируете использовать эту функцию</span><span class="sxs-lookup"><span data-stu-id="716c3-171">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="716c3-172">Вы можете определить поведение при активации трехмерного Секондаритиле, чтобы управлять тем, как оно будет реагировать, когда пользователь выберет его.</span><span class="sxs-lookup"><span data-stu-id="716c3-172">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="716c3-173">Это можно использовать для размещения трехмерных объектов на домашней странице Mixed Reality, которые являются исключительно информативными или декоративными.</span><span class="sxs-lookup"><span data-stu-id="716c3-173">This can be used to place 3D objects in the Mixed Reality home that are purely informative or decorative.</span></span> <span data-ttu-id="716c3-174">Поддерживаются следующие типы поведения активации:</span><span class="sxs-lookup"><span data-stu-id="716c3-174">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="716c3-175">По умолчанию: когда пользователь выбирает 3D-Секондаритиле, что приложение активируется</span><span class="sxs-lookup"><span data-stu-id="716c3-175">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="716c3-176">Нет: при выборе пользователем 3D Секондаритиле ничего не происходит, и приложение не активируется.</span><span class="sxs-lookup"><span data-stu-id="716c3-176">None: When the user selects the 3D secondaryTile nothing happens and the app isn't activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="716c3-177">Получение и обновление существующего "Секондаритиле"</span><span class="sxs-lookup"><span data-stu-id="716c3-177">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="716c3-178">Разработчики могут вернуть список существующих вторичных плиток, включающих ранее указанные свойства.</span><span class="sxs-lookup"><span data-stu-id="716c3-178">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="716c3-179">Они также могут обновлять свойства, изменяя значение и вызывая UpdateAsync ().</span><span class="sxs-lookup"><span data-stu-id="716c3-179">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="716c3-180">Проверка того, что пользователь находится в Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="716c3-180">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="716c3-181">Трехмерные ссылки (secondaryTiles) можно создавать только тогда, когда представление отображается на гарнитуре Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="716c3-181">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="716c3-182">Если представление не представлено на гарнитуре Windows Mixed Reality, рекомендуется правильно его обработать, либо скрыть точку входа, либо Показать сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="716c3-182">When your view isn't being presented in a Windows Mixed Reality headset, we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="716c3-183">Это можно проверить, выполнив запрос к [искуррентвиевпресентедонхолографик ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span><span class="sxs-lookup"><span data-stu-id="716c3-183">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="716c3-184">Уведомления на плитках</span><span class="sxs-lookup"><span data-stu-id="716c3-184">Tile notifications</span></span>

<span data-ttu-id="716c3-185">Уведомления плитки сейчас не поддерживают отправку обновлений в 3D-ресурс.</span><span class="sxs-lookup"><span data-stu-id="716c3-185">Tile notifications don't currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="716c3-186">Это означает, что разработчики не могут выполнять следующие действия:</span><span class="sxs-lookup"><span data-stu-id="716c3-186">This means that developers can't do the following:</span></span>

* <span data-ttu-id="716c3-187">Push-уведомления</span><span class="sxs-lookup"><span data-stu-id="716c3-187">Push Notifications</span></span>
* <span data-ttu-id="716c3-188">Периодическое опрос</span><span class="sxs-lookup"><span data-stu-id="716c3-188">Periodic Polling</span></span>
* <span data-ttu-id="716c3-189">Запланированные уведомления</span><span class="sxs-lookup"><span data-stu-id="716c3-189">Scheduled Notifications</span></span>

<span data-ttu-id="716c3-190">Дополнительные сведения о функциях и атрибутах других плиток, а также о том, как они используются для двумерных плиток, см. в [документации по плитке для приложений UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="716c3-190">For more information on the other tiles features and attributes and how they're used for 2D tiles, see the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="716c3-191">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="716c3-191">See also</span></span>

* <span data-ttu-id="716c3-192">[Образец модели Mixed Reality](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) , содержащий средство запуска 3D-приложения.</span><span class="sxs-lookup"><span data-stu-id="716c3-192">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="716c3-193">Руководство по проектированию средств запуска трехмерных приложений</span><span class="sxs-lookup"><span data-stu-id="716c3-193">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="716c3-194">Создание трехмерных моделей для использования на домашней странице Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="716c3-194">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="716c3-195">Реализация запуска трехмерных приложений (приложения Win32)</span><span class="sxs-lookup"><span data-stu-id="716c3-195">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="716c3-196">Навигация по дому с технологией Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="716c3-196">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
