---
title: 5. Добавление кнопки и сброс расположений фигур
description: Часть 5 (из 6) серии руководств по созданию приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, UX Tools, документация, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 8e16865e89c06c37f2932f1828bf8ca5551e6fce
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "96609695"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="370d4-104">5. Добавление кнопки и сброс расположений фигур</span><span class="sxs-lookup"><span data-stu-id="370d4-104">5. Adding a button & resetting piece locations</span></span>

<span data-ttu-id="370d4-105">В предыдущем руководстве мы добавили субъекты взаимодействия с рукой к компонентам Pawn и Manipulator на шахматной доске, чтобы сделать оба эти компонента интерактивными.</span><span class="sxs-lookup"><span data-stu-id="370d4-105">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="370d4-106">В этом разделе показано, как с помощью подключаемого модуля Mixed Reality Toolkit UX Tools можно создать приложение для игры в шахматы с новыми функциями и ссылками на субъекты в схемах.</span><span class="sxs-lookup"><span data-stu-id="370d4-106">In this section, you'll continue to use the Mixed Reality Toolkit UX Tools plugin to build out your chess app with new functions and Actor references in Blueprints.</span></span> <span data-ttu-id="370d4-107">К концу раздела у вас все будет готово к упаковке приложения смешанной реальности и его развертыванию на устройстве или эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="370d4-107">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="370d4-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="370d4-108">Objectives</span></span>

* <span data-ttu-id="370d4-109">Добавление интерактивной кнопки.</span><span class="sxs-lookup"><span data-stu-id="370d4-109">Adding an interactive button</span></span>
* <span data-ttu-id="370d4-110">Создание функции для сброса расположения фигуры.</span><span class="sxs-lookup"><span data-stu-id="370d4-110">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="370d4-111">Подключение кнопки к триггеру, чтобы ее нажатие активировало созданную функцию.</span><span class="sxs-lookup"><span data-stu-id="370d4-111">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="370d4-112">Создание функции сброса</span><span class="sxs-lookup"><span data-stu-id="370d4-112">Creating a reset function</span></span>

<span data-ttu-id="370d4-113">Первым делом необходимо создать схему функции, которая сбрасывает расположение фигуры, возвращая ее на исходное место в сцене.</span><span class="sxs-lookup"><span data-stu-id="370d4-113">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span>

1.  <span data-ttu-id="370d4-114">Откройте **WhiteKing**, щелкните значок **+** рядом с разделом **Functions** (Функции) на панели **My Blueprint** (Моя схема) и присвойте имя **Reset Location** (Сбросить расположение).</span><span class="sxs-lookup"><span data-stu-id="370d4-114">Open **WhiteKing**, select the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location**.</span></span>

2.  <span data-ttu-id="370d4-115">Перетащите закрепление выполнения из функции **Reset Location** в произвольное место сетки схемы, чтобы создать узел **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="370d4-115">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span>
    * <span data-ttu-id="370d4-116">Эта функция задает для субъекта преобразование (расположение, поворот и масштабирование) относительно родительского элемента.</span><span class="sxs-lookup"><span data-stu-id="370d4-116">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="370d4-117">С помощью этой функции мы можем вернуть короля на доске в исходное место, даже если сама доска была перемещена.</span><span class="sxs-lookup"><span data-stu-id="370d4-117">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span>

3. <span data-ttu-id="370d4-118">Щелкните правой кнопкой мыши внутри графа событий, выберите **Make Transform** (Создать преобразование) и задайте для параметра **Location** (Расположение) значения **X = -26**, **Y = 4** и **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="370d4-118">Right-click inside the Event Graph, select **Make Transform**, and change its **Location** to **X = -26**, **Y = 4**, **Z = 0**.</span></span>
    * <span data-ttu-id="370d4-119">Соедините закрепление **Return Value** (Возвращаемое значение) с закреплением **New Relative Transform** (Новое относительное преобразование) элемента **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="370d4-119">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform**.</span></span>

