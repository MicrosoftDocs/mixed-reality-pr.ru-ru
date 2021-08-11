---
title: Руководство по babylon.js для подготовки сцены с базовыми трехмерными объектами
description: Узнайте, как использовать babylon.js и добавлять базовые трехмерные объекты в сцену.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: смешанная реальность, javascript, учебник, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, иммерсивное веб-приложение
ms.localizationpriority: high
ms.openlocfilehash: 9d74104924aa859f5ab18248a487a7e80392809adb09361e84c5ad386f1321c4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212395"
---
# <a name="tutorial-prepare-a-scene"></a>Руководство. Подготовка сцены

Узнайте, как подготовить сцену и добавить в нее некоторые основные трехмерные элементы.

Из этого руководства вы узнаете, как выполнять следующие задачи:

> [!div class="checklist"]
> * Создание сцены
> * Добавление камеры
> * Добавление света
> * Добавление базовых трехмерных элементов

## <a name="before-you-begin"></a>Подготовка к работе

На предыдущем шаге руководства была создана базовая веб-страница. Откройте веб-страницу для редактирования.

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

## <a name="create-a-scene"></a>Создание сцены

Сцена — это место, где будет отображаться содержимое. Может существовать несколько сцен, а также возможно переключение между ними. Подробнее о [сцене babylon.js](https://doc.babylonjs.com/divingDeeper/scene).

1. Добавьте тег скрипта после элемента HTML Canvas и добавьте следующий код, чтобы создать сцену, заполненную черным цветом:

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

    В приведенном выше коде необходимо создать экземпляр babylon.js движка веб-отрисовки, который визуализирует сцену и привязывает события к холсту. Дополнительные сведения о движке см. на странице документации [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)

1. По умолчанию сцена не отрисовывается. Помните, что существует несколько сцен, и вы можете управлять тем, какая из них отображается. Для повторной отрисовки сцены в каждом кадре выполните следующий код после вызова функции *createScene*:

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a>Добавление базовых трехмерных элементов

1. Давайте добавим нашу первую трехмерную фигуру. В трехмерном виртуальном мире фигуры строятся на основе *сеток* — множестве треугольных поверхностей, соединенных друг с другом, каждая из которых состоит из трех вершин. Можно использовать предопределенную сетку или создать собственную. Здесь мы будем использовать стандартную сетку Box, т. е. куб. Чтобы создать куб, используйте [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box). Сетка включает имя и параметры (они зависят от типа сетки). Добавьте следующий код в функцию *createScene*:

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. Откройте веб-страницу в браузере Microsoft Edge и проверьте выходные данные. В окне браузера отображается пустая страница. Откройте DevTools с помощью клавиатуры и выберите F12 или CTRL+SHIFT+I (Windows, Linux) или Command+Option+I (macOS). Открыв вкладку *Консоль*, можете начать поиск ошибок. Появится сообщение об ошибке: "Uncaught Error: No camera defined" (Необработанная ошибка: камера не найдена). Теперь необходимо добавить камеру в сцену.

## <a name="add-a-camera"></a>Добавление камеры

1. Чтобы просматривать виртуальный мир и взаимодействовать с ним, необходимо подключить к холсту камеру. Добавим камеру типа [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), которую можно поворачивать вокруг целевого объекта. Ниже приведены параметры, необходимые для создания экземпляра камеры.
    1. **name**: имя камеры;
    1. **alpha**: угловое положение вдоль продольной оси (в радианах);
    1. **beta**: угловое положение вдоль широтной оси (в радианах);
    1. **radius**: расстояние от целевого объекта;
    1. **target**: точка, к которой будет всегда направлена камера (определяется координатами X, Y и Z);
    1. **scene**: сцена, в которой находится камера.

    Alpha, beta, radius и target определяют расположение камеры в пространстве, как показано на схеме ниже.

    ![Камера, альфа, бета, радиус](../images/camera-alpha-beta-radius.jpg)

    Добавьте следующий код в функцию *createScene*:

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. Если вы проверите результат в браузере, то увидите черный холст. Отсутствует источник света.

## <a name="add-light"></a>Добавление света

1. Существует четыре типа источников света, которые могут использоваться с различными свойствами освещения: точечный, направленный, прожектор и полусферический свет. Давайте добавим полусферический свет [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight) следующим образом:

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. Окончательный код веб-страницы будет так:

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

1. Проверьте результат в браузере. Вы увидите куб и с помощью мыши сможете повернуть камеру вокруг него и просмотреть его грани:

![Простая сцена с кубом](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Следующее руководство: 3. Взаимодействие с трехмерным объектом](interact-03.md)
