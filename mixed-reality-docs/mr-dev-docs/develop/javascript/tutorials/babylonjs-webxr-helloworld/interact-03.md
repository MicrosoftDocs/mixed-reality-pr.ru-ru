---
title: Руководство по взаимодействию с трехмерными объектами с использованием babylon.js
description: Узнайте, как использовать babylon.js и взаимодействовать с трехмерными объектами.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: смешанная реальность, javascript, учебник, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, иммерсивное веб-приложение
ms.localizationpriority: high
ms.openlocfilehash: a3dbab0572cd50105dac3d877a0d72c5cbc504b6
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584523"
---
# <a name="tutorial-interact-with-3d-object"></a><span data-ttu-id="be51b-104">Руководство. Взаимодействие с трехмерным объектом</span><span class="sxs-lookup"><span data-stu-id="be51b-104">Tutorial: Interact with 3D object</span></span>

<span data-ttu-id="be51b-105">Узнайте, как создавать трехмерные объекты и взаимодействия для работы в смешанной реальности с помощью babylon.js.</span><span class="sxs-lookup"><span data-stu-id="be51b-105">Learn how to create 3D objects and interactions for a Mixed Reality experience using babylon.js.</span></span> <span data-ttu-id="be51b-106">В этом разделе вы начнете с простого примера: нарисуете грани куба при выборе объекта.</span><span class="sxs-lookup"><span data-stu-id="be51b-106">In this section, you'll start with something simple, like painting the faces of a cube when you select the object.</span></span>

<span data-ttu-id="be51b-107">В этом руководстве рассматриваются следующие темы:</span><span class="sxs-lookup"><span data-stu-id="be51b-107">This tutorial covers the following topics:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="be51b-108">добавление взаимодействий;</span><span class="sxs-lookup"><span data-stu-id="be51b-108">How to add interactions</span></span>
> * <span data-ttu-id="be51b-109">включение режима погружения WebXR;</span><span class="sxs-lookup"><span data-stu-id="be51b-109">Enable WebXR immersive mode</span></span>
> * <span data-ttu-id="be51b-110">запуск приложения в симуляторе Windows Mixed Reality;</span><span class="sxs-lookup"><span data-stu-id="be51b-110">Run the app on Windows Mixed Reality Simulator</span></span>
> * <span data-ttu-id="be51b-111">запуск и отладка приложения в Chrome на Android.</span><span class="sxs-lookup"><span data-stu-id="be51b-111">Run and debug the app on Android Chrome</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="be51b-112">Подготовка к работе</span><span class="sxs-lookup"><span data-stu-id="be51b-112">Before you begin</span></span>

<span data-ttu-id="be51b-113">На предыдущем шаге руководства была создана базовая веб-страница со сценой.</span><span class="sxs-lookup"><span data-stu-id="be51b-113">In previous tutorial step a basic web page with a scene was created.</span></span> <span data-ttu-id="be51b-114">Откройте веб-страницу для редактирования.</span><span class="sxs-lookup"><span data-stu-id="be51b-114">Have the hosting web page open for editing.</span></span>

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

## <a name="add-interaction"></a><span data-ttu-id="be51b-115">Добавление взаимодействия</span><span class="sxs-lookup"><span data-stu-id="be51b-115">Add interaction</span></span>

