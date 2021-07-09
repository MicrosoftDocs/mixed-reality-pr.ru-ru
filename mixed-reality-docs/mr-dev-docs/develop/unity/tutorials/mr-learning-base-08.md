---
title: Использование функции отслеживания взгляда
description: Из этого курса вы узнаете, как использовать отслеживание глаз в приложениях смешанной реальности в Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, MRTK, Mixed Reality Toolkit, UWP, отслеживание глаз
ms.localizationpriority: high
ms.openlocfilehash: a5b93b9e66ffb1e4e9f60251cdc146f48005ae8b
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2021
ms.locfileid: "110713795"
---
# <a name="8-using-eye-tracking"></a>8. Использование функции отслеживания взгляда

Из этого руководства вы узнаете, как включить функцию отслеживания взгляда для HoloLens 2 и добавить ее в объекты, чтобы активировать действия, когда пользователь смотрит на объекты.

> [!NOTE]
> Если вы также развертываете этот проект в HoloLens (1-е поколение), обратите внимание, что функция отслеживания взгляда поддерживается только в HoloLens 2.

## <a name="objectives"></a>Задачи

* Узнайте, как включить функцию отслеживания взгляда для HoleLens 2
* Узнайте, как с помощью функции отслеживания взгляда активировать действие

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Проверка того, включена ли функция ввода с использованием взгляда

В меню Unity последовательно выберите элементы Mixed Reality (Смешанная реальность) > Toolkit (Набор средств) > Utilities (Служебные программы) > **Configure Project for MRTK** (Настроить проект для MRTK), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Затем перейдите в раздел **UWP Capabilities** (Возможности UWP) и убедитесь, что раздел **Enable Eye Gaze Input Capability** (Включить ввод с использованием взгляда) выделен серым цветом.

![Окно конфигурации проекта MRTK в Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> Функция ввода с использованием взгляда должна была быть включена в ходе выполнения инструкций, приведенных в разделе [Применение параметров конфигуратора проекта MRTK](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk), при настройке проекта Unity в начале работы с этой серией руководств. Если функция отключена, включите ее сейчас.

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Включение отслеживания взгляда в поставщике данных о направлении взгляда

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, затем в окне Inspector (Инспектор) перейдите на вкладку MixedRealityToolkit > **Input** (Ввод) и выполните следующие действия:

* Клонируйте профиль **DefaultHoloLens2InputSystemProfile** и присвойте ему понятное имя, например _GettingStarted_HoloLens2InputSystemProfile_.
* Разверните раздел **Pointers** (Указатели).
* Клонируйте профиль **DefaultMixedRealityPointerProfile** и присвойте ему понятное имя, например _GettingStarted_MixedRealityPointerProfile_.
* В разделе **Gaze Settings** (Параметры взгляда) установите флажок **Is Eye Tracking Enabled** (Включено отслеживание взгляда).

![Компонент MixedRealityToolkit в Unity с примененными созданными профилями и включенным отслеживанием глаз](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> Сведения о том, как правильно клонировать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>Включение имитации отслеживания взгляда для редактора Unity

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, в окне инспектора откройте вкладку **Input** (Ввод) и сделайте следующее:

* Разверните раздел **Input Data Providers**  > **Input Simulation Service** (Поставщики входных данных > Служба имитации ввода).
* Клонируйте профиль **DefaultMixedRealityInputSimulationProfile** и присвойте ему понятное имя, например _GettingStarted_MixedRealityInputSimulationProfile_.
* Найдите раздел **Eye Gaze Simulation** (Имитация направления взгляда) и задайте для параметра **Default Eye Gaze Simulation Mode** (Режим имитации направления взгляда по умолчанию) значение **Camera Forward Axis** (Ось камеры, направленная вперед).

![Unity с выбранным объектом TextMeshPro](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>Добавление функции отслеживания взгляда в объекты

В окне Hierarchy (Иерархия) разверните **RoverExplorer** > **Buttons (Кнопки)** и выберите все три дочерних объекта кнопки:

![Unity с выбранным объектом Button](images/mr-learning-base/base-08-section4-step1-1.png)

Выбрав три объекта Button, в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **EyeTrackingTarget** ко всем выбранным объектам:

![Unity с выбранным объектом TextMeshPro и добавленными компонентами](images/mr-learning-base/base-08-section4-step1-2.png)

В окне Hierarchy (Иерархия) разверните **RoverExplorer** > **Buttons (Кнопки)**  > **Hints (Подсказки)**  > **SeeItSayItLabel** > **TextMeshPro**.

Затем в окне Hierarchy (Иерархия) выберите объект кнопки **Hints** (Советы) и настройте компонент **EyeTrackingTarget** следующим образом:

* В разделе события **On Look At Start ()** (При взгляде на начало ())
  * Щелкните небольшой значок **+** , чтобы добавить событие.
  * Назначьте объект **TextMeshPro** от кнопки **Hints** (Советы) полю **None (Object)** (Нет (объект)).
  * В раскрывающемся списке **No Function** (Нет функции) выберите **TextMeshPro** > **float fontSize**, чтобы обновлять это значение свойства при срабатывании события.
  * Задайте для аргумента значение **0,06**, чтобы увеличить текущий размер шрифта 0,04 на 50 %.
* В разделе события **On Look At Start ()** (При отведении взгляда ())
  * Щелкните небольшой значок **+** , чтобы добавить событие.
  * Назначьте объект **TextMeshPro** от кнопки **Hints** (Советы) полю **None (Object)** (Нет (объект)).
  * В раскрывающемся списке **No Function** (Нет функции) выберите **TextMeshPro** > **float fontSize**, чтобы обновлять это значение свойства при срабатывании события.
  * Задайте для аргумента значение **0,04**, чтобы сбросить размер шрифта обратно до значения 0,04.

![Unity с выбранным объектом TextMeshPro для Hints и настроенным компонентом EyeTrackingTarget](images/mr-learning-base/base-08-section4-step1-3.png)

**Повторите** этот шаг для объекта кнопки **Explode** (Развернуть) и **Reset** (Сбросить), чтобы настроить отслеживание взгляда для оставшихся кнопок.

Если теперь перейти в режим игры, а затем нажать и удерживать правую кнопку мыши при перемещении указателя мыши до тех пор, пока взгляд не достигнет одной из кнопок, вы увидите, что размер шрифта увеличится на 50 %. При отведении взгляда текст вернется к исходному размеру:

![Разделенное представление Unity в режиме воспроизведения с взглядом, направленным на метку кнопки Explode с отслеживанием взгляда](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>Поздравляем!

Из этого руководства вы узнали, как включить функцию отслеживания взгляда для HoloLens 2 и добавить ее в объекты, чтобы активировать действия, когда пользователь смотрит на объекты.

> [!div class="nextstepaction"]
> [Следующее руководство: 9. Использование речевых команд](mr-learning-base-09.md)
