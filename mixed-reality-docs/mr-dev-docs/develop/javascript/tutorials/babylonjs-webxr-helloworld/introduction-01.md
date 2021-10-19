---
title: Руководства по началу работы с babylon.js и WebXR
description: Пройдите этот курс, чтобы узнать, как использовать babylon.js и создавать базовое приложение смешанной реальности.
author: vtieto
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: смешанная реальность, javascript, учебник, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, иммерсивное веб-приложение
ms.localizationpriority: high
ms.openlocfilehash: c733cca2ed9cf60e8d0ea8bf8692fbb22ef72292
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130155050"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a>Руководство. Создание первого приложения WebXR с помощью babylon.js

В этом руководстве рассказано, как создать базовое приложение смешанной реальности с помощью babylon.js и Visual Studio Code. Приложение, которое вы будете собирать, будет визуализировать куб, поворачивать его, чтобы отображать другие грани, и добавлять взаимодействия. В этом руководстве описано следующее:

> [!div class="checklist"]
> * Настройка среды разработки
> * API babylon.js для создания базовых трехмерных элементов  
> * Создание веб-страницы
> * Взаимодействие с трехмерными элементами
> * Запуск приложения в симуляторе Windows Mixed Reality

## <a name="prerequisites"></a>Предварительные требования

* Браузер с поддержкой WebXR, например [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 или более поздней версии
* [NodeJS](https://nodejs.org/)
* Необязательно: [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10), если вы хотите использовать симулятор Windows Mixed Reality
* Необязательно: [симулятор Windows Mixed Reality](../../../advanced-concepts/using-the-windows-mixed-reality-simulator.md)

## <a name="getting-started"></a>Начало работы

Чтобы создать этот проект с нуля, начните с проекта Visual Studio Code (VSCode).

> [!NOTE]
> Использование редактора VSCode не является обязательным, но мы будем применять его для удобства в рамках этого руководства. Более опытные разработчики JavaScript могут использовать любой другой редактор по своему выбору, даже простой Блокнот.

1. Скачайте [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) отдельным файлом или воспользуйтесь интерактивной версией, которую можно найти на [официальном веб-сайте babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers). Можно также клонировать весь проект babylon.js из [GitHub](https://github.com/BabylonJS/Babylon.js)
1. Создайте пустой файл и сохраните его как HTML-страницу, например index.html.
1. Создайте базовую разметку HTML и сделайте ссылку на файл JavaScript babylon.js. Готовый код показан ниже.

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
        </head>
    <body>
    </body>
    </html>
    ```

1. Добавьте в текст элемент HTML *Canvas*, чтобы отобразить содержимое babylon.js. Обратите внимание, что Canvas содержит атрибут ID, который позволяет получить доступ к этому элементу HTML из JavaScript позже.

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

1. Элемент Canvas занимает всю веб-страницу. На этом веб-страница завершается. Теперь страница готова. Вы можете открыть ее в любом браузере и проверить, нет ли ошибок, хотя на ней еще нет иммерсивных возможностей.

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Следующее руководство: 2. Подготовка сцены](prepare-scene-02.md)