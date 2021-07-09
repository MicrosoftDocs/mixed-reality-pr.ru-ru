---
title: Руководства по началу работы с babylon.js и WebXR
description: Пройдите этот курс, чтобы узнать, как использовать babylon.js и создавать базовое приложение смешанной реальности.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: смешанная реальность, javascript, учебник, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, иммерсивное веб-приложение
ms.localizationpriority: high
ms.openlocfilehash: 2d3f59b2769f99a756c4f0c10df1d8a8604a595e
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600123"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a><span data-ttu-id="959b7-104">Руководство. Создание первого приложения WebXR с помощью babylon.js</span><span class="sxs-lookup"><span data-stu-id="959b7-104">Tutorial: Create your first WebXR application using babylon.js</span></span>

<span data-ttu-id="959b7-105">В этом руководстве рассказано, как создать базовое приложение смешанной реальности с помощью babylon.js и Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="959b7-105">This tutorial will show you how to create a basic Mixed Reality app using babylon.js and Visual Studio Code.</span></span> <span data-ttu-id="959b7-106">Приложение, которое вы будете собирать, будет визуализировать куб, поворачивать его, чтобы отображать другие грани, и добавлять взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="959b7-106">The app you're going to build will render a cube, let you rotate it to bring the other faces into view, and add interactions.</span></span> <span data-ttu-id="959b7-107">В этом руководстве описано следующее:</span><span class="sxs-lookup"><span data-stu-id="959b7-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="959b7-108">Настройка среды разработки</span><span class="sxs-lookup"><span data-stu-id="959b7-108">Set up a development environment</span></span>
> * <span data-ttu-id="959b7-109">API babylon.js для создания базовых трехмерных элементов</span><span class="sxs-lookup"><span data-stu-id="959b7-109">The babylon.js API to create basic 3D elements</span></span>  
> * <span data-ttu-id="959b7-110">Создание веб-страницы</span><span class="sxs-lookup"><span data-stu-id="959b7-110">Create a new web page</span></span>
> * <span data-ttu-id="959b7-111">Взаимодействие с трехмерными элементами</span><span class="sxs-lookup"><span data-stu-id="959b7-111">Interact with 3D elements</span></span>
> * <span data-ttu-id="959b7-112">Запуск приложения в симуляторе Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="959b7-112">Run the application in a Windows Mixed Reality Simulator</span></span>

## <a name="prerequisites"></a><span data-ttu-id="959b7-113">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="959b7-113">Prerequisites</span></span>

* <span data-ttu-id="959b7-114">Браузер с поддержкой WebXR, например [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span><span class="sxs-lookup"><span data-stu-id="959b7-114">WebXR-supported browser, for example [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span></span>
* <span data-ttu-id="959b7-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="959b7-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 or higher</span></span>
* [<span data-ttu-id="959b7-116">NodeJS</span><span class="sxs-lookup"><span data-stu-id="959b7-116">NodeJS</span></span>](https://nodejs.org/)
* <span data-ttu-id="959b7-117">Необязательно: [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10), если вы хотите использовать симулятор Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="959b7-117">Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) if you want to use a Windows Mixed Reality Simulator</span></span>
* <span data-ttu-id="959b7-118">Необязательно: [симулятор Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="959b7-118">Optional: [Windows Mixed Reality simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="getting-started"></a><span data-ttu-id="959b7-119">Начало работы</span><span class="sxs-lookup"><span data-stu-id="959b7-119">Getting started</span></span>

<span data-ttu-id="959b7-120">Чтобы создать этот проект с нуля, начните с проекта Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="959b7-120">To create this project from scratch, start with a Visual Studio Code (VSCode) project.</span></span>

> [!NOTE]
> <span data-ttu-id="959b7-121">Использование редактора VSCode не является обязательным, но мы будем применять его для удобства в рамках этого руководства.</span><span class="sxs-lookup"><span data-stu-id="959b7-121">Using VSCode isn't mandatory, but we'll be using it for convenience throughout the tutorial.</span></span> <span data-ttu-id="959b7-122">Более опытные разработчики JavaScript могут использовать любой другой редактор по своему выбору, даже простой Блокнот.</span><span class="sxs-lookup"><span data-stu-id="959b7-122">More experienced JavaScript developers can use any other editor of their choice, even the simplest Notepad.</span></span>

1. <span data-ttu-id="959b7-123">Скачайте [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) отдельным файлом или воспользуйтесь интерактивной версией, которую можно найти на [официальном веб-сайте babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span><span class="sxs-lookup"><span data-stu-id="959b7-123">Either download the [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) single file or use an online version that can be found on the [official babylon.js web site](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span></span> <span data-ttu-id="959b7-124">Можно также клонировать весь проект babylon.js из [GitHub](https://github.com/BabylonJS/Babylon.js)</span><span class="sxs-lookup"><span data-stu-id="959b7-124">You can also clone the entire babylon.js project from [GitHub](https://github.com/BabylonJS/Babylon.js)</span></span>
1. <span data-ttu-id="959b7-125">Создайте пустой файл и сохраните его как HTML-страницу, например index.html.</span><span class="sxs-lookup"><span data-stu-id="959b7-125">Create an empty file and save it as html page, for example index.html</span></span>
1. <span data-ttu-id="959b7-126">Создайте базовую разметку HTML и сделайте ссылку на файл JavaScript babylon.js.</span><span class="sxs-lookup"><span data-stu-id="959b7-126">Create a basic html markup and reference the babylon.js javascript file.</span></span> <span data-ttu-id="959b7-127">Готовый код показан ниже.</span><span class="sxs-lookup"><span data-stu-id="959b7-127">The final code is as shown below:</span></span>

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

1. <span data-ttu-id="959b7-128">Добавьте в текст элемент HTML *Canvas*, чтобы отобразить содержимое babylon.js.</span><span class="sxs-lookup"><span data-stu-id="959b7-128">Add a *canvas* HTML element inside the body to render the contents of babylon.js.</span></span> <span data-ttu-id="959b7-129">Обратите внимание, что Canvas содержит атрибут ID, который позволяет получить доступ к этому элементу HTML из JavaScript позже.</span><span class="sxs-lookup"><span data-stu-id="959b7-129">Note that the canvas has an id attribute, which lets you access this HTML element from JavaScript later on.</span></span>

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

1. <span data-ttu-id="959b7-130">Элемент Canvas занимает всю веб-страницу.</span><span class="sxs-lookup"><span data-stu-id="959b7-130">The canvas occupies the entire web page.</span></span> <span data-ttu-id="959b7-131">На этом веб-страница завершается.</span><span class="sxs-lookup"><span data-stu-id="959b7-131">That completes our web page.</span></span> <span data-ttu-id="959b7-132">Теперь страница готова.</span><span class="sxs-lookup"><span data-stu-id="959b7-132">At this point, the web page is ready.</span></span> <span data-ttu-id="959b7-133">Вы можете открыть ее в любом браузере и проверить, нет ли ошибок, хотя на ней еще нет иммерсивных возможностей.</span><span class="sxs-lookup"><span data-stu-id="959b7-133">You can open it in any browser and ensure there are no errors shown, though there is no immersive experience yet.</span></span>

## <a name="next-steps"></a><span data-ttu-id="959b7-134">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="959b7-134">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="959b7-135">Следующее руководство: 2. Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="959b7-135">Next Tutorial: 2. Prepare a scene</span></span>](prepare-scene-02.md)