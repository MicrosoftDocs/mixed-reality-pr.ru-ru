---
title: Руководство по babylon.js для подготовки сцены с базовыми трехмерными объектами
description: Узнайте, как использовать babylon.js и добавлять базовые трехмерные объекты в сцену.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: смешанная реальность, javascript, учебник, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, иммерсивное веб-приложение
ms.localizationpriority: high
ms.openlocfilehash: 8213c445da9c1bbf0eeb591b7995fb61bc6d5b5f
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584512"
---
# <a name="tutorial-prepare-a-scene"></a><span data-ttu-id="24286-104">Руководство. Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="24286-104">Tutorial: Prepare a scene</span></span>

<span data-ttu-id="24286-105">Узнайте, как подготовить сцену и добавить в нее некоторые основные трехмерные элементы.</span><span class="sxs-lookup"><span data-stu-id="24286-105">Learn how to prepare a scene, and add some basic 3D elements to it.</span></span>

<span data-ttu-id="24286-106">Из этого руководства вы узнаете, как выполнять следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="24286-106">In this tutorial, learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="24286-107">Создание сцены</span><span class="sxs-lookup"><span data-stu-id="24286-107">Create a scene</span></span>
> * <span data-ttu-id="24286-108">Добавление камеры</span><span class="sxs-lookup"><span data-stu-id="24286-108">Add a camera</span></span>
> * <span data-ttu-id="24286-109">Добавление света</span><span class="sxs-lookup"><span data-stu-id="24286-109">Add light</span></span>
> * <span data-ttu-id="24286-110">Добавление базовых трехмерных элементов</span><span class="sxs-lookup"><span data-stu-id="24286-110">Add basic 3D elements</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="24286-111">Подготовка к работе</span><span class="sxs-lookup"><span data-stu-id="24286-111">Before you begin</span></span>

<span data-ttu-id="24286-112">На предыдущем шаге руководства была создана базовая веб-страница.</span><span class="sxs-lookup"><span data-stu-id="24286-112">In previous tutorial step a basic web page was created.</span></span> <span data-ttu-id="24286-113">Откройте веб-страницу для редактирования.</span><span class="sxs-lookup"><span data-stu-id="24286-113">Have the web page open for editing.</span></span>

```html
<html>
    <head>
        <title>Babylon.js sample code</title>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
<body>
    <canvas id="renderCanvas"></canvas>
</body>
</html>
```

## <a name="create-a-scene"></a><span data-ttu-id="24286-114">Создание сцены</span><span class="sxs-lookup"><span data-stu-id="24286-114">Create a scene</span></span>

