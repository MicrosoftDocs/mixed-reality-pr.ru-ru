---
title: UMG и клавиатура в Unreal
description: Узнайте, как использовать несферную график движения для создания системы пользовательского интерфейса из мини-приложений.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, HoloLens 2, отслеживание взгляда, ввод с экрана, головной дисплей, нереалный механизм, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, мини-приложения, Пользовательский интерфейс, УМГ, нереалная графика, нереалная подсистема, UE, UE4
ms.openlocfilehash: 59ad108a0e27298256f4f0d1661381a4f1748777
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609765"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="88671-104">UMG и клавиатура в Unreal</span><span class="sxs-lookup"><span data-stu-id="88671-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="88671-105">Нереалная графика движения (УМГ) — это встроенная система пользовательского интерфейса нереального механизма, используемая для создания таких интерфейсов, как меню и текстовые поля.</span><span class="sxs-lookup"><span data-stu-id="88671-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="88671-106">Пользовательские интерфейсы, созданные с помощью УМГ, состоят из мини-приложений.</span><span class="sxs-lookup"><span data-stu-id="88671-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="88671-107">Мы покажем вам создание нового мини-приложения, его добавление в мировое пространство и включение взаимодействия с помощью системной клавиатуры в качестве примера.</span><span class="sxs-lookup"><span data-stu-id="88671-107">We'll guide you through creating a new widget, adding it to world space, and enabling interaction using the system keyboard as an example.</span></span> <span data-ttu-id="88671-108">Дополнительные сведения о УМГ см. в официальной [документации по](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)нереальному подсистеме.</span><span class="sxs-lookup"><span data-stu-id="88671-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="88671-109">Создание нового мини-приложения</span><span class="sxs-lookup"><span data-stu-id="88671-109">Create a new widget</span></span>

- <span data-ttu-id="88671-110">Создайте проект мини-приложения для размещения пользовательского интерфейса игры:</span><span class="sxs-lookup"><span data-stu-id="88671-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Снимок экрана: Добавление схемы мини-приложения из нереального меню](images/unreal-umg-img-01.png)

- <span data-ttu-id="88671-112">Откройте новый проект и добавьте компоненты из палитры на холст.</span><span class="sxs-lookup"><span data-stu-id="88671-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="88671-113">В этом случае мы добавили два компонента текстового поля из раздела input:</span><span class="sxs-lookup"><span data-stu-id="88671-113">In this case, we've added two Text Box components from the “Input” section:</span></span>

![Снимок экрана: окно иерархии с выделенным и развернутым компонентом текстового мини-приложения](images/unreal-umg-img-02.png)

- <span data-ttu-id="88671-115">Выберите мини-приложение в окне "иерархия" или "Конструктор" и измените параметры на панели сведений.</span><span class="sxs-lookup"><span data-stu-id="88671-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="88671-116">В этом случае мы добавили текст подсказок по умолчанию и цвет оттенков, который появляется при наведении указателя мыши на текстовое поле.</span><span class="sxs-lookup"><span data-stu-id="88671-116">In this case, we’ve added some default “Hint Text” and a tint color that appears when you hover over the text box.</span></span>  <span data-ttu-id="88671-117">Текстовое поле будет отображать виртуальную клавиатуру на HoloLens, когда она взаимодействует с:</span><span class="sxs-lookup"><span data-stu-id="88671-117">A text box will pop up a virtual keyboard on HoloLens when it's interacted with:</span></span>

![Снимок экрана измененных параметров в окне иерархии](images/unreal-umg-img-03.png)

- <span data-ttu-id="88671-119">На панели подробностей можно также подписываться на события.</span><span class="sxs-lookup"><span data-stu-id="88671-119">Events can also be subscribed to in the details panel:</span></span>

