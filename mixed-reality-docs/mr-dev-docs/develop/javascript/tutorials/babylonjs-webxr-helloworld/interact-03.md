---
title: Руководство по взаимодействию с трехмерными объектами с использованием babylon.js
description: Узнайте, как использовать babylon.js и взаимодействовать с трехмерными объектами.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: смешанная реальность, javascript, учебник, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, иммерсивное веб-приложение
ms.localizationpriority: high
ms.openlocfilehash: 5d156f50125473ce2055bc0095842f89a3ce9853
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130153389"
---
# <a name="tutorial-interact-with-3d-object"></a>Руководство. Взаимодействие с трехмерным объектом

Узнайте, как создавать трехмерные объекты и взаимодействия для работы в смешанной реальности с помощью babylon.js. В этом разделе вы начнете с простого примера: нарисуете грани куба при выборе объекта.

В этом руководстве рассматриваются следующие темы:

> [!div class="checklist"]
> * добавление взаимодействий;
> * включение режима погружения WebXR;
> * запуск приложения в симуляторе Windows Mixed Reality;
> * запуск и отладка приложения в Chrome на Android.

## <a name="before-you-begin"></a>Подготовка к работе

На предыдущем шаге руководства была создана базовая веб-страница со сценой. Откройте веб-страницу для редактирования.

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

## <a name="add-interaction"></a>Добавление взаимодействия

