---
title: Имитация игры на трехмерном пианино
description: Сведения о том, как добавить взаимодействия к виртуальному пианино с помощью Babylon.js.
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: смешанная реальность, javascript, учебник, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, иммерсивное веб-приложение
ms.localizationpriority: high
ms.openlocfilehash: 3476a7abdef062f62b4fa92c268bd2d50bcafc2a
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130154105"
---
# <a name="tutorial-play-the-3d-piano"></a>Учебник. Игра на трехмерном пианино

В предыдущем учебнике мы создали модель полной клавиатуры пианино с 88 клавишами. Теперь сделаем так, чтобы на нем можно было играть в пространстве смешанной реальности.

В этом учебнике рассматривается следующее.

> [!div class="checklist"]
> * Добавление интерактивных функций пианино с помощью событий указателя.
> * Изменение размера сеток.
> * Включение поддержки телепортации и нескольких указателей в смешанной реальности.

## <a name="before-you-begin"></a>Перед началом

Обязательно изучите [предыдущий учебник в серии](keyboard-model-02.md), чтобы продолжить написание кода.

*index.html*

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

*scene.js*

```javascript
const buildKey = function (scene, parent, props) {
    if (props.type === "white") {
        /*
        Props for building a white key should contain: 
        note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX

        As an example, the props for building the middle C white key would be
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
        */

        // Create bottom part
        const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);

        // Create top part
        const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
        top.position.z =  4.75;
        top.position.x += props.topPositionX;

        // Merge bottom and top parts
        // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
        const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.name = props.note + props.register;
        key.parent = parent;

        return key;
    }
    else if (props.type === "black") {
        /*
        Props for building a black key should contain: 
        note, wholePositionX, register, referencePositionX

        As an example, the props for building the C#4 black key would be
        {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
        */

        // Create black color material
        const blackMat = new BABYLON.StandardMaterial("black");
        blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

        // Create black key
        const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
        key.position.z += 4.75;
        key.position.y += 0.25;
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.material = blackMat;
        key.parent = parent;

        return key;
    }
}

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

    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }

    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});

    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });

    // Lift the piano keyboard
    keyboard.position.y += 80;

    const xrHelper = await scene.createDefaultXRExperienceAsync();

    return scene;
}
```

## <a name="making-the-piano-keyboard-playable"></a>Реализация возможности игры на пианино

Сейчас созданная нами клавиатура пианино является статической моделью, которая не реагирует на взаимодействия пользователя. В этом разделе мы запрограммируем клавиши на смещение вниз и проигрывание звука при нажатии.

1. Babylon.js предоставляет различные типы событий, или [наблюдаемые объекты](https://doc.babylonjs.com/divingDeeper/events/observables), с которыми можно взаимодействовать. В нашем случае мы будем работать с `onPointerObservable`, так как мы хотим запрограммировать клавиши на выполнение действий при нажатии на них с помощью указателя (щелчок мыши, касание, нажатие кнопки контроллера смешанной реальности и т. д.).

    Здесь приведена базовая структура добавления любого поведения к `onPointerObservable`:

    ```javascript
    scene.onPointerObservable.add((pointerInfo) => {
        // do something
    });
    ```

1. Хотя Babylon.js предоставляет [множество различных типов событий указателя](https://doc.babylonjs.com/typedoc/classes/babylon.pointereventtypes), мы будем использовать только события `POINTERDOWN` и `POINTERUP`, чтобы запрограммировать поведение клавиш пианино, с помощью следующей структуры:

    ```javascript
    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                // When the pointer is down on a piano key,
                // move the piano key downward (to show that it is pressed)
                // and play the sound of the note
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                // When the pointer is released,
                // move the piano key upward to its original position
                // and stop the sound of the note of the key that is released
                break;
        }
    });
    ```

1. Сначала реализуем перемещение клавиши пианино вниз и вверх при ее нажатии и отпускании.

    В событии нажатия указателем нам нужно обнаружить сетку, по которой выполняется щелчок, проверить, что это именно клавиша пианино, и изменить координату сетки по оси Y с небольшим отрицательным смещением, чтобы создать видимость того, что клавиша нажата.

    Событие отпускания с помощью указателя будет более сложным, так как можно отпустить не ту клавишу, на которой было выполнено нажатие. Например, пользователь может с помощью мыши нажать клавишу C4, перетащить указатель на E4, а затем отпустить кнопку. В этом случае нам все равно нужно отпустить нажатую клавишу (C4), а не только клавишу с событием `pointerUp` (E4).

    Рассмотрим приведенный ниже код, позволяющий сделать это:

    ```javascript
    const pointerToKey = new Map();
    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                if(pointerInfo.pickInfo.hit) {
                    const pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    const pointerId = pointerInfo.event.pointerId;
                    if (pickedMesh.parent === keyboard) {
                        pickedMesh.position.y -= 0.5;
                        // play the sound of the note
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                const pointerId = pointerInfo.event.pointerId;
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5;
                    // stop the sound of the note of the key that is released
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });
    ```

    Значение `pointerId` уникально для каждого указателя и позволяет идентифицировать указатель, если у нас есть несколько контроллеров или если мы используем сенсорный экран. Здесь мы инициализировали объект `Map` с именем `pointerToKey` для хранения связи указателя с нажатой клавишей, чтобы мы знали, какую клавишу следует отпустить при отпускании указателя, независимо от его конечного положения.

1. Вот как будет выглядеть взаимодействие с приведенным выше кодом:

    ![Интерактивные клавиши пианино](./images/interactive-piano-keys.gif)

1. Теперь реализуем воспроизведение и приостановку звука при нажатии и отпускании клавиши. Для этого мы воспользуемся библиотекой Javascript с именем **soundfont-player**, которая позволяет легко воспроизводить звуки MIDI выбранного инструмента.

    [Скачайте сжатый код библиотеки](./files/soundfont-player.min.js), сохраните его в папке с файлом *index.html* и включите его в тег `<header>` в файле *index.html*:

    ```html
    <head>
        <title>Babylon Template</title>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <script src="scene.js"></script>
        <script src="soundfont-player.min.js"></script>
        <style>
                body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    ```

    После импорта библиотеки мы теперь можем инициализировать инструмент и воспроизвести/приостановить звуки MIDI с помощью библиотеки:

    ```javascript
    const pianoSound = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');
    const C4 = piano.play("C4"); // Play note C4
    C4.stop(); // Stop note C4
    ```

1. Теперь внедрим эту возможность в события указателя и завершим код для этого раздела:

    ```javascript
    const pointerToKey = new Map()
    const piano = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');

    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                if(pointerInfo.pickInfo.hit) {
                    let pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    let pointerId = pointerInfo.event.pointerId;
                    if (keys.has(pickedMesh)) {
                        pickedMesh.position.y -= 0.5; // Move the key downward
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh,
                            note: pianoSound.play(pointerInfo.pickInfo.pickedMesh.name) // Play the sound of the note
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                let pointerId = pointerInfo.event.pointerId;
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5; // Move the key upward
                    pointerToKey.get(pointerId).note.stop(); // Stop the sound of the note
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });
    ```

    Так как мы назвали сетку каждой клавиши по соответствующей ноте, мы можем легко указать, какую ноту следует воспроизвести, передав имя сетки в функцию `pianoSound.play()`. Также обратите внимание, что мы сохраняем звук в объект сопоставления `pointerToKey`, чтобы мы знали, воспроизведение какого звука нужно прекратить при отпускании клавиши.

## <a name="scaling-the-piano-for-immersive-vr-mode"></a>Изменение размера пианино для режима иммерсивной виртуальной реальности

Теперь вы уже, наверное, поиграли на пианино с помощью мышки (или даже сенсорного экрана) после добавления интерактивных функций. В этом разделе мы перейдем к иммерсивному пространству виртуальной реальности.

1. Чтобы открыть страницу в иммерсивной гарнитуре виртуальной реальности, сначала подключите гарнитуру к компьютеру разработки и обязательно [настройте ее для использования в приложении Windows Mixed Reality](/enthusiast-guide/set-up-windows-mixed-reality). Если вы используете симулятор Windows Mixed Reality, [обязательно включите его](../../../advanced-concepts/using-the-windows-mixed-reality-simulator.md).

1. Теперь вы увидите кнопку иммерсивной виртуальной реальности в правом нижнем углу веб-страницы. Щелкните ее, и вы сможете увидеть пианино на подключенном устройстве смешанной реальности.

    ![Кнопка иммерсивной виртуальной реальности](../images/immersive-vr-button.png)

1. Перейдя в виртуальное пространство, вы можете заметить, что созданное нами пианино просто огромно. В мире виртуальной реальности мы можем стоять только под ним и играть, наводя указатель на клавиши с большого расстояния.

    ![Огромное пианино](./images/huge-piano.jpg)

1. Давайте уменьшим размер пианино, чтобы сделать его похожим на обычное реальное пианино. Для этого нам потребуется функция, позволяющая [масштабировать сетку относительно точки в пространстве](https://doc.babylonjs.com/toolsAndResources/utilities/Pivot#enlargement). Добавьте эту функцию в *scene.js* (за пределами `createScene()`):

    ```javascript
    const scaleFromPivot = function(transformNode, pivotPoint, scale) {
        const _sx = scale / transformNode.scaling.x;
        const _sy = scale / transformNode.scaling.y;
        const _sz = scale / transformNode.scaling.z;
        transformNode.scaling = new BABYLON.Vector3(_sx, _sy, _sz); 
        transformNode.position = new BABYLON.Vector3(pivotPoint.x + _sx * (transformNode.position.x - pivotPoint.x), pivotPoint.y + _sy * (transformNode.position.y - pivotPoint.y), pivotPoint.z + _sz * (transformNode.position.z - pivotPoint.z));
    }
    ```

    Эта функция принимает 3 параметра:
    * **transformNode**: `TransformNode` для масштабирования.
    * **pivotPoint**: объект `Vector3`, указывающий точку, относительно которой выполняется масштабирование.
    * **scale**: коэффициент масштабирования.

1. Мы воспользуемся этой функцией для масштабирования корпуса пианино и клавиш с коэффициентом 0,015, с точкой поворота в начале системы координат. Добавьте вызов функции к функции `createScene()`, поместив ее после `keyboard.position.y += 80;`:

    ```javascript
    // Put this line at the beginning of createScene()
    const scale = 0.015;
    ```

    ```javascript
    // Put this function call after keyboard.position.y += 80;

    // Scale the entire piano
    scaleFromPivot(piano, new BABYLON.Vector3(0, 0, 0), scale);
    ```

1. Также не забудьте применить масштабирование к положению камеры:

    ```javascript
    const alpha =  3*Math.PI/2;
    const beta = Math.PI/50;
    const radius = 220*scale; // scale the radius
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. Теперь, когда мы снова вошли в пространство виртуальной реальности, пианино будет иметь обычный размер.

    ![Обычное стоячее пианино в виртуальной реальности](./images/normal-standup-piano.jpg)

## <a name="enabling-webxr-features"></a>Включение функций WebXR

Теперь, когда мы изменили размер пианино до нужного в пространстве виртуальной реальности, мы включим некоторые интересные функции WebXR для улучшенного взаимодействия с пианино в пространстве.

1. Если вы играли на пианино с помощью контроллеров иммерсивной виртуальной реальности, вы могли заметить, что одновременно можете использовать только один контроллер. Мы включим [поддержку нескольких указателей](https://doc.babylonjs.com/typedoc/interfaces/babylon.iwebxrcontrollerpointerselectionoptions) в пространстве смешанной реальности с помощью [диспетчера функций WebXR](https://doc.babylonjs.com/divingDeeper/webXR/webXRFeaturesManager) в Babylon.js.

    Добавьте следующий код в функцию `createScene()` после строки инициализации `xrHelper`:

    ```javascript
    const featuresManager = xrHelper.baseExperience.featuresManager;

    const pointerSelection = featuresManager.enableFeature(BABYLON.WebXRFeatureName.POINTER_SELECTION, "stable", {
        xrInput: xrHelper.input,
        enablePointerSelectionOnAllControllers: true        
    });
    ```

1. Кроме того, в зависимости от положения начальной точки вам может быть трудно разместиться перед пианино. Если вы знакомы с иммерсивной средой виртуальной реальности, наверное, вы уже знаете о **телепортации**, функции, которая позволяет мгновенно перемещаться на другую точку в пространстве, просто указав на нее.

1. Чтобы использовать [функцию телепортации](https://doc.babylonjs.com/divingDeeper/webXR/WebXRSelectedFeatures#teleportation-module) в Babylon.js, нам сначала нужна сетка пола, на котором мы можем "стоять" в пространстве виртуальной реальности. Добавьте следующий код в функцию `createScene()`, чтобы создать пол:

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 400, height: 400});
    ```

1. Поддержка телепортации также дает еще одну полезную возможность, которая называется [позицией привязки](https://doc.babylonjs.com/divingDeeper/webXR/WebXRSelectedFeatures#snap-to-hotspots). Проще говоря, это определенная позиция, на которую будет перемещен пользователь.

    Например, мы можем задать позицию привязки перед пианино, чтобы пользователи могли легко телепортироваться к такому расположению при наведении указателя на точку рядом с пианино.

    Добавьте приведенный ниже код, чтобы включить функцию телепортации и указать точку привязки:

    ```javascript
    const teleportation = featuresManager.enableFeature(BABYLON.WebXRFeatureName.TELEPORTATION, "stable", {
        xrInput: xrHelper.input,
        floorMeshes: [ground],
        snapPositions: [new BABYLON.Vector3(2.4*3.5*scale, 0, -10*scale)],
    });
    ```

1. Теперь вы сможете легко перемещаться к пианино, телепортируясь к точке привязки перед ним, и сможете нажимать две клавиши одновременно, используя оба контроллера.

    ![Телепортация к пианино](./images/teleportation-demo.gif)

    ![Игра на пианино с помощью контроллеров](./images/play-piano-controller.gif)

## <a name="summary"></a>Сводка

Поздравляем! Вы завершили серию учебников по созданию пианино с помощью Babylon.js и узнали, как выполнять такие действия:

> [!div class="checklist"]
> * создание, размещение и объединение сеток для создания модели клавиатуры пианино;
> * импорт модели Babylon.js для стоячего корпуса пианино;
> * добавление взаимодействий с помощью указателя к каждой клавише пианино;
> * изменение размера сеток на основе точки вращения;
> * включение основных функций WebXR, таких как телепортация и поддержка нескольких указателей.

Ниже приведен готовый код для *scene.js* и *index.html*:

*scene.js*

```javascript
const buildKey = function (scene, parent, props) {
    if (props.type === "white") {
        /*
        Props for building a white key should contain: 
        note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX

        As an example, the props for building the middle C white key would be
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
        */

        // Create bottom part
        const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);

        // Create top part
        const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
        top.position.z =  4.75;
        top.position.x += props.topPositionX;

        // Merge bottom and top parts
        // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
        const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.name = props.note + props.register;
        key.parent = parent;

        return key;
    }
    else if (props.type === "black") {
        /*
        Props for building a black key should contain: 
        note, wholePositionX, register, referencePositionX

        As an example, the props for building the C#4 black key would be
        {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
        */

        // Create black color material
        const blackMat = new BABYLON.StandardMaterial("black");
        blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

        // Create black key
        const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
        key.position.z += 4.75;
        key.position.y += 0.25;
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.material = blackMat;
        key.parent = parent;

        return key;
    }
}

const scaleFromPivot = function(transformNode, pivotPoint, scale) {
    const _sx = scale / transformNode.scaling.x;
    const _sy = scale / transformNode.scaling.y;
    const _sz = scale / transformNode.scaling.z;
    transformNode.scaling = new BABYLON.Vector3(_sx, _sy, _sz); 
    transformNode.position = new BABYLON.Vector3(pivotPoint.x + _sx * (transformNode.position.x - pivotPoint.x), pivotPoint.y + _sy * (transformNode.position.y - pivotPoint.y), pivotPoint.z + _sz * (transformNode.position.z - pivotPoint.z));
}

const createScene = async function(engine) {
    const scale = 0.015;
    const scene = new BABYLON.Scene(engine);

    const alpha =  3*Math.PI/2;
    const beta = Math.PI/50;
    const radius = 220*scale;
    const target = new BABYLON.Vector3(0, 0, 0);

    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);

    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
    light.intensity = 0.6;

    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }

    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});

    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });

    // Lift the piano keyboard
    keyboard.position.y += 80;

    // Scale the entire piano
    scaleFromPivot(piano, new BABYLON.Vector3(0, 0, 0), scale);

    const pointerToKey = new Map()
    const pianoSound = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');

    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                // Only take action if the pointer is down on a mesh
                if(pointerInfo.pickInfo.hit) {
                    let pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    let pointerId = pointerInfo.event.pointerId;
                    if (pickedMesh.parent === keyboard) {
                        pickedMesh.position.y -= 0.5; // Move the key downward
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh,
                            note: pianoSound.play(pointerInfo.pickInfo.pickedMesh.name) // Play the sound of the note
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                let pointerId = pointerInfo.event.pointerId;
                // Only take action if the released pointer was recorded in pointerToKey
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5; // Move the key upward
                    pointerToKey.get(pointerId).note.stop(); // Stop the sound of the note
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });

    const xrHelper = await scene.createDefaultXRExperienceAsync();

    const featuresManager = xrHelper.baseExperience.featuresManager;

    featuresManager.enableFeature(BABYLON.WebXRFeatureName.POINTER_SELECTION, "stable", {
        xrInput: xrHelper.input,
        enablePointerSelectionOnAllControllers: true        
    });

    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 400, height: 400});

    featuresManager.enableFeature(BABYLON.WebXRFeatureName.TELEPORTATION, "stable", {
        xrInput: xrHelper.input,
        floorMeshes: [ground],
        snapPositions: [new BABYLON.Vector3(2.4*3.5*scale, 0, -10*scale)],
    });

    return scene;
}
```

*index.html*

```html
<html>
    <head>
        <title>Babylon Template</title>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <script src="scene.js"></script>
        <script src="soundfont-player.min.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
   <body>
    <canvas id="renderCanvas"></canvas>
    <script>
        const canvas = document.getElementById("renderCanvas"); // Get the canvas element
        const engine = new BABYLON.Engine(canvas, true); // Generate the BABYLON 3D engine

        // Register a render loop to repeatedly render the scene
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

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о разработке JavaScript в смешанной реальности см. в статье [Общие сведения о разработке JavaScript](/javascript-development-overview.md).
