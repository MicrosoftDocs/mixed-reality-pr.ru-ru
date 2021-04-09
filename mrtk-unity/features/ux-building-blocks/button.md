---
title: Кнопки
description: Общие сведения о кнопках в МРТК
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Смешанная реальность, разработка, МРТК, кнопки МРТК
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003121"
---
# <a name="button"></a>Кнопка

![Кнопка "Main"](../images/button/MRTK_Button_Main.png)

Кнопка предоставляет пользователю возможность вызвать немедленное действие. Это один из самых базовых компонентов в смешанной реальности. МРТК предоставляет различные типы кнопок Prefabs.

## <a name="button-prefabs-in-mrtk"></a>Кнопка Prefabs в МРТК

Примеры кнопки Prefabs в ``MRTK/SDK/Features/UX/Interactable/Prefabs`` папке

### <a name="unity-ui-imagegraphic-based-buttons"></a>Изображение или кнопки на основе графического интерфейса Unity

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>Кнопки на основе "конфликты"

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) PressableButtonHoloLens2 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) PressableButtonHoloLens2Unplated 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) PressableButtonHoloLens2Circular 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    Кнопка в стиле "оболочка" HoloLens 2 с поддержкой обратной связи, которая поддерживает различные визуальные отзывы, такие как границы, освещение и сжатые формы спереди.
    :::column-end:::
    :::column:::
    Кнопка типа оболочки HoloLens 2 без формы
    :::column-end:::
    :::column:::
    Кнопка типа оболочки HoloLens 2 с круглой фигурой
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    ![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    Широкая кнопка в стиле 32x96mm HoloLens 2
    :::column-end:::
    :::column:::
    Горизонтальная панель кнопки HoloLens 2 с общей службой
    :::column-end:::
    :::column:::
    Вертикальная панель кнопки HoloLens 2 с общей службой
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    32x32mm. флажок в стиле оболочки HoloLens 2
    :::column-end:::
    :::column:::
    32x32mm коммутатора HoloLens 2 в стиле оболочки 
    :::column-end:::
    :::column:::
    32x32mm-радио в стиле оболочки HoloLens 2
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96** 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    32x96mm. флажок в стиле оболочки HoloLens 2
    :::column-end:::
    :::column:::
    32x96mm коммутатора HoloLens 2 в стиле оболочки
    :::column-end:::
    :::column:::
    32x96mm-радио в стиле оболочки HoloLens 2
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![Радиальный ](../images/button/MRTK_Button_Radial.png) **радиальный**
    :::column-end:::
    :::column:::
    ![Флажок](../images/button/MRTK_Button_Checkbox.png) **Флажок**
    :::column-end:::
    :::column:::
    ![Тогглесвитч ](../images/button/MRTK_Button_ToggleSwitch.png) **тогглесвитч**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Радиальная кнопка 
    :::column-end:::
    :::column:::
    Флажок 
    :::column-end:::
    :::column:::
    Тумблер
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**
    :::column-end:::
    :::column:::
    ![Прессаблераундбуттон ](../images/button/MRTK_Button_Round.png) **прессаблераундбуттон** 
    :::column-end:::
    :::column:::
    ![Кнопка "Базовая" кнопки ](../images/button/MRTK_Button_Base.png) 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Кнопка стиля оболочки 1-го поколения HoloLens
    :::column-end:::
    :::column:::
    Кнопка "круглая фигура"
    :::column-end:::
    :::column:::
    Кнопка "базовый"
    :::column-end:::
:::row-end:::

`Button`Ресурсы (Asset/мртк/SDK/Features/UX/взаимодействовать/Prefabs/Button. prefab) основаны на [взаимодействующей](interactable.md) концепции, обеспечивающей простоту элементов управления пользовательского интерфейса для кнопок или других типов интерактивных поверхностей. Кнопка базовые показатели поддерживает все доступные входные методы, включая вводные данные для практических действий, а также взгляните + Air — касание для дальнего взаимодействия. Можно также использовать команду Voice для активации кнопки.

`PressableButtonHoloLens2` (Assets/МРТК/SDK/Features/UX/взаимодействовать/Prefabs/PressableButtonHoloLens2. prefab) — это кнопка в стиле оболочки HoloLens 2, которая поддерживает точное перемещение кнопки для входных данных прямого отслеживания. Он сочетает `Interactable` скрипт со `PressableButton` сценарием.

Для HoloLens 2 рекомендуется использовать кнопки с непрозрачной службой. Прозрачные кнопки не рекомендуются из-за таких проблем с удобством использования и стабильностью:

* Трудно прочитать значок и текст в физической среде.
* Трудно понять, когда триггер события
* Голограммы, отображаемые с помощью прозрачной плоскости, могут быть нестабильными с глубиной ЛСР в HoloLens 2 стабилизации

![Пластина кнопки](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>Использование нажатых кнопок

### <a name="unity-ui-based-buttons"></a>Кнопки на основе пользовательского интерфейса Unity

Создание холста в сцене (GameObject-> пользовательского интерфейса > Canvas). На панели инспектора для холста:

* Щелкните "преобразовать в МРТК холст".
* Нажмите кнопку "добавить Неаринтерактионтаучаблеунитюи".
* Установить масштаб X, Y и Z компонента преобразования Rect в значение 0,001

Затем перетащите `PressableButtonUnityUI` (Assets/мртк/SDK/Features/UX/взаимодействовать/Prefabs/прессаблебуттонунитюи. prefab), `PressableButtonUnityUICircular` (Assets/МРТК/SDK/Features/UX/взаимодействовать/Prefabs/прессаблебуттонунитюиЦиркулар. prefab) или `PressableButtonHoloLens2UnityUI` (Assets/мртк/SDK/FEATUREs/UX/взаимодействовать/Prefabs/PressableButtonHoloLens2UnityUI. prefab) на холст.

### <a name="collider-based-buttons"></a>Кнопки на основе "конфликты"

Просто перетащите `PressableButtonHoloLens2` (Assets/мртк/SDK/Features/UX/взаимодействовать/Prefabs/PressableButtonHoloLens2. prefab) или `PressableButtonHoloLens2Unplated` (Assets/МРТК/SDK/Features/UX/взаимодействовать/Prefabs/PressableButtonHoloLens2Unplated. prefab) в сцену. Эти кнопки Prefabs уже настроены на воспроизведение звука для различных типов входных данных, включая ввод с клавиатуры и взгляд.

События, предоставляемые в prefab, а также [взаимодействующий](interactable.md) компонент, можно использовать для активации дополнительных действий. Нажатые кнопки в [сцене хандинтерактионексампле](../example-scenes/hand-interaction-examples.md) используют интерактивное событие *OnClick* для активации изменения в цвете Куба. Это событие активируется для различных типов методов ввода, таких как "взгляд", "Воздушный нажим", "рука-Ray", а также для нажатия физической кнопки с помощью сценария "нажатая кнопка".

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

Можно настроить, когда нажатая кнопка вызывает событие *OnClick* с помощью `PhysicalPressEventRouter` кнопки. Например, можно установить *OnClick* , чтобы срабатывать при первом нажатии кнопки, а не при нажатии и освобождении, настроив параметр *"взаимодействовать"* при нажатии кнопки " *событие при нажатии*".

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

Чтобы воспользоваться конкретными сведениями о состоянии ввода, можно использовать нажатые кнопки события: начать, *сенсорный элемент*, *нажата* кнопка, *кнопка* *запущена*. Однако эти события не будут срабатывать в ответ на вход воздуха, руки или глаз. **Чтобы обеспечить поддержку практических и дальнего взаимодействия, рекомендуется использовать интерактивное событие *OnClick* .**

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a>Состояния взаимодействия

В состоянии простоя Передняя пластина кнопки не видна. В качестве подходов к отпечатку пальца или курсора, направленного на ввод целевого объекта, отображается рамка свечения передней формы. На поверхности передней панели имеется дополнительное выделение заданной должности. При отправке с помощью пальца Передняя пластина перемещается вместе с рукой. Когда вы наводите указатель мыши на поверхность передней панели, он показывает слабый импульс, позволяющий визуально отразить сенсорную точку.

В командной строке HoloLens 2 существует множество визуальных подсказок и аффорданцес для повышения достоверности пользователя при взаимодействии.

|  ![Неблизкое освещение](../images/button/ux_button_affordance_proximitylight.jpg) | ![Выделение фокуса](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Сжатие контейнера](../images/button/ux_button_affordance_compression.jpg) | ![Импульс на триггере](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| Неблизкое освещение | Выделение фокуса | Сжатие контейнера | Импульс на триггере |

Ненавязчивый импульс активируется нажатой кнопкой, которая ищет *проксимитилигхт (s)* , которые находятся на текущем взаимодействующем указателе. Если обнаружены индикаторы близости, `ProximityLight.Pulse` вызывается метод, который автоматически анимируется параметры шейдера для вывода импульса.

## <a name="inspector-properties"></a>Свойства инспектора

![Структура кнопки](../images/button/MRTK_Button_Structure.png)

**Конфликт Box** 
 `Box Collider` для передней панели кнопки.

**Нажатая кнопка** Логика движения кнопки с помощью действия руки.

**Маршрутизатор событий физического нажатия** Этот сценарий отправляет события из руки и [взаимодействует](interactable.md)с пользователем.

**Взаимодействие** 
 [Взаимодействие](interactable.md) обрабатывает различные типы состояний взаимодействия и событий. Этот сценарий непосредственно обрабатывает входные данные и ввод с помощью HoloLens, жестов, голоса и впечатляющих видеоконтроллеров.

**Источник звука** Источник звука Unity для аудиоклипов с отзывами.

*Неаринтерактионтаучабле. CS* требуется для того, чтобы любой объект с сенсорным вводом был управляемым.

## <a name="prefab-layout"></a>Макет prefab

Объект *буттонконтент* содержит переднюю форму, текстовую метку и значок. *Фронтплате* реагирует на близость индекса с помощью шейдера *Button_Box* . В нем показаны свечение границ, световой эффект и импульсное воздействие на касание. Текстовая метка создается с помощью Текстмеш Pro. Видимость *сиитсайитлабел* контролируется темой [взаимодействия](interactable.md).

![Макет кнопки](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>Изменение значка и текста

Кнопки МРТК используют `ButtonConfigHelper` компонент для изменения значка кнопки, текста и метки. (Обратите внимание, что некоторые поля могут отсутствовать, если элементы не представлены на выбранной кнопке.)

![Вспомогательная функция настройки кнопки](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>Создание и изменение наборов значков

**Набор значков** — это общий набор ресурсов значков, используемых `ButtonConfigHelper` компонентом. Поддерживаются три *стиля* значков.

* **Четыре** значка визуализируются с помощью `MeshRenderer` . Это стиль значка по умолчанию.
* Значки **спрайтов** подготавливаются к просмотру с помощью `SpriteRenderer` . Это полезно, если вы предпочитаете импортировать значки в виде листа спрайта или хотите предоставить доступ к ресурсам значков с компонентами пользовательского интерфейса Unity. Чтобы использовать этот стиль, необходимо установить пакет редактора спрайтов **(Windows-> диспетчер пакетов — > 2D-спрайт)** .
* Значки **char** подготавливаются к просмотру с помощью `TextMeshPro` компонента. Это полезно, если вы предпочитаете использовать шрифт значка. Чтобы использовать шрифт значка HoloLens, потребуется создать `TextMeshPro` ресурс шрифта.

Чтобы изменить стиль, используемый для кнопки, разверните раскрывающийся список *значки* в буттонконфигхелпер и выберите из раскрывающегося списка *стиль значка* .

Новый набор значков кнопок можно создать с помощью меню актив: **создать > набор средств для смешанной реальности > набора значков.** Чтобы добавить четыре значка и значки спрайтов, просто перетащите их в соответствующие массивы. Чтобы добавить значки char, необходимо сначала создать и назначить ресурс-контейнер шрифта.

В МРТК 2,4 и более поздних версиях мы рекомендуем перемещать текстуры пользовательских значков в виде значков.
Чтобы обновить ресурсы на всех кнопках в проекте до нового рекомендуемого формата, используйте Буттонконфигхелпермигратионхандлер.
(Набор средств для смешанной реальности — > служебные программы — > окно миграции — выбор обработчика миграции > — > Microsoft. Микседреалити. Toolkit. Utilities. Буттонконфигхелпермигратионхандлер)

Импорт пакета Microsoft. Микседреалититулкит. Unity. Tools, необходимого для обновления кнопок.

![Диалоговое окно обновления](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Если значок не найден в наборе значков по умолчанию во время миграции, в Микседреалититулкит. Generated/Кустомиконсетс будет создан пользовательский набор значков. В диалоговом окне будет указано, что выполнено.

![Уведомление о настраиваемом значке](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>Создание ресурса шрифта значка HoloLens

Сначала импортируйте шрифт значка в Unity. На компьютерах с Windows шрифт HoloLens по умолчанию можно найти в *Windows/Fonts/holomdl2. ttf.* Скопируйте и вставьте этот файл в папку Assets.

Затем откройте средство создания ресурса шрифта Текстмешпро с помощью **окна > текстмешпро > "создатель ресурса шрифта".** Ниже приведены рекомендуемые параметры для создания шрифта HoloLens Atlas. Чтобы включить все значки, вставьте следующий диапазон Юникода в поле *последовательности символов* :

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Создание кнопки 1](../images/button/MRTK_Font_Asset_Creation_1.png)

После создания ресурса шрифта сохраните его в свой проект и присвойте ему поле *шрифта со значком char* в наборе значков. Теперь раскрывающийся список *Доступные значки* будет заполнен. Чтобы сделать значок доступным для кнопки, щелкните его. Он будет добавлен в раскрывающийся список *Выбранные значки* и теперь будет отображаться в, `ButtonConfigHelper.` при необходимости можно дать значку тег. Это позволяет задать значок во время выполнения.

![Создание кнопки 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Создание кнопки 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

Чтобы использовать набор значков, нажмите кнопку, разверните раскрывающийся список значков в `ButtonConfigHelper` и назначьте его полю *набора значков* .

![Набор значков кнопок](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>Изменение размера кнопки

Размер кнопки в стиле оболочки HoloLens 2 — 32x32mm. Чтобы настроить измерение, измените размер этих объектов на кнопке Prefab:

1. **фронтплате**
2. **Четыре** непечатных панели
3. **Box конфликтует** в корне

Затем нажмите кнопку **исправить границы** в скрипте неаринтерактионтаучабле, который находится в корне кнопки.

Изменение размера ![ кнопки фронтплате Настройка размера 1](../images/button/MRTK_Button_SizeCustomization1.png)

Обновление размера ![ плоской кнопки Настройка 2](../images/button/MRTK_Button_SizeCustomization2.png)

Обновление размера кнопки "рамка", ![ настройки размера 3](../images/button/MRTK_Button_SizeCustomization3.png)

Нажмите кнопку "исправить границы" ![ Настройка размера 4](../images/button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it&quot;></a>Голосовая команда (&quot;см.,&quot;, ")"

**Обработчик речевого ввода** [Взаимодействующий](interactable.md) скрипт в нажатой кнопке уже реализует `IMixedRealitySpeechHandler` . Здесь можно задать ключевое слово Voice Command.

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

**Профиль ввода речи** Кроме того, необходимо зарегистрировать ключевое слово голосовой команды в *профиле глобальных речевых команд*.

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

**См. раздел-IT, метка** Нажатая кнопка prefab имеет заполнитель Текстмеш Pro Label в объекте *сиитсайитлабел* . Эту метку можно использовать для передачи ключевому слову команды Voice для кнопки пользователю.

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a>Как сделать кнопку с нуля

Примеры этих кнопок можно найти в сцене **прессаблебуттонексампле** .

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1. Создание нажатой кнопки с кубом (только для взаимодействия)

1. Создание куба Unity (GameObject > трехмерный объект > Кубу)
2. Добавить `PressableButton.cs` Скрипт
3. Добавить `NearInteractionTouchable.cs` Скрипт

На `PressableButton` панели инспектора укажите объект куба для **визуальных элементов кнопки перемещения**.

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

При выборе Куба в объекте отображается несколько цветных слоев. Это визуализирует значения расстояния в разделе **Параметры**. С помощью дескрипторов можно настроить время запуска (перемещения объекта) и время активации события.

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

При нажатии кнопки будут перемещены и созданы соответствующие события, представленные в `PressableButton.cs` сценарии, такие как таучбегин (), таученд (), буттонпрессед (), буттонрелеасед ().

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a>Устранение неполадок

Если кнопка выполняется двойным щелчком, убедитесь, что свойство **Принудительная отправка на передний план** активна, а плоскость **Начало push-уведомлений** помещается перед **ближайшей сенсорной** плоскостью. **Сенсорная плоскость близкого взаимодействия** обозначается синей плоскостью, помещенной перед началом координат белой стрелки в приведенном ниже GIF-файле:

![Компонент скрипта для нажатой кнопки с выделенным свойством принудительная передача](../images/button/MRTK_Button_Enforce_Push.png)

![Анимированный пример перемещения начала push-уведомления перед близкой плоскостью с сенсорным взаимодействием](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2. Добавление визуальной обратной связи к кнопке "базовый куб"

Стандартный шейдер МРТК предоставляет различные функции, упрощающие Добавление визуальной обратной связи. Создайте материал и выберите шейдер `Mixed Reality Toolkit/Standard` . Также можно использовать или дублировать один из существующих материалов в `/SDK/StandardAssets/Materials/` , использующий стандартный ШЕЙДЕР мртк.

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

Проверьте `Hover Light` и `Proximity Light` в разделе **Параметры Fluent**. Это обеспечивает визуальную обратную связь как с ближайшими, так и с большим указателем (светлое изображение).

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3. Добавление обратной связи для кнопки "базовый куб"

Так как `PressableButton.cs` скрипт предоставляет такие события, как таучбегин (), таученд (), буттонпрессед (), буттонрелеасед (), мы легко можем назначить звуковые отзывы. Просто добавьте Unity `Audio Source` в объект Cube, а затем назначьте аудиоклипы, выбрав аудиосаурце. плайонешот (). В папке можно использовать MRTK_Select_Main и MRTK_Select_Secondary аудиоклипы `/SDK/StandardAssets/Audio/` .

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4. Добавление визуальных состояний и обработку событий дальнего взаимодействия

[Взаимодействие](interactable.md) — это скрипт, который упрощает создание визуального состояния для различных типов входных данных. Он также обрабатывает события дальнего взаимодействия. Добавьте `Interactable.cs` объект куба и перетащите его в **целевое** поле в разделе **Профили**. Затем создайте новую тему с типом **скалеоффсетколорсеме**. В этой теме можно указать цвет объекта для конкретных состояний взаимодействия, например **фокус** и **нажатое**. Кроме того, можно также управлять масштабом и смещением. Установите флажок **замедление** и задайте длительность, чтобы сделать визуальный переход гладким.

![Выбор темы профиля](../images/button/mrtk_button_profiles.gif)

Вы увидите, что объект отвечает на оба (руки или указатель) и почти (руки) взаимодействия.

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a>Примеры настраиваемых кнопок

В [сцене хандинтерактионексампле](../example-scenes/hand-interaction-examples.md)ознакомьтесь с примерами пианино и круглыми кнопками, которые используют `PressableButton` .

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

Каждому ключу пианино `PressableButton` `NearInteractionTouchable` присваивается и назначается сценарий. Важно проверить правильность *локального направления вперед* `NearInteractionTouchable` . Он представлен белой стрелкой в редакторе. Убедитесь, что стрелка направлена далеко от лицевой стороны кнопки:

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a>См. также

* [Интерактивный объект](interactable.md)
* [Визуальные темы](visual-themes.md)