1. <span data-ttu-id="be51b-116">Сначала обновим наш код, создающий куб, чтобы куб был окрашен в случайный цвет.</span><span class="sxs-lookup"><span data-stu-id="be51b-116">First, let's update our code that creates the cube, so that the cube is painted with a random color.</span></span> <span data-ttu-id="be51b-117">Для этого мы добавим [материал](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) для куба.</span><span class="sxs-lookup"><span data-stu-id="be51b-117">To do that, we will add [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) to our cube.</span></span> <span data-ttu-id="be51b-118">В материале можно указать цвет и текстуры, а также использовать их для покрытия других объектов.</span><span class="sxs-lookup"><span data-stu-id="be51b-118">Material allows us to specify color and textures and can be used to cover other objects.</span></span> <span data-ttu-id="be51b-119">Способ отображения материала зависит от света или источников света, используемых в сцене, и от того, как он реагирует.</span><span class="sxs-lookup"><span data-stu-id="be51b-119">How a material appears depends on the light or lights used in the scene and how it is set to react.</span></span> <span data-ttu-id="be51b-120">Например, diffuseColor распределяет цвет по сетке, к которой он присоединен.</span><span class="sxs-lookup"><span data-stu-id="be51b-120">For example, the diffuseColor spreads the color all over the mesh to which it is attached.</span></span> <span data-ttu-id="be51b-121">Добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="be51b-121">Add the following code:</span></span>

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. <span data-ttu-id="be51b-122">Теперь, когда куб окрашен в случайный цвет, давайте добавим взаимодействие:</span><span class="sxs-lookup"><span data-stu-id="be51b-122">Now that the cube is painted with a random color, let's add an interaction to:</span></span>

    * <span data-ttu-id="be51b-123">для изменения цвета при щелчке по кубу;</span><span class="sxs-lookup"><span data-stu-id="be51b-123">Change the color when the cube is clicked</span></span>
    * <span data-ttu-id="be51b-124">для перемещения куба после изменения цвета.</span><span class="sxs-lookup"><span data-stu-id="be51b-124">Move the cube after the color is changed</span></span>

    <span data-ttu-id="be51b-125">Чтобы добавить взаимодействия, мы будем использовать [действия](https://doc.babylonjs.com/divingDeeper/events/actions).</span><span class="sxs-lookup"><span data-stu-id="be51b-125">To add interactions we should be using [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span></span> <span data-ttu-id="be51b-126">Действие запускается в ответ на срабатывание триггера события.</span><span class="sxs-lookup"><span data-stu-id="be51b-126">An action is launched in response to the event trigger.</span></span> <span data-ttu-id="be51b-127">Например, когда пользователь щелкает куб.</span><span class="sxs-lookup"><span data-stu-id="be51b-127">For example, when the user clicks on the cube.</span></span> <span data-ttu-id="be51b-128">Все, что нам нужно сделать, — это создать экземпляр BABYLON.ActionManager и зарегистрировать действие для определенного триггера.</span><span class="sxs-lookup"><span data-stu-id="be51b-128">All we need to do is instantiate BABYLON.ActionManager and register an action for certain trigger.</span></span> <span data-ttu-id="be51b-129">[BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) будет выполнять нашу функцию JavaScript, когда кто-то щелкнет куб:</span><span class="sxs-lookup"><span data-stu-id="be51b-129">The [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) will run our JavaScript function when someone clicks on the cube:</span></span>

    ```javascript
    box.actionManager = new BABYLON.ActionManager(scene);
    box.actionManager.registerAction(new BABYLON.ExecuteCodeAction(
        BABYLON.ActionManager.OnPickTrigger, 
        function (evt) {
            const sourceBox = evt.meshUnderPointer;
            
            //move the box upright
            sourceBox.position.x += 0.1;
            sourceBox.position.y += 0.1;

            //update the color
            boxMaterial.diffuseColor = BABYLON.Color3.Random();
        }));
    ```

1. <span data-ttu-id="be51b-130">Окончательный код веб-страницы будет выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="be51b-130">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));

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

## <a name="enable-webxr-immersive-experience"></a><span data-ttu-id="be51b-131">Включение иммерсивного интерфейса WebXR</span><span class="sxs-lookup"><span data-stu-id="be51b-131">Enable WebXR immersive experience</span></span>

<span data-ttu-id="be51b-132">Теперь, когда наш куб изменяет цвета, мы готовы попробовать иммерсивное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="be51b-132">Now that our cube is changing colors, we're ready to try the immersive experience.</span></span>