1. Сначала обновим наш код, создающий куб, чтобы куб был окрашен в случайный цвет. Для этого мы добавим [материал](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) для куба. В материале можно указать цвет и текстуры, а также использовать их для покрытия других объектов. Способ отображения материала зависит от света или источников света, используемых в сцене, и от того, как он реагирует. Например, diffuseColor распределяет цвет по сетке, к которой он присоединен. Добавьте следующий код:

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. Теперь, когда куб окрашен в случайный цвет, давайте добавим взаимодействие:

    * для изменения цвета при щелчке по кубу;
    * для перемещения куба после изменения цвета.

    Чтобы добавить взаимодействия, мы будем использовать [действия](https://doc.babylonjs.com/divingDeeper/events/actions). Действие запускается в ответ на срабатывание триггера события. Например, когда пользователь щелкает куб. Все, что нам нужно сделать, — это создать экземпляр BABYLON.ActionManager и зарегистрировать действие для определенного триггера. [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) будет выполнять нашу функцию JavaScript, когда кто-то щелкнет куб:

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

1. Окончательный код веб-страницы будет выглядеть так:

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

## <a name="enable-webxr-immersive-experience"></a>Включение иммерсивного интерфейса WebXR

Теперь, когда наш куб изменяет цвета, мы готовы попробовать иммерсивное взаимодействие.

1. На этом этапе мы введем [основание](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground). Куб будет находиться в воздухе, и в нижней части будет отображаться пол. Добавьте основание следующим образом:

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    Это создает простой пол размером 4 x 4.

1. Чтобы добавить поддержку WebXR, необходимо вызвать *createDefaultXRExperienceAsync* с результатом *Promise* (обещание). Добавьте этот код в конец функции *createScene* вместо *return scene*:

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. Так как функция *createScene* теперь возвращает обещание вместо сцены, необходимо изменить способ вызова *createScene* и *engine.runRenderLoop*. Замените текущие вызовы этих функций, расположенные непосредственно перед тегом *\</script>* , с помощью следующего кода:

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. Окончательный код веб-страницы будет выглядеть так:

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

1. Приведенный выше код создает следующие выходные данные в окне браузера: ![сцена WebXR](../images/hello-world-webxr-scene.png)

## <a name="run-on-a-windows-mixed-reality-simulator"></a>Запуск в симуляторе Windows Mixed Reality

1. [Включите симулятор Windows Mixed Reality](../../../advanced-concepts/using-the-windows-mixed-reality-simulator.md), если вы еще не сделали это в прошлом.

1. Нажмите кнопку режима иммерсивной виртуальной реальности в правом нижнем углу: ![Immersive VR Button](../images/immersive-vr-button.png).

1. Это действие запустит окно симулятора Windows Mixed Reality, как показано ниже: ![Портал смешанной реальности](../images/mixed-reality-portal.png)

1. Используйте клавиши W, A, S и D на клавиатуре для перемещения вперед, назад, влево и вправо. Используйте смоделированную руку для создания целевого куба и нажмите клавишу ВВОД на клавиатуре, чтобы выполнить действие щелчка. Куб изменит свой цвет и перейдет в новое положение.

> [!NOTE]
> При нацеливании на куб убедитесь, что конец телекинеза (белый круг) пересекается с кубом, как показано на рисунке выше. Узнайте больше о [наведении и фиксации с помощью руки](../../../../design/point-and-commit.md).

## <a name="run-and-debug-on-android-device"></a>Запуск и отладка на устройстве с Android

Чтобы включить отладку на устройстве с Android, выполните следующие действия.

### <a name="prerequisites"></a>Предварительные требования

* Веб-сервер, который обслуживает статическую страницу HTML в безопасном контексте (https:// или через перенаправление портов на localhost) на компьютере разработки. Например, вы можете использовать пакет NPM *serve* в качестве простого упрощенного веб-сервера, который обслуживает статические HTML-файлы. Дополнительные сведения о пакете [NPM serve](https://github.com/vercel/serve#readme).
* Устройство с Google Play Маркетом (установленным изначально) и под управлением Android 7.0 или более поздней версии.
* Последняя версия [Google Chrome](https://support.google.com/chrome/answer/95346) на рабочей станции разработки и на устройстве.
* Чтобы убедиться, что устройство правильно настроено для запуска WebXR, перейдите на [страницу примера WebXR](https://immersive-web.github.io/webxr-samples/) на устройстве. Должно отобразиться сообщение:

    > Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware. (Ваш браузер поддерживает WebXR и может запускать виртуальную реальность и расширенные возможности, если у вас есть соответствующее оборудование.)

1. Включите режим разработчика и отладку по USB на устройстве с Android. Узнайте, как это сделать для вашей версии Android, на официальной странице документации: [Настройка параметров разработчика на устройстве](https://developer.android.com/studio/debug/dev-options).
1. Затем подключите устройство с Android к компьютеру разработки или ноутбуку через USB-кабель.
1. Убедитесь, что веб-сервер на компьютере разработки запущен. Например, перейдите к корневой папке, содержащей основную веб-страницу (index.html), и выполните следующий код (при условии, что используется пакет NPM serve):

    ```bash
    serve
    ```

1. Откройте Google Chrome на компьютере разработки и введите в адресной строке следующий текст:
    > chrome://inspect#devices ![Окно отладки USB в Chrome](../images/chrome-usb-debug.png)
1. Убедитесь, что установлен флажок *Discover USB devices* (Обнаружение USB-устройств).
1. Нажмите кнопку *Port forwarding* (Перенаправление портов) и убедитесь, что *Port forwarding* (Перенаправление портов) включено и содержит запись *localhost:500*, как показано ниже: ![Окно перенаправления портов в Chrome.](../images/chrome-port-forwarding.png)
1. На подключенном устройстве с Android откройте окно Google Chrome и перейдите на *http://localhost:5000* , где вы должны увидеть куб.
1. На компьютере разработки в Chrome вы увидите ваше устройство и список веб-страниц, которые в настоящий момент открыты здесь: ![Окно проверки в Chrome](../images/chrome-inspect.png)
1. Нажмите кнопку *Inspect* (Проверить) рядом с записью *http://localhost:5000* : ![ Окно отладки Chrome DevTools](../images/chrome-debug.png)
1. Использование [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) для отладки страницы

## <a name="takeaways"></a>Общие выводы

Далее следуют самые важные выводы из этого руководства.
* Babylon.js упрощает создание впечатляющих интерфейсов с помощью JavaScript.
* Для создания виртуальных сцен вам не нужно писать низкоуровневый код или изучать новую технологию.
* Вы можете создавать приложения смешанной реальности с помощью браузера, поддерживающего WebXR, без необходимости покупать гарнитуру.

## <a name="next-steps"></a>Дальнейшие действия

Поздравляем! Вы завершили серию руководств по babylon.js и изучили следующее:
> [!div class="checklist"]
> * Настройка среды разработки
> * Создание веб-страницы для отображения результатов
> * API babylon.js для создания основных трехмерных элементов и взаимодействия с ними
> * Запуск и тестирование приложения в симуляторе Windows Mixed Reality

Дополнительные сведения о разработке JavaScript в смешанной реальности см. в статье [Общие сведения о разработке JavaScript](/javascript-development-overview.md).

Если вам нужен другой учебник по babylon.js, см. [серию учебников по созданию пианино](../babylonjs-webxr-piano/introduction-01.md), в которой описывается, как создать пианино в пространстве виртуальной реальности с помощью babylon.js.
