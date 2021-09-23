---
title: Создание пианино в WebXR с помощью BabylonJS
description: Изучите эту серию учебников, чтобы узнать, как создать работающую клавиатуру пианино с 88 клавишами в WebXR с помощью BabylonJS.
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: смешанная реальность, javascript, учебник, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, иммерсивное веб-приложение
ms.localizationpriority: high
ms.openlocfilehash: 93a3896b081e736bb62bceb6c8ae609685d7c5b5
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932498"
---
# <a name="tutorial-build-a-piano-in-webxr-using-babylonjs"></a>Учебник. Создание пианино в WebXR с помощью Babylon.js

Создание пианино в реальном мире требует много времени, навыков и материалов. Но как насчет создания пианино для мира виртуальной или дополненной реальности?

В этой серии учебников описывается, как использовать Babylon.js для создания веб-приложения смешанной реальности, которое предоставляет работающее стоячее пианино с 88 клавишами в виртуальном мире. В готовом приложении вы сможете телепортироваться к пианино и играть на клавишах с помощью контроллеров смешанной реальности.

Из этой серии учебников вы узнаете, как выполнять следующие задачи:

> [!div class="checklist"]
> * создание, размещение и объединение сеток для создания клавиатуры пианино;
> * импорт модели Babylon.js для стоячего корпуса пианино;
> * добавление взаимодействий с помощью указателя к каждой клавише пианино;
> * включение поддержки телепортации и нескольких указателей в WebXR.

## <a name="prerequisites"></a>Предварительные требования

* Компьютер, подключенный к Интернету.
* Базовые знания JavaScript.
* [Учебник по Hello World на JavaScript в WebXR](../babylonjs-webxr-helloworld/introduction-01.md)
* Браузер с поддержкой WebXR, например [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 или более поздней версии
* Любая [гарнитура виртуальной реальности](../../../../discover/immersive-headset-hardware-details.md) или [симулятор Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md).
* Необязательно: [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10), если вы хотите использовать симулятор Windows Mixed Reality

## <a name="getting-started"></a>Начало работы

Начнем с настройки веб-страницы HTML, которая будет содержать сцену Babylon.js.

1. Создайте папку с именем *babylonjs-piano-tutorial* и откройте ее в Visual Studio Code.

    > [!NOTE]
    > Хотя вы можете использовать любой редактор кода для выполнения дальнейших действий, для удобства в рамках этого учебника мы будем использовать Visual Studio Code.

1. В папке создайте файл с именем *index.html* и вставьте в него приведенный ниже шаблон:

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas"); 
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
        
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

    Дополнительные сведения о содержимом этого шаблона см. в [учебнике по Hello World](../babylonjs-webxr-helloworld/introduction-01.md), знакомство с которым обязательно для работы с этим учебником.

1. Если вы попытаетесь открыть этот файл в браузере, консоль отобразит сообщение об ошибке с указанием того, что функция `createScene()` не найдена. Разрешите эту ошибку, реализовав функцию `createScene()` в следующем разделе.

## <a name="setup-the-scene"></a>Настройка сцены

1. В папке, в которой находится *index.html*, создайте другой файл с именем *scene.js*. Мы будем хранить в этом файле весь код JavaScript, связанный с настройкой сцены и созданием пианино.

1. Добавим функцию `createScene()` в *scene.js*:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        return scene;
    }
    ```

    Обратите внимание, что мы делаем `createScene()` асинхронной функцией. Далее описано, почему.

1. Затем мы добавим источник света и камеру, чтобы сцена была видимой. Обновите функцию `createScene()`:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);

        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;

        return scene;
    }
    ```

    Здесь мы создали объект [ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), который указывает почти полностью вниз и нацелен на начальную точку пространства. Созданный источник света — это объект [HemisphericLight](https://doc.babylonjs.com/divingDeeper/lights/lights_introduction#the-hemispheric-light), который указывает вверх и полезен для имитации объемного пространства. Мы также немного приглушили свет, снизив его интенсивность.

    Если вам нужно вспомнить, как создать камеру и источник света, вернитесь к [разделу "Подготовка сцены" из серии учебников по Hello World](../babylonjs-webxr-helloworld/prepare-scene-02.md#add-a-camera), прежде чем переходить к следующему шагу.

1. Наконец, так как мы разрабатываем приложение для платформы WebXR, нам потребуется [включить интерфейс смешанной реальности](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR) в сцене, вставив следующую строку перед `return scene;`:

    ```javascript
    const xrHelper = await scene.createDefaultXRExperienceAsync();
    ```

    В JavaScript для использования `await` в функции `async`, вложенной в функцию, родительская функция также должна быть асинхронной (`async`). Именно поэтому мы определили функцию `createScene` как асинхронную ранее. Далее в этой серии учебников мы будем использовать этот `xrHelper`, чтобы включить и настроить разные функции WebXR, поддерживаемые Babylon.js.

1. Полный файл *scene.js* должен выглядеть следующим образом:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        
        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. Теперь, когда у нас есть рабочая функция `createScene()`, сделаем так, чтобы *index.html* загрузил файл *scene.js* в виде скрипта. Это нужно для того, чтобы функция `createScene()` была распознана в *index.html*. Добавьте следующую строку кода в разделе `<header>` HTML-файла:

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <script src="scene.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas");
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
                
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

1. Откройте *index.html* в браузере, и вы обнаружите, что отображаемое ранее сообщение об ошибке отсутствует. На странице будет показана пустая сцена Babylon.js.

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Следующий учебник: Создание трехмерной модели пианино](keyboard-model-02.md)