1. <span data-ttu-id="be51b-133">На этом этапе мы введем [основание](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span><span class="sxs-lookup"><span data-stu-id="be51b-133">In this step we're going to introduce a [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span></span> <span data-ttu-id="be51b-134">Куб будет находиться в воздухе, и в нижней части будет отображаться пол.</span><span class="sxs-lookup"><span data-stu-id="be51b-134">The cube will be hanging in the air and we will see a floor at the bottom.</span></span> <span data-ttu-id="be51b-135">Добавьте основание следующим образом:</span><span class="sxs-lookup"><span data-stu-id="be51b-135">Add the ground as follows:</span></span>

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    <span data-ttu-id="be51b-136">Это создает простой пол размером 4 x 4.</span><span class="sxs-lookup"><span data-stu-id="be51b-136">This creates a simple 4x4-meter floor.</span></span>

1. <span data-ttu-id="be51b-137">Чтобы добавить поддержку WebXR, необходимо вызвать *createDefaultXRExperienceAsync* с результатом *Promise* (обещание).</span><span class="sxs-lookup"><span data-stu-id="be51b-137">In order to add WebXR support, we need to call *createDefaultXRExperienceAsync*, which has a *Promise* result.</span></span> <span data-ttu-id="be51b-138">Добавьте этот код в конец функции *createScene* вместо *return scene*:</span><span class="sxs-lookup"><span data-stu-id="be51b-138">Add this code at the end of *createScene* function instead of *return scene;*:</span></span>

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. <span data-ttu-id="be51b-139">Так как функция *createScene* теперь возвращает обещание вместо сцены, необходимо изменить способ вызова *createScene* и *engine.runRenderLoop*.</span><span class="sxs-lookup"><span data-stu-id="be51b-139">Since the *createScene* function is now returning a promise instead of a scene, we need to modify how *createScene* and *engine.runRenderLoop* are called.</span></span> <span data-ttu-id="be51b-140">Замените текущие вызовы этих функций, расположенные непосредственно перед тегом *\</script>* , с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="be51b-140">Replace the current calls of these functions, which are located right before the *\</script>* tag, with the code below:</span></span>

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. <span data-ttu-id="be51b-141">Окончательный код веб-страницы будет выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="be51b-141">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));
                    
                const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
                
                const xrPromise = scene.createDefaultXRExperienceAsync({
                    floorMeshes: [ground]
                });
                
                return xrPromise.then((xrExperience) => {
                    console.log("Done, WebXR is enabled.");
                    return scene;
                });
            };
            
            createScene().then(sceneToRender => {
                engine.runRenderLoop(() => sceneToRender.render());
            });
        </script>
    </body>
    </html>
    ```

1. <span data-ttu-id="be51b-142">Приведенный выше код создает следующие выходные данные в окне браузера: ![сцена WebXR](../images/hello-world-webxr-scene.png)</span><span class="sxs-lookup"><span data-stu-id="be51b-142">The above code generates the following output in the browser window: ![WebXR scene](../images/hello-world-webxr-scene.png)</span></span>

## <a name="run-on-a-windows-mixed-reality-simulator"></a><span data-ttu-id="be51b-143">Запуск в симуляторе Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="be51b-143">Run on a Windows Mixed Reality Simulator</span></span>

1. <span data-ttu-id="be51b-144">[Включите симулятор Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md), если вы еще не сделали это в прошлом.</span><span class="sxs-lookup"><span data-stu-id="be51b-144">[Enable the Windows Mixed Reality Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) if you have not done so in the past.</span></span>

1. <span data-ttu-id="be51b-145">Нажмите кнопку режима иммерсивной виртуальной реальности в правом нижнем углу: ![Immersive VR Button](../images/immersive-vr-button.png).</span><span class="sxs-lookup"><span data-stu-id="be51b-145">Select the Immersive-VR button on the bottom right corner: ![Immersive VR Button](../images/immersive-vr-button.png)</span></span>

1. <span data-ttu-id="be51b-146">Это действие запустит окно симулятора Windows Mixed Reality, как показано ниже: ![Портал смешанной реальности](../images/mixed-reality-portal.png)</span><span class="sxs-lookup"><span data-stu-id="be51b-146">This action will launch the Windows Mixed Reality Simulator window as shown below: ![Mixed Reality Portal](../images/mixed-reality-portal.png)</span></span>

1. <span data-ttu-id="be51b-147">Используйте клавиши W, A, S и D на клавиатуре для перемещения вперед, назад, влево и вправо.</span><span class="sxs-lookup"><span data-stu-id="be51b-147">Use the W,A,S, and D keys on your keyboard to walk forward, back left and right accordingly.</span></span> <span data-ttu-id="be51b-148">Используйте смоделированную руку для создания целевого куба и нажмите клавишу ВВОД на клавиатуре, чтобы выполнить действие щелчка.</span><span class="sxs-lookup"><span data-stu-id="be51b-148">Use simulated hand to target the cube and press the Enter key on your keyboard to perform the click action.</span></span> <span data-ttu-id="be51b-149">Куб изменит свой цвет и перейдет в новое положение.</span><span class="sxs-lookup"><span data-stu-id="be51b-149">The cube will change its color and move to a new position.</span></span>

> [!NOTE]
> <span data-ttu-id="be51b-150">При нацеливании на куб убедитесь, что конец телекинеза (белый круг) пересекается с кубом, как показано на рисунке выше.</span><span class="sxs-lookup"><span data-stu-id="be51b-150">When targeting the cube, make sure that the end of hand ray (white circle) intersects with the cube as shown on the picture above.</span></span> <span data-ttu-id="be51b-151">Узнайте больше о [наведении и фиксации с помощью руки](../../../../design/point-and-commit.md).</span><span class="sxs-lookup"><span data-stu-id="be51b-151">Learn more about [Point and commit with hands](../../../../design/point-and-commit.md).</span></span>

## <a name="run-and-debug-on-android-device"></a><span data-ttu-id="be51b-152">Запуск и отладка на устройстве с Android</span><span class="sxs-lookup"><span data-stu-id="be51b-152">Run and debug on Android device</span></span>

<span data-ttu-id="be51b-153">Чтобы включить отладку на устройстве с Android, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="be51b-153">Perform the following steps to enable debugging on your Android device:</span></span>

### <a name="prerequisites"></a><span data-ttu-id="be51b-154">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="be51b-154">Prerequisites</span></span>

* <span data-ttu-id="be51b-155">Веб-сервер, который обслуживает статическую страницу HTML в безопасном контексте (https:// или через перенаправление портов на localhost) на компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="be51b-155">A web server that serves static html page in secure context (https:// or via Port forwarding on localhost) on development machine.</span></span> <span data-ttu-id="be51b-156">Например, вы можете использовать пакет NPM *serve* в качестве простого упрощенного веб-сервера, который обслуживает статические HTML-файлы. Дополнительные сведения о пакете [NPM serve](https://github.com/vercel/serve#readme).</span><span class="sxs-lookup"><span data-stu-id="be51b-156">For example leverage *serve* npm package as simple lightweight web server that serves static html files, check more [npm serve](https://github.com/vercel/serve#readme)</span></span>
* <span data-ttu-id="be51b-157">Устройство с Google Play Маркетом (установленным изначально) и под управлением Android 7.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="be51b-157">The device originally shipped with the Google Play Store and must be running Android 7.0 or newer</span></span>
* <span data-ttu-id="be51b-158">Последняя версия [Google Chrome](https://support.google.com/chrome/answer/95346) на рабочей станции разработки и на устройстве.</span><span class="sxs-lookup"><span data-stu-id="be51b-158">The latest version of [Google Chrome](https://support.google.com/chrome/answer/95346) on both the development workstation and on the device</span></span>
* <span data-ttu-id="be51b-159">Чтобы убедиться, что устройство правильно настроено для запуска WebXR, перейдите на [страницу примера WebXR](https://immersive-web.github.io/webxr-samples/) на устройстве.</span><span class="sxs-lookup"><span data-stu-id="be51b-159">To verify that the device is correctly configured to run WebXR, browse to a [sample WebXR page](https://immersive-web.github.io/webxr-samples/) on the device.</span></span> <span data-ttu-id="be51b-160">Должно отобразиться сообщение:</span><span class="sxs-lookup"><span data-stu-id="be51b-160">You should see the message, such as:</span></span>

    > <span data-ttu-id="be51b-161">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware. (Ваш браузер поддерживает WebXR и может запускать виртуальную реальность и расширенные возможности, если у вас есть соответствующее оборудование.)</span><span class="sxs-lookup"><span data-stu-id="be51b-161">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware.</span></span>

1. <span data-ttu-id="be51b-162">Включите режим разработчика и отладку по USB на устройстве с Android.</span><span class="sxs-lookup"><span data-stu-id="be51b-162">Enable developer mode and USB debugging on an Android device.</span></span> <span data-ttu-id="be51b-163">Узнайте, как это сделать для вашей версии Android, на официальной странице документации: [Настройка параметров разработчика на устройстве](https://developer.android.com/studio/debug/dev-options).</span><span class="sxs-lookup"><span data-stu-id="be51b-163">See how to do this for your version of Android at the official documentation page [Configure on-device developer options](https://developer.android.com/studio/debug/dev-options)</span></span>
1. <span data-ttu-id="be51b-164">Затем подключите устройство с Android к компьютеру разработки или ноутбуку через USB-кабель.</span><span class="sxs-lookup"><span data-stu-id="be51b-164">Next, connect Android device to your development machine or laptop via USB cable</span></span>
1. <span data-ttu-id="be51b-165">Убедитесь, что веб-сервер на компьютере разработки запущен.</span><span class="sxs-lookup"><span data-stu-id="be51b-165">Ensure that the web server on the development machine is running.</span></span> <span data-ttu-id="be51b-166">Например, перейдите к корневой папке, содержащей основную веб-страницу (index.html), и выполните следующий код (при условии, что используется пакет NPM serve):</span><span class="sxs-lookup"><span data-stu-id="be51b-166">For example, navigate to the root folder containing your web hosting page (index.html) and execute the following code (assuming you use serve npm package):</span></span>

    ```bash
    serve
    ```

1. <span data-ttu-id="be51b-167">Откройте Google Chrome на компьютере разработки и введите в адресной строке следующий текст:</span><span class="sxs-lookup"><span data-stu-id="be51b-167">Open Google Chrome on your development machine and enter in the address bar the following text:</span></span>
    > <span data-ttu-id="be51b-168">chrome://inspect#devices ![Окно отладки USB в Chrome](../images/chrome-usb-debug.png)</span><span class="sxs-lookup"><span data-stu-id="be51b-168">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span></span>
1. <span data-ttu-id="be51b-169">Убедитесь, что установлен флажок *Discover USB devices* (Обнаружение USB-устройств).</span><span class="sxs-lookup"><span data-stu-id="be51b-169">Ensure that the *Discover USB devices* checkbox is enabled</span></span>
1. <span data-ttu-id="be51b-170">Нажмите кнопку *Port forwarding* (Перенаправление портов) и убедитесь, что *Port forwarding* (Перенаправление портов) включено и содержит запись *localhost:500*, как показано ниже: ![Окно перенаправления портов в Chrome.](../images/chrome-port-forwarding.png)</span><span class="sxs-lookup"><span data-stu-id="be51b-170">Click the button *Port forwarding* and ensure that *Port forwarding* is enabled and contains an entry *localhost:5000* as shown below:  ![Chrome Port Forwarding window](../images/chrome-port-forwarding.png)</span></span>
1. <span data-ttu-id="be51b-171">На подключенном устройстве с Android откройте окно Google Chrome и перейдите на *http://localhost:5000* , где вы должны увидеть куб.</span><span class="sxs-lookup"><span data-stu-id="be51b-171">In your connected Android device open a Google Chrome window and browse to *http://localhost:5000* and you should see the cube</span></span>
1. <span data-ttu-id="be51b-172">На компьютере разработки в Chrome вы увидите ваше устройство и список веб-страниц, которые в настоящий момент открыты здесь: ![Окно проверки в Chrome](../images/chrome-inspect.png)</span><span class="sxs-lookup"><span data-stu-id="be51b-172">On your development machine, in Chrome, you will see your device and a list of web pages currently opened in there:  ![Chrome Inspect window](../images/chrome-inspect.png)</span></span>
1. <span data-ttu-id="be51b-173">Нажмите кнопку *Inspect* (Проверить) рядом с записью *http://localhost:5000* : ![ Окно отладки Chrome DevTools](../images/chrome-debug.png)</span><span class="sxs-lookup"><span data-stu-id="be51b-173">Click the button *Inspect* next to an entry *http://localhost:5000*:  ![Chrome DevTools Debug window](../images/chrome-debug.png)</span></span>
1. <span data-ttu-id="be51b-174">Использование [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) для отладки страницы</span><span class="sxs-lookup"><span data-stu-id="be51b-174">Use the [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) to debug the page</span></span>

## <a name="takeaways"></a><span data-ttu-id="be51b-175">Общие выводы</span><span class="sxs-lookup"><span data-stu-id="be51b-175">Takeaways</span></span>

<span data-ttu-id="be51b-176">Далее следуют самые важные выводы из этого руководства.</span><span class="sxs-lookup"><span data-stu-id="be51b-176">The following are the most important takeaways from this tutorial:</span></span>
* <span data-ttu-id="be51b-177">Babylon.js упрощает создание впечатляющих интерфейсов с помощью JavaScript.</span><span class="sxs-lookup"><span data-stu-id="be51b-177">Babylon.js makes it easy to create immersive experiences using JavaScript</span></span>
* <span data-ttu-id="be51b-178">Для создания виртуальных сцен вам не нужно писать низкоуровневый код или изучать новую технологию.</span><span class="sxs-lookup"><span data-stu-id="be51b-178">To create virtual scenes you don't need to write low-level code or learn a new technology</span></span>
* <span data-ttu-id="be51b-179">Вы можете создавать приложения смешанной реальности с помощью браузера, поддерживающего WebXR, без необходимости покупать гарнитуру.</span><span class="sxs-lookup"><span data-stu-id="be51b-179">You can build Mixed Reality applications with WebXR-supported browser without need to buy a headset</span></span>

## <a name="next-steps"></a><span data-ttu-id="be51b-180">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="be51b-180">Next steps</span></span>

<span data-ttu-id="be51b-181">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="be51b-181">Congratulations!</span></span> <span data-ttu-id="be51b-182">Вы завершили серию руководств по babylon.js и изучили следующее:</span><span class="sxs-lookup"><span data-stu-id="be51b-182">You've completed our series of babylon.js tutorials and learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="be51b-183">Настройка среды разработки</span><span class="sxs-lookup"><span data-stu-id="be51b-183">Set up a development environment</span></span>
> * <span data-ttu-id="be51b-184">Создание веб-страницы для отображения результатов</span><span class="sxs-lookup"><span data-stu-id="be51b-184">Create a new web page to display results</span></span>
> * <span data-ttu-id="be51b-185">API babylon.js для создания основных трехмерных элементов и взаимодействия с ними</span><span class="sxs-lookup"><span data-stu-id="be51b-185">The babylon.js API to create and interact with basic 3D elements</span></span>
> * <span data-ttu-id="be51b-186">Запуск и тестирование приложения в симуляторе Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="be51b-186">Run and test the application in a Windows Mixed Reality Simulator</span></span>

<span data-ttu-id="be51b-187">Дополнительные сведения о разработке JavaScript в смешанной реальности см. в статье [Общие сведения о разработке JavaScript](/javascript-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="be51b-187">For more information on Mixed Reality JavaScript development see [JavaScript development overview](/javascript-development-overview.md).</span></span>