<span data-ttu-id="24286-115">Сцена — это место, где будет отображаться содержимое.</span><span class="sxs-lookup"><span data-stu-id="24286-115">A scene is where all the contents will be displayed.</span></span> <span data-ttu-id="24286-116">Может существовать несколько сцен, а также возможно переключение между ними.</span><span class="sxs-lookup"><span data-stu-id="24286-116">There might be multiple scenes and it is possible to switch between scenes.</span></span> <span data-ttu-id="24286-117">Подробнее о [сцене babylon.js](https://doc.babylonjs.com/divingDeeper/scene).</span><span class="sxs-lookup"><span data-stu-id="24286-117">Read more about [babylon.js Scene](https://doc.babylonjs.com/divingDeeper/scene).</span></span>

1. <span data-ttu-id="24286-118">Добавьте тег скрипта после элемента HTML Canvas и добавьте следующий код, чтобы создать сцену, заполненную черным цветом:</span><span class="sxs-lookup"><span data-stu-id="24286-118">Add the script tag after the canvas html element and add the following code to create a scene filled in black color:</span></span>

    ```html
    <script type="text/javascript">
        const canvas = document.getElementById("renderCanvas");
        const engine = new BABYLON.Engine(canvas, true);
        
        const createScene = function() {
            const scene = new BABYLON.Scene(engine);
            scene.clearColor = new BABYLON.Color3.Black;
            return scene;
        }

        const sceneToRender = createScene();
    </script>
    ```

    <span data-ttu-id="24286-119">В приведенном выше коде необходимо создать экземпляр babylon.js движка веб-отрисовки, который визуализирует сцену и привязывает события к холсту.</span><span class="sxs-lookup"><span data-stu-id="24286-119">In the code above we have to create an instance of babylon.js web rendering engine that renders a scene and hooks events on the canvas.</span></span> <span data-ttu-id="24286-120">Дополнительные сведения о движке см. на странице документации [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span><span class="sxs-lookup"><span data-stu-id="24286-120">For more information about the engine, check the documentation page [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span></span>

1. <span data-ttu-id="24286-121">По умолчанию сцена не отрисовывается.</span><span class="sxs-lookup"><span data-stu-id="24286-121">The scene is not rendered by default.</span></span> <span data-ttu-id="24286-122">Помните, что существует несколько сцен, и вы можете управлять тем, какая из них отображается.</span><span class="sxs-lookup"><span data-stu-id="24286-122">Remember, there might be multiple scenes and you control which scene is displayed.</span></span> <span data-ttu-id="24286-123">Для повторной отрисовки сцены в каждом кадре выполните следующий код после вызова функции *createScene*:</span><span class="sxs-lookup"><span data-stu-id="24286-123">To render the scene repeatedly on every frame, execute the following code after the call to *createScene* function:</span></span>

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a><span data-ttu-id="24286-124">Добавление базовых трехмерных элементов</span><span class="sxs-lookup"><span data-stu-id="24286-124">Add basic 3D element</span></span>

1. <span data-ttu-id="24286-125">Давайте добавим нашу первую трехмерную фигуру.</span><span class="sxs-lookup"><span data-stu-id="24286-125">Let's add our first 3D shape.</span></span> <span data-ttu-id="24286-126">В трехмерном виртуальном мире фигуры строятся на основе *сеток* — множестве треугольных поверхностей, соединенных друг с другом, каждая из которых состоит из трех вершин.</span><span class="sxs-lookup"><span data-stu-id="24286-126">In the 3D virtual world shapes are built from *meshes*, lots of triangular facets joined together, each facet made from three vertices.</span></span> <span data-ttu-id="24286-127">Можно использовать предопределенную сетку или создать собственную.</span><span class="sxs-lookup"><span data-stu-id="24286-127">You can either use a predefined mesh or create your own custom mesh.</span></span> <span data-ttu-id="24286-128">Здесь мы будем использовать стандартную сетку Box, т. е. куб.</span><span class="sxs-lookup"><span data-stu-id="24286-128">Here we will be using a predefined box mesh, i.e. a cube.</span></span> <span data-ttu-id="24286-129">Чтобы создать куб, используйте [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span><span class="sxs-lookup"><span data-stu-id="24286-129">To create the box use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span></span> <span data-ttu-id="24286-130">Сетка включает имя и параметры (они зависят от типа сетки).</span><span class="sxs-lookup"><span data-stu-id="24286-130">The parameters are name, and options (options are different according to the type of mesh).</span></span> <span data-ttu-id="24286-131">Добавьте следующий код в функцию *createScene*:</span><span class="sxs-lookup"><span data-stu-id="24286-131">Append the following code to the function *createScene*:</span></span>

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. <span data-ttu-id="24286-132">Откройте веб-страницу в браузере Microsoft Edge и проверьте выходные данные.</span><span class="sxs-lookup"><span data-stu-id="24286-132">Open the web page in the Microsoft Edge browser and check the output.</span></span> <span data-ttu-id="24286-133">В окне браузера отображается пустая страница.</span><span class="sxs-lookup"><span data-stu-id="24286-133">The browser window shows a blank page.</span></span> <span data-ttu-id="24286-134">Откройте DevTools с помощью клавиатуры и выберите F12 или CTRL+SHIFT+I (Windows, Linux) или Command+Option+I (macOS).</span><span class="sxs-lookup"><span data-stu-id="24286-134">Open DevTools by using the keyboard and select F12 or Control+Shift+I (Windows, Linux) or Command+Option+I (macOS).</span></span> <span data-ttu-id="24286-135">Открыв вкладку *Консоль*, можете начать поиск ошибок.</span><span class="sxs-lookup"><span data-stu-id="24286-135">After opening the *Console* tab, you can start looking for errors.</span></span> <span data-ttu-id="24286-136">Появится сообщение об ошибке: "Uncaught Error: No camera defined" (Необработанная ошибка: камера не найдена).</span><span class="sxs-lookup"><span data-stu-id="24286-136">There will be an error displayed: 'Uncaught Error: No camera defined'.</span></span> <span data-ttu-id="24286-137">Теперь необходимо добавить камеру в сцену.</span><span class="sxs-lookup"><span data-stu-id="24286-137">Now we have to add a camera to the scene.</span></span>

## <a name="add-a-camera"></a><span data-ttu-id="24286-138">Добавление камеры</span><span class="sxs-lookup"><span data-stu-id="24286-138">Add a camera</span></span>

1. <span data-ttu-id="24286-139">Чтобы просматривать виртуальный мир и взаимодействовать с ним, необходимо подключить к холсту камеру.</span><span class="sxs-lookup"><span data-stu-id="24286-139">In order to view the virtual world and interact with it, a camera must be attached to the canvas.</span></span> <span data-ttu-id="24286-140">Добавим камеру типа [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), которую можно поворачивать вокруг целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="24286-140">Let's add the camera of type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), which can be rotated around a target.</span></span> <span data-ttu-id="24286-141">Ниже приведены параметры, необходимые для создания экземпляра камеры.</span><span class="sxs-lookup"><span data-stu-id="24286-141">The parameters required to create an instance of the camera are:</span></span>
    1. <span data-ttu-id="24286-142">**name**: имя камеры;</span><span class="sxs-lookup"><span data-stu-id="24286-142">**name**: name of the camera</span></span>
    1. <span data-ttu-id="24286-143">**alpha**: угловое положение вдоль продольной оси (в радианах);</span><span class="sxs-lookup"><span data-stu-id="24286-143">**alpha**: angular position along the longitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="24286-144">**beta**: угловое положение вдоль широтной оси (в радианах);</span><span class="sxs-lookup"><span data-stu-id="24286-144">**beta**: angular position along the latitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="24286-145">**radius**: расстояние от целевого объекта;</span><span class="sxs-lookup"><span data-stu-id="24286-145">**radius**: distance from the target</span></span>
    1. <span data-ttu-id="24286-146">**target**: точка, к которой будет всегда направлена камера (определяется координатами X, Y и Z);</span><span class="sxs-lookup"><span data-stu-id="24286-146">**target**: the point that the camera would always face towards (defined by x-y-z coordinates)</span></span>
    1. <span data-ttu-id="24286-147">**scene**: сцена, в которой находится камера.</span><span class="sxs-lookup"><span data-stu-id="24286-147">**scene**: the scene that the camera is in</span></span>

    <span data-ttu-id="24286-148">Alpha, beta, radius и target определяют расположение камеры в пространстве, как показано на схеме ниже.</span><span class="sxs-lookup"><span data-stu-id="24286-148">Alpha, beta, radius, and target together define the camera's position in the space, as shown in the diagram below:</span></span>

    ![Камера, альфа, бета, радиус](../images/camera-alpha-beta-radius.jpg)

    <span data-ttu-id="24286-150">Добавьте следующий код в функцию *createScene*:</span><span class="sxs-lookup"><span data-stu-id="24286-150">Add the following code to the *createScene* function:</span></span>

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. <span data-ttu-id="24286-151">Если вы проверите результат в браузере, то увидите черный холст.</span><span class="sxs-lookup"><span data-stu-id="24286-151">If you check the output in the browser, you will see a black canvas.</span></span> <span data-ttu-id="24286-152">Отсутствует источник света.</span><span class="sxs-lookup"><span data-stu-id="24286-152">We are missing the light.</span></span>

## <a name="add-light"></a><span data-ttu-id="24286-153">Добавление света</span><span class="sxs-lookup"><span data-stu-id="24286-153">Add light</span></span>

1. <span data-ttu-id="24286-154">Существует четыре типа источников света, которые могут использоваться с различными свойствами освещения: точечный, направленный, прожектор и полусферический свет.</span><span class="sxs-lookup"><span data-stu-id="24286-154">There are four types of lights that can be used with a range of lighting properties: Point, Directional, Spot and Hemispheric Light.</span></span> <span data-ttu-id="24286-155">Давайте добавим полусферический свет [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="24286-155">Let's add the ambient light [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), as follows:</span></span>

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. <span data-ttu-id="24286-156">Окончательный код веб-страницы будет так:</span><span class="sxs-lookup"><span data-stu-id="24286-156">The final code of the web page will look as follows:</span></span>

    ```html
    <html>
    <head>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    <body>
        <canvas id="renderCanvas"></canvas>
        <script>
            const canvas = document.getElementById("renderCanvas");
            const engine = new BABYLON.Engine(canvas, true);
            
            const createScene = function() {
                const scene = new BABYLON.Scene(engine);
                scene.clearColor = new BABYLON.Color3.Black;
                
                const alpha =  Math.PI/4;
                const beta = Math.PI/3;
                const radius = 8;
                const target = new BABYLON.Vector3(0, 0, 0);
                
                const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;
                
                return scene;
            };
            
            const sceneToRender = createScene();
            engine.runRenderLoop(function(){
                sceneToRender.render();
            });
        </script>
    </body>
    </html>
    ```

1. <span data-ttu-id="24286-157">Проверьте результат в браузере.</span><span class="sxs-lookup"><span data-stu-id="24286-157">Check the output in the browser.</span></span> <span data-ttu-id="24286-158">Вы увидите куб и с помощью мыши сможете повернуть камеру вокруг него и просмотреть его грани:</span><span class="sxs-lookup"><span data-stu-id="24286-158">You should see the cube and using the mouse you can rotate the camera around the cube and see the different faces of the cube:</span></span>

![Простая сцена с кубом](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a><span data-ttu-id="24286-160">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="24286-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="24286-161">Следующее руководство: 3. Взаимодействие с трехмерным объектом</span><span class="sxs-lookup"><span data-stu-id="24286-161">Next Tutorial: 3. Interact with 3D object</span></span>](interact-03.md)