![Снимок экрана событий на панели подробностей](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="88671-121">Добавление мини-приложения в мировое пространство</span><span class="sxs-lookup"><span data-stu-id="88671-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="88671-122">Создайте субъект, добавьте компонент Widget и добавьте субъект в сцену:</span><span class="sxs-lookup"><span data-stu-id="88671-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![Снимок экрана субъекта с присоединенным мини-приложением](images/unreal-umg-img-05.png)

- <span data-ttu-id="88671-124">На панели подробностей для мини-приложения задайте **класс Widget** для созданной ранее схемы мини-приложения:</span><span class="sxs-lookup"><span data-stu-id="88671-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![Снимок экрана: панель сведений о проекте с набором классов мини-приложений](images/unreal-umg-img-06.png)

- <span data-ttu-id="88671-126">Для мини-приложения текста убедитесь, что флажок **получить аппаратные входные данные** не установлен, поэтому мы обновляем только текст с виртуальной клавиатуры:</span><span class="sxs-lookup"><span data-stu-id="88671-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![Снимок экрана раздела "взаимодействие" с параметром "получить аппаратное устройство ввода" снят](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="88671-128">Взаимодействие мини-приложения</span><span class="sxs-lookup"><span data-stu-id="88671-128">Widget Interaction</span></span>

<span data-ttu-id="88671-129">Мини-приложения УМГ обычно получают входные данные от мыши.</span><span class="sxs-lookup"><span data-stu-id="88671-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="88671-130">В HoloLens или VR необходимо имитировать мышь с компонентом взаимодействия мини-приложения, чтобы получить те же события.</span><span class="sxs-lookup"><span data-stu-id="88671-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="88671-131">Создайте субъект, добавьте компонент взаимодействия с **мини** -приложением и добавьте субъект в сцену:</span><span class="sxs-lookup"><span data-stu-id="88671-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![Снимок экрана: новый субъект с выделенным компонентом взаимодействия мини-приложения](images/unreal-umg-img-08.png)

- <span data-ttu-id="88671-133">На панели подробностей для компонента взаимодействия мини-приложения выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="88671-133">In the details panel for the Widget Interaction component:</span></span>
    - <span data-ttu-id="88671-134">Установка расстояния взаимодействия до нужного значения расстояния</span><span class="sxs-lookup"><span data-stu-id="88671-134">Set the interaction distance to the distance value you want</span></span>
    - <span data-ttu-id="88671-135">Задайте для **источника взаимодействия** значение **Custom** .</span><span class="sxs-lookup"><span data-stu-id="88671-135">Set the **Interaction Source** to **custom**</span></span>
    - <span data-ttu-id="88671-136">Для разработки задайте для параметра **Показывать отладку** **значение true**:</span><span class="sxs-lookup"><span data-stu-id="88671-136">For development, set **Show Debug** to **true**:</span></span>

![Снимок экрана: свойства компонента взаимодействия и отладки мини-приложения](images/unreal-umg-img-09.png)

<span data-ttu-id="88671-138">По умолчанию для источника взаимодействия используется «World», который должен отсылать райкастс на основе расположения в мире компонента взаимодействия мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="88671-138">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component.</span></span> <span data-ttu-id="88671-139">В AR и VR это не так.</span><span class="sxs-lookup"><span data-stu-id="88671-139">In AR and VR, that's not the case.</span></span>  <span data-ttu-id="88671-140">Включение функции "показывать отладку" и добавление оттенок при наведении для мини-приложений важно для проверки того, что компонент взаимодействия мини-приложения выполняет предполагаемое действие.</span><span class="sxs-lookup"><span data-stu-id="88671-140">Enabling “Show Debug” and adding a hover tint to widgets is important to check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="88671-141">Обходной путь заключается в использовании настраиваемого источника и задании райкаст в графе событий с рука-Ray.</span><span class="sxs-lookup"><span data-stu-id="88671-141">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="88671-142">Здесь мы вызываем этот метод из Tick события:</span><span class="sxs-lookup"><span data-stu-id="88671-142">Here we're calling this from Event Tick:</span></span>

![План такта события](images/unreal-umg-img-10.png)

<span data-ttu-id="88671-144">Затем добавьте виртуальные события указателя мыши в компонент взаимодействия мини-приложения, передействующий в входные данные HoloLens.</span><span class="sxs-lookup"><span data-stu-id="88671-144">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="88671-145">В этом случае отправьте событие щелчка левой кнопкой мыши, когда продается рука, и событие выпуска левой кнопки мыши при невозможности:</span><span class="sxs-lookup"><span data-stu-id="88671-145">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![Схема с добавленными виртуальными событиями указателя мыши](images/unreal-umg-img-13.png)

<span data-ttu-id="88671-147">Теперь, когда вы развертываете приложение в HoloLens 2, вы увидите, что с правой стороны будет расширяться луч.</span><span class="sxs-lookup"><span data-stu-id="88671-147">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="88671-148">Если вы направите его по одному из редактируемых текстовых полей и просто коснитесь, системная клавиатура появится перед вами и позволит ввести текст.</span><span class="sxs-lookup"><span data-stu-id="88671-148">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="88671-149">Для системной клавиатуры HoloLens требуется нереалия ядра 4,26 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="88671-149">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="88671-150">Кроме того, клавиатура не отображается при потоковой передаче приложения из нереального редактора в гарнитуру, только если приложение выполняется на устройстве.</span><span class="sxs-lookup"><span data-stu-id="88671-150">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="88671-151">См. также:</span><span class="sxs-lookup"><span data-stu-id="88671-151">See Also:</span></span>
* [<span data-ttu-id="88671-152">Документация по УМГ в реальном времени</span><span class="sxs-lookup"><span data-stu-id="88671-152">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="88671-153">Практические руководства УМГ</span><span class="sxs-lookup"><span data-stu-id="88671-153">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
