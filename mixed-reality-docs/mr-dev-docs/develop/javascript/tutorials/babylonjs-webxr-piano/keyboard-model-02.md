---
title: Создание трехмерной модели пианино
description: Сведения о том, как создать трехмерную модель пианино с помощью кода Babylon.js.
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: смешанная реальность, javascript, учебник, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, иммерсивное веб-приложение
ms.localizationpriority: high
ms.openlocfilehash: e5c3dd6206566f781ceb52e5d13a49a0c9ab1018
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932515"
---
# <a name="tutorial-build-a-3d-piano-model"></a>Учебник. Создание трехмерной модели пианино

В предыдущем учебнике из серии мы настроили веб-страницу, содержащую сцену на Babylon.js с камерой и источником света. В этом учебнике мы создадим модель пианино и добавим ее в сцену.

![Сетка стоячего пианино](./images/standup-piano-mesh.png)

В этом учебнике рассматривается следующее.

> [!div class="checklist"]
> * Создание, позиционирование и слияние сеток
> * Создание клавиатуры пианино из прямоугольных сеток
> * Импорт трехмерной модели корпуса пианино

## <a name="before-you-begin"></a>Перед началом

Обязательно изучите [предыдущий учебник в серии](introduction-01.md), чтобы продолжить написание кода.

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

## <a name="getting-started"></a>Начало работы

Начнем с создания простой клавиатуры пианино, имеющей следующую структуру:

![Описание регистра пианино](./images/piano-register.jpg)

На этом рисунке имеется 7 белых клавиш и 5 черных клавиш, каждая из которых помечена названием ноты. Полная клавиатура с 88 клавишами содержит 7 полных повторений такого набора клавиш (также называется регистром) и 4 дополнительных клавиши. Каждый регистр имеет удвоенную частоту предыдущего регистра. Например частота колебаний C5 (нота C в пятом регистре) в два раза выше частоты C4, частота D5 в два раза выше D4 и так далее.

Визуально каждый регистр неотличим от остальных, поэтому мы можем начать с изучения того, как создать простую клавиатуру пианино с таким набором клавиш. Позже мы можем реализовать полную клавиатуру с 88 клавишами.

## <a name="build-a-simple-piano-keyboard"></a>Создание простой клавиатуры пианино

> [!NOTE]
> Хотя вы можете найти готовые трехмерные модели с клавиатурами пианино в сетевых источниках и импортировать их в нашу веб-страницу, в этом учебнике мы создадим клавиатуру с нуля, чтобы обеспечить максимальные возможности настройки и продемонстрировать, как создавать трехмерные модели с помощью Babylon.js.

1. Прежде чем приступать к созданию сеток для клавиатуры, обратите внимание, что каждая черная клавиша не выровнена точно между двух белых клавиш и клавиши имеют разную ширину. Это означает, что нужно создать и разместить сетку для каждой клавиши по отдельности.

    ![Выравнивание черных клавиш](./images/black-key-position.png)

1. Можно увидеть, что каждая белая клавиша состоит из двух частей: (1) нижняя часть под черными клавишами и (2) верхняя часть рядом с черными клавишами. Эти части имеют разные размеры, но вместе образуют цельную белую клавишу.

    ![Форма белых клавиш](./images/white-key-shape-label.png)

1. Ниже приведен код для создания одной белой клавиши для ноты C (пока не нужно беспокоиться о его добавлении в *scene.js*):

    ```javascript
    const whiteKeyBottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: 2.3, height: 1.5, depth: 4.5}, scene);
    const whiteKeyTop = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: 1.4, height: 1.5, depth: 5}, scene);
    whiteKeyTop.position.z += 4.75;
    whiteKeyTop.position.x -= 0.45;

    // Parameters of BABYLON.Mesh.MergeMeshes:
    // (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
    const whiteKeyV1 = BABYLON.Mesh.MergeMeshes([whiteKeyBottom, whiteKeyTop], true, false, null, false, false);
    whiteKeyV1.material = whiteMat;
    whiteKeyV1.name = "C4";
    ```

    Здесь мы создали две [прямоугольных](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box#box-mesh) сетки: одна для нижней части и другая для верхней части белых клавиш. Затем мы изменим положение верхней части так, чтобы поместить ее поверх нижней со сдвигом влево, чтобы оставить место для соседней черной клавиши (C#).

    Наконец, объединим эти две части с помощью функции [MergeMeshes](https://doc.babylonjs.com/divingDeeper/mesh/mergeMeshes) для создания цельной белой клавиши. Готовая сетка, которая создается этим кодом:

    ![Белая клавиша C](./images/white-key-c.png)

1. Создать черную клавишу проще. Так как все черные клавиши имеют прямоугольную форму, можно создать черную клавишу, просто создав прямоугольную сетку со [StandardMaterial](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction#color) черного цвета.

    > [!NOTE]
    > Так как по умолчанию сетка имеет светло-серый цвет, похожий на белый, в этом учебнике не рассматриваются шаги по добавлению материала белого цвета к белым клавишам. Но вы можете самостоятельно добавить материал, если хотите, чтобы ваши клавиши имели естественный белый цвет.

    Ниже приведен код для создания черной клавиши C# (не беспокойтесь о добавлении этого кода в *scene.js*):

    ```javascript
    const blackMat = new BABYLON.StandardMaterial("black");
    blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

    const blackKey = BABYLON.MeshBuilder.CreateBox("C#4", {width: 1.4, height: 2, depth: 5}, scene);
    blackKey.position.z += 4.75;
    blackKey.position.y += 0.25;
    blackKey.position.x += 0.95;
    blackKey.material = blackMat;
    ```

    Черная клавиша, созданная этим кодом (вместе с предыдущей белой клавишей), будет выглядеть следующим образом:

    ![Черная клавиша (C#)](./images/black-key-csharp.png)

1. Как видите, при создании каждой клавиши мы используем множество похожих фрагментов кода, так как нам нужно задать размеры и расположение каждой из них. В следующем разделе мы попробуем упростить весь процесс создания.

## <a name="build-a-simple-piano-keyboard-efficiently"></a>Эффективное создание простой клавиатуры пианино

1. Хотя каждая белая клавиша имеет свою форму, каждую из них можно создать совмещением верхней и нижней частей. Поэтому мы реализуем общую функцию для создания и размещения любой белой клавиши.

    Добавьте функцию ниже в *scene.js*, за функцией `createScene()`:

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
    }
    ```

    В этом блоке кода мы создали функцию с именем `buildKey()`, которая создает и возвращает белую клавишу, если `props.type` имеет значение `"white"`. Определив тип клавиши в параметре `props`, мы можем создать черные и белые клавиши в одной функции, создав ответвление с помощью инструкции if.

    Используются следующие параметры `buildKey()`:
    * **scene**: сцена, в которой располагается клавиша.
    * **parent**: родительский элемент сетки (позволяет нам сгруппировать все клавиши в одном родительском элементе).
    * **props**: свойства создаваемой клавиши.

    `props` для белой клавиши будет содержать следующие элементы:
    * **type**: "white" (белый).
    * **name**: имя ноты для клавиши.
    * **topWidth**: ширина верхней части.
    * **bottomWidth**: ширина нижней части.
    * **topPositionX**: положение верхней части по оси X относительно нижней части.
    * **wholePositionX**: положение всей клавиши по оси X относительно конечной точки регистра (правый край клавиши B).
    * **register**: регистр, к которому принадлежит клавиша (число от 0 до 8).
    * **referencePositionX**: координата X конечной точки регистра (используется в качестве контрольной точки).

    Разделив `wholePositionX` и `referencePositionX`, мы сможем инициализировать параметры `props`, необходимые для создания клавиши определенного типа (например, C) в любом регистре, а затем добавить `register` и `referencePositionX` в `props` при создании такой клавиши в определенном регистре (например, C4, C5).

1. Аналогичным образом также можно написать универсальную функцию для создания черной клавиши. Развернем функцию `buildKey()`, чтобы включить такую логику:

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
    ```

    `props` для черной клавиши содержит следующие элементы:

    * **type**: "black" (черный).
    * **name**: имя ноты для клавиши.
    * **wholePositionX**: положение всей клавиши по оси X относительно конечной точки регистра (правый край клавиши B).
    * **register**: регистр, к которому принадлежит клавиша (число от 0 до 8).
    * **referencePositionX**: координата X конечной точки регистра (используется в качестве контрольной точки).

    Структура `props` для создания черной клавиши намного проще, так как для этого требуется только создать параллелепипед, а ширина и положение по оси Z каждой черной клавиши одинаковы.

1. Теперь, когда мы можем намного проще создать клавиши, инициализируем массив с `props` для каждой клавиши, соответствующей ноте в регистре, а затем вызовем функцию `buildKey()` с каждой из них, чтобы создать простую клавиатуру в четвертом регистре.

    Мы также создадим [TransformNode](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/transform_node#a-transformnode) с именем `keyboard` в качестве [родительского элемента](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/parent#overview-of-a-parent) всех клавиш пианино. Так как любое изменение положения или размера, примененное к родительскому элементу, также применяется к дочерним элементам, такая группировка клавиш позволит масштабировать или перемещать их одновременно.

    Добавьте следующие строки кода в функцию `createScene()`:

    ```javascript
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

    keyParams.forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
    })
    ```

    Как вы, наверное, заметили, в этом блоке кода мы располагаем все клавиши относительно их исходной точки в пространстве.

1. Вот код, который на данный момент содержит *scene.js*:

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
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
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
    
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
        })

        const xrHelper = await scene.createDefaultXRExperienceAsync();

        return scene;
    }
    ```

1. Вот так будет выглядеть результат:

    ![Клавиатура пианино с одним регистром](./images/piano-one-register.png)

## <a name="expanding-to-an-88-key-piano"></a>Расширение до пианино с 88 клавишами

В этом разделе мы расширим использование функций для создания клавиш, чтобы создать полную клавиатуру пианино с 88 клавишами.

1. Как было сказано ранее, полная клавиатура пианино с 88 клавишами содержит 7 повторяющихся регистров и 4 других ноты. Три таких ноты находятся в регистре 0 (левый край клавиатуры), а одна нота — в регистре 8 (правый край клавиатуры).

    ![Структура пианино с 88 клавишами](./images/88-key-piano-keyboard-layout.jpg)

1. Сначала мы создадим 7 полных повторений, добавив еще один цикл вокруг написанного ранее цикла. Замените предыдущий цикл для функции `buildKey()` следующим кодом:

    ```javascript
    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }
    ```

    В этом цикле мы создадим клавиши для регистров с 1 до 7 и инкрементно будем увеличивать контрольную позицию каждый раз при переходе к следующему регистру.

1. Затем мы создадим все остальные клавиши. Добавьте следующий фрагмент в функцию `createScene()`:

    ```javascript
    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    ```

    Обратите внимание, что клавиша с левого края и клавиша с правого края пианино не вписываются в размеры объекта props, определенные в `keyParams` (так как они не располагаются рядом с черной клавишей с другого края), поэтому нам нужно определить новый объект `props` для каждой из них, чтобы задать особую форму.

1. После внесенных изменений клавиатура должна выглядеть следующим образом:

    ![Сетка полной клавиатуры пианино](./images/full-keyboard-mesh.png)

## <a name="adding-a-piano-frame"></a>Добавление корпуса пианино

1. Сцена выглядит немного странно с клавиатурой, подвешенной в пространстве. Поэтому мы добавим стоячий корпус для клавиатуры.

1. Аналогично тому, как мы создали клавиши, мы также можем создать корпус путем размещения и сочетания группы прямоугольных сеток.

    Но мы предоставим вам возможность самостоятельно решить эту задачу с использованием [BABYLON.SceneLoader.ImportMesh](https://doc.babylonjs.com/divingDeeper/importers/loadingFileTypes#sceneloaderimportmesh) для импорта готовой сетки стоячего корпуса пианино. Добавьте следующий фрагмент кода в `createScene()`:

    ```javascript
    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });
    ```

    Обратите внимание, что мы снова создаем родительский элемент `TransformNode` с именем `piano` для группировки клавиатуры и каркаса как единого целого. Это значительно упростит перемещение или изменение размера пианино (если нам это потребуется).

1. После импорта корпуса обратите внимание, что клавиатура располагается в нижней его части (так как по умолчанию клавиши имеют нулевые координаты по оси Y). Давайте приподнимем клавиатуру, чтобы она поместилась в стоячем корпусе пианино:

    ```javascript
    // Lift piano keys
    keyboard.position.y += 80;
    ```

    Так как `keyboard` является родительским элементом всех клавиш пианино, мы можем поднять все клавиши, просто изменив положение `keyboard` по оси Y.

1. Финальный код *scene.js* должен выглядеть следующим образом:

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

1. Теперь у нас есть такое пианино: ![Сетка стоячего пианино](./images/standup-piano-mesh.png)

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Следующий учебник: Игра на трехмерном пианино](keyboard-interaction-03.md)