![Функция сброса расположения](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="370d4-121">Скомпилируйте (**Compile**) и сохраните (**Save**) проект, после чего вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="370d4-121">**Compile** and **Save** the project before returning to the Main window.</span></span>


## <a name="adding-a-button"></a><span data-ttu-id="370d4-122">Добавление кнопки</span><span class="sxs-lookup"><span data-stu-id="370d4-122">Adding a button</span></span>

<span data-ttu-id="370d4-123">Теперь, когда функция настроена, следующая задача — создать кнопку, при нажатии которой функция будет выполняться.</span><span class="sxs-lookup"><span data-stu-id="370d4-123">Now that the function is set up correctly, your next task is to create a button that fires it off when touched.</span></span>

1.  <span data-ttu-id="370d4-124">Щелкните **Add New > Blueprint Class** (Добавить > Класс схемы), разверните раздел **All Classes** (Все классы) и введите **UxtPressableButtonActor** для поиска.</span><span class="sxs-lookup"><span data-stu-id="370d4-124">Click **Add New > Blueprint Class**, expand the **All Classes** section, and search for **UxtPressableButtonActor**.</span></span>
    * <span data-ttu-id="370d4-125">Присвойте созданной кнопке имя **ResetButton** и дважды щелкните ее, чтобы открыть соответствующую схему.</span><span class="sxs-lookup"><span data-stu-id="370d4-125">Name it **ResetButton** and double click to open the Blueprint</span></span>

![Создание подкласса схемы из кнопки в стиле HoloLens 2](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="370d4-127">Убедитесь, что параметр **ResetButton(self)** выбран в области **Components** (Компоненты).</span><span class="sxs-lookup"><span data-stu-id="370d4-127">Ensure **ResetButton(self)** is selected in the **Components** panel.</span></span> <span data-ttu-id="370d4-128">В области **Details** (Сведения) перейдите к разделу **Button** (Кнопка).</span><span class="sxs-lookup"><span data-stu-id="370d4-128">In the **Details** panel, navigate to the **Button** section.</span></span> <span data-ttu-id="370d4-129">Укажите для параметра **Button Label** (Метка кнопки) значение Reset (Сбросить), разверните раздел **Button Icon Brush** (Кисть значка с кнопкой) и нажмите кнопку **Open Icon Brush Editor** (Открыть редактор кисти значка).</span><span class="sxs-lookup"><span data-stu-id="370d4-129">Change the default **Button Label** to "Reset", expand the **Button Icon Brush** section, and press the **Open Icon Brush Editor** button.</span></span>

![Настройка метки и значка для кнопки](images/unreal-uxt/5-buttonconfig.PNG)

<span data-ttu-id="370d4-131">Откроется редактор кисти значка, где можно выбрать новый значок для кнопки.</span><span class="sxs-lookup"><span data-stu-id="370d4-131">The Icon Brush Editor will open, which you can use to select a new icon for your button.</span></span>

![Выбор значка для кнопки](images/unreal-uxt/5-iconbrusheditor.PNG)

<span data-ttu-id="370d4-133">Доступно множество параметров, с помощью которых можно настроить кнопку.</span><span class="sxs-lookup"><span data-stu-id="370d4-133">There are plenty of other settings you can adjust to configure your button.</span></span> <span data-ttu-id="370d4-134">Дополнительные сведения о компоненте нажимаемой кнопки UXT см. в [документации](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).</span><span class="sxs-lookup"><span data-stu-id="370d4-134">To learn more about the UXT Pressable Button component, check out the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).</span></span>

3. <span data-ttu-id="370d4-135">В области **Components** (Компоненты) щелкните **ButtonComponent (Inherited)** и прокрутите панель **Details** (Сведения) до раздела **Events** (События).</span><span class="sxs-lookup"><span data-stu-id="370d4-135">Click **ButtonComponent (Inherited)** in the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span>
    * <span data-ttu-id="370d4-136">Нажмите зеленую кнопку **+** рядом с событием **On Button Pressed** (По нажатию кнопки), чтобы добавить это событие в граф событий. Добавленное событие будет инициироваться при нажатии кнопки, которую мы создаем.</span><span class="sxs-lookup"><span data-stu-id="370d4-136">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span>

<span data-ttu-id="370d4-137">Из этого события мы будем вызывать функцию **Reset Location** (Сброс расположения) элемента **WhiteKing**, для чего требуется ссылка на субъект **WhiteKing** на данном уровне.</span><span class="sxs-lookup"><span data-stu-id="370d4-137">From here, you’ll want to call **WhiteKing**’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span>

4.  <span data-ttu-id="370d4-138">На панели **My Blueprint** (Моя схема) перейдите к разделу **Variables** (Переменные), нажмите кнопку **+** и присвойте переменной имя **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="370d4-138">In the **My Blueprint** panel, navigate to the **Variables** section, click the **+** button, and name the variable **WhiteKing**.</span></span>
    * <span data-ttu-id="370d4-139">На панели **Details** (Сведения) щелкните раскрывающийся список рядом с полем **Variable Type** (Тип переменной), затем выполните поиск по слову **WhiteKing** и выберите **Object Reference** (Ссылка на объект).</span><span class="sxs-lookup"><span data-stu-id="370d4-139">In the **Details** panel, select the dropdown next to **Variable Type**, search for **WhiteKing**, and select the **Object Reference**.</span></span>
    * <span data-ttu-id="370d4-140">Установите флажок **Instance Editable** (Редактируемый экземпляр), который позволяет задать переменную на уровне Main.</span><span class="sxs-lookup"><span data-stu-id="370d4-140">Check the box next to **Instance Editable**, which allows the variable to be set from the Main Level.</span></span>

![Создание переменной](images/unreal-uxt/5-var.PNG)

5.  <span data-ttu-id="370d4-142">Перетащите переменную WhiteKing из раздела **My Blueprint > Variables** (Моя схема > Переменные) на граф Reset Button Event Graph (Граф событий кнопки сброса) и выберите **Get WhiteKing** (Получить WhiteKing).</span><span class="sxs-lookup"><span data-stu-id="370d4-142">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing**.</span></span>

## <a name="firing-the-function"></a><span data-ttu-id="370d4-143">Вызов функции</span><span class="sxs-lookup"><span data-stu-id="370d4-143">Firing the function</span></span>

<span data-ttu-id="370d4-144">Теперь осталось сделать так, чтобы при нажатии нашей кнопки вызывалась функция сброса.</span><span class="sxs-lookup"><span data-stu-id="370d4-144">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="370d4-145">Перетащите закрепление вывода WhiteKing и отпустите его для размещения нового узла.</span><span class="sxs-lookup"><span data-stu-id="370d4-145">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="370d4-146">Выберите функцию **Reset Location** (Сброс расположения).</span><span class="sxs-lookup"><span data-stu-id="370d4-146">Select the **Reset Location** function.</span></span> <span data-ttu-id="370d4-147">Наконец, перетащите выходное закрепление выполнения из события **On Button Pressed** (По нажатию кнопки) к входному закреплению выполнения функции **Reset Location** (Сброс расположения).</span><span class="sxs-lookup"><span data-stu-id="370d4-147">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="370d4-148">**Скомпилируйте** и **сохраните** схему ResetButton, а затем вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="370d4-148">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span>

![Вызов функции сброса расположения из события нажатия кнопки](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="370d4-150">Перетащите элемент **ResetButton** в окно просмотра и задайте для него следующее расположение: **X = 50**, **Y = -25**, **Z = 10**.</span><span class="sxs-lookup"><span data-stu-id="370d4-150">Drag **ResetButton** into the viewport and set its location to **X = 50**, **Y = -25**, and **Z = 10**.</span></span> <span data-ttu-id="370d4-151">Задает вращение до **Z = 180**.</span><span class="sxs-lookup"><span data-stu-id="370d4-151">Set its rotation to **Z = 180**.</span></span> <span data-ttu-id="370d4-152">В разделе **Default** (По умолчанию) задайте для переменной **WhiteKing** значение **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="370d4-152">Under **Default**, set the value of the **WhiteKing** variable to **WhiteKing**.</span></span>

![Указание переменной](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="370d4-154">Запустите приложение, переместите фигуру, а затем нажмите кнопку в стиле HoloLens 2 — вы увидите, как работает логика сброса расположения.</span><span class="sxs-lookup"><span data-stu-id="370d4-154">Run the app, move the chess piece to a new location, and press your HoloLens 2-style button to see the reset logic in action!</span></span>

<span data-ttu-id="370d4-155">Теперь у вас есть приложение смешанной реальности с интерактивной фигурой и доской, а также работающая кнопка для сброса расположения этой фигуры.</span><span class="sxs-lookup"><span data-stu-id="370d4-155">You now have a mixed reality app with an interactable chess piece and board, and a fully functioning button that resets the piece’s location.</span></span> <span data-ttu-id="370d4-156">Законченное приложение в том объеме, в котором оно реализовано к данному моменту, вы найдете в репозитории [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span><span class="sxs-lookup"><span data-stu-id="370d4-156">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="370d4-157">Вы можете не ограничиваться примерами из этого руководства и настроить остальные шахматные фигуры так, чтобы при нажатии этой кнопки вся доска принимала исходный вид.</span><span class="sxs-lookup"><span data-stu-id="370d4-157">Feel free to go beyond this tutorial and set up the rest of the chess pieces so that the entire board is reset when you press the reset button.</span></span>

![Готовая сцена в окне просмотра](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="370d4-159">Теперь вы можете переходить к последнему разделу, в котором показано, как упаковать приложение и развернуть его на устройстве или в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="370d4-159">You're ready to move on to the final section of this tutorial where you'll learn how to package and deploy the app to a device or emulator.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="370d4-160">На этом этапе вам необходимо внести изменения в проект с использованием рекомендуемых **[параметров производительности для Unreal](../performance-recommendations-for-unreal.md)** , прежде чем вы развернете приложение на устройстве или в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="370d4-160">At this point, you should update your project with the recommended **[Unreal performance settings](../performance-recommendations-for-unreal.md)** before deploying your application to a device or emulator.</span></span>

[<span data-ttu-id="370d4-161">Следующий раздел: 6. Упаковка и развертывание на устройстве или в эмуляторе</span><span class="sxs-lookup"><span data-stu-id="370d4-161">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
