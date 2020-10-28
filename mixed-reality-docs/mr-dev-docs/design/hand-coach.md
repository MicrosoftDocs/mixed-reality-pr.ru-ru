---
title: Обучающая рука
description: Трехмерные руки, активируемые, когда система не обнаруживает руки пользователя, которые помогут им помочь.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, проектирование, рука, увлекательная гарнитура, МРТК, руки, помощь
ms.openlocfilehash: 10e5f3b025e4346d7c4075c2de7252c9ab217c93
ms.sourcegitcommit: 24d96bf3bb9a3143445e018195edae99d91684c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92683250"
---
# <a name="hand-coach"></a>Обучающая рука
![Пример: рука](images/HandCoach/MRTK_handCoach.jpg)<br>

Руки — это трехмерные модели, которые запускаются, когда система не обнаруживает руки пользователя. Это реализовано как компонент обучения, который помогает пользователю, когда жест не научился. Если пользователь не выполнил указанный жест в течение периода, руки будут циклически заканчиваться с задержкой. Для представления нажатия кнопки или выбора голограммы можно использовать руку.  

## <a name="hand-coach-provided"></a>Предоставленная консультационная рука

Текущая модель взаимодействия представляет широкий спектр элементов управления жестами, таких как прокрутка, дальнее выделение и близко к касанию. Ниже приведен полный список существующих жестов руки, представленных в<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> мртк</a>.

:::row:::
    :::column:::
       ![Пример приближения к SELECT](images/HandCoach/NearSelect.gif)<br>
       **Пример вблизи Select — показывает, как выбрать кнопки или закрыть взаимодействующие объекты**<br>
    :::column-end:::
    :::column:::
       ![Пример воздушного касания](images/HandCoach/AirTap.gif)<br>
        **Пример Air TAP — используется для демонстрации выбора объектов, которые находятся далеко**<br>
    :::column-end:::
    :::column:::
       ![Пример перемещения](images/HandCoach/Move.gif)<br>
       **Пример перемещения объекта в пространстве — используется для демонстрации перемещения голограммы в пространстве**<br>
    :::column-end:::
    :::column:::
       ![Пример поворота](images/HandCoach/Rotate.gif)<br>
       **Пример Rotate-Used, демонстрирующий поворот голограмм или объектов**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Пример масштабирования](images/HandCoach/Scale.gif)<br>
       **Пример масштабирования — используется для демонстрации того, как можно управлять голограммами, чтобы они были больше или меньше**<br>
    :::column-end:::
    :::column:::
       ![Пример Palm up](images/HandCoach/PalmUp.gif)<br>
        **Пример использования Palm — предлагаемое использование для открытия меню "руки"**<br>
    :::column-end:::
    :::column:::
       ![Пример Хандфлип](images/HandCoach/HandFlip.gif)<br>
       **Примере с перелистыванием вручную — другой способ открыть меню "руки"**<br>
    :::column-end:::
    :::column:::
       ![Пример прокрутки](images/HandCoach/Scoll.gif)<br>
       **Пример прокрутки — используется для прокрутки списка или длинного документа**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>Принципы проектирования

Для Hololens2 мы разработали взаимодействия, основанные на инстинктуал и естественных жестах руки. Мы считаем, что они интуитивно понятны большинству пользователей, и, таким способом, не создают выделенные данные для обучения жестов. Вместо этого мы создали свою помощь, чтобы помочь пользователям, которые могут задержаться или не знакомы с голограммами, узнать об этих жестах. Без обучения мы продемонстрировали, что пользователи покажут, как выполнить действие, выполнив демонстрацию, что это лучший вариант. Во всех наших исследованиях было обнаружено, что пользователи смогли понять жест, но требовалось небольшое руководство. Если бы мы определили, что пользователь не взаимодействует с объектом в течение периода, будет запущено обучение руки, которое демонстрирует правильное размещение и положение пальца. 

### <a name="intuitive"></a>Точки

При анимации рук это должно быть очевидным и не должно вызывать путаницы. Анимация руки — это представление жеста, который вы пытаетесь вызвать пользователю, чтобы понять его назначение. 

Например, если вы хотите, чтобы пользователь нажмет кнопку, будет активирована рука, нажатие кнопки.

![Пример: близкое касание](images/HandCoach/NearSelect_unity.gif)<br>
*Практические примеры, демонстрирующие касание драгоценного камень*  

### <a name="hand-scale"></a>Масштаб вручную

Мы протестировали различные размеры с помощью меню пользовательского интерфейса и заказалось, что если бы у руки было истинное изменение размера, это менаЦинго, но если бы они оказались слишком маленькими, то трудно увидеть и понять жест. 

**Голоса и руки**

Не ожидается, что пользователи могут прослушивать один набор инструкций с помощью голоса, а также просматривать различные инструкции с помощью руки. Поочередно изменяйте свои инструкции, чтобы помочь пользователям сосредоточиться на снижении перегрузки датчиков.


## <a name="can-i-create-my-own"></a>Можно ли создать собственную?

Да. Мы рекомендуем вам создать собственный уникальный жест для игры и участвовать в сообществе!
Мы предоставили Maya-файл с определенной нагрузкой, который можно использовать для приложения, который можно скачать здесь: <a href="files/HandCoach_MRTK.zip"> скачать HandCoach_MRTK.zip </a>

![Пример анимированных рук в Maya](images/HandCoach/MayaSelect_Gif.gif)<br>
*Пример анимационной руки, знакомство Box в Maya*


**Рекомендуемое средство разработки**

Многие из трехмерных исполнителей используют [Maya Autodesk, который может использовать HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) для преобразования способа создания ресурсов. Файл руки — это двоичный файл Maya, поэтому рекомендуется использовать Maya для анимации и экспорта стрелок. Если вы предпочитаете использовать другую трехмерную программу, см <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> Скачайте HandCoachMRTK_FBX.zip </a> , чтобы создать собственную установку контроллера. 

Если вы используете доступный для загрузки файл руки Maya, рекомендуется масштабировать руки в Unity до 0,6.

![Пример: высокоMayaная платформа для подготовки к сдаче](images/HandCoach/MayaExample.png)<br>
*Руки с Спецоснастка*

### <a name="technical-specs"></a>Технические спецификации

*   Два переданного файла доступны в формате ASCII Maya
*    Правая и левая рука доступны в двоичном формате Maya
*   Задайте для файла Maya значение 24 кадров/с
*   В файле имеется левая и правая рука, которые можно использовать для двух перенаправленных или однопользовательских жестов. Правая рука отображается по умолчанию.
*   Рекомендуется оставить буфер около 10 кадров в начале и в конце для появления.
*   При анимации объекта с указанным целевым объектом рекомендуется анимировать его в поле по умолчанию или значение null.
*   Если рука выполняет анимацию физического объекта, такого как Box, рекомендуется не анимировать перевод в Maya, но дожидаться анимации в Unity или в коде.
*   Видимая анимация должна составлять 1,5 с для получения значимой информации
*   Когда вы довольны анимацией:
    *   Выбор всех соединений и внедрить ключевых кадров
    *   Удаление контроллеров, выбор соединений и сетки и экспорт в качестве FBX
    *  При наличии нескольких анимаций можно использовать встроенную средство экспорта игр Maya: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Экспорт из Maya

Когда вы удовлетворены анимацией
* Выбрать все соединения: выбрать иерархию >

     ![Пример: иерархия в меню](images/HandCoach/Hierarchy.png)<br>
* Внедрить анимации: переключение на анимацию > ключ > анимация внедрить

     ![Пример: внедрить анимации меню "расположение"](images/HandCoach/BakeAnimation.png)<br>
* Удалить платформу контроллера: > MainR_Grp или MainL_Grp

     ![Пример: расположение меню для платформы контроллера](images/HandCoach/ControllerRig.png)<br>

* Экспортировать как FBX: выберите JNT + сеток: файл > экспорт выбор (флажок) > выбор экспорта

     ![Пример. Экспорт расположения меню выбора](images/HandCoach/OptionBox.png)<br>

     ![Пример: расположение меню](images/HandCoach/SelectionExport.png)<br>

     ![Пример. расположение меню "Параметры экспорта"](images/HandCoach/FBXSelection.png)<br>


 При экспорте в FBX и внесении в Unity масштабирование осуществляется до 0,6. Мы обнаружили, что это был идеальный баланс для отображения рук. 

![Пример: параметры Unity](images/HandCoach/HandHintScale.png)<br>
*Параметры Unity для HandCoach_R prefab найдены в МРТК*


## <a name="implementing-hands-into-your-unity-project"></a>Реализация руки в проекте Unity

### <a name="best-practices"></a>Рекомендации
*    Рекомендуется масштабировать руки в Unity до 0,6
*   Руки следует воспроизводить дважды, в противном случае — до завершения жеста. Для того чтобы пользователь имел время для регистрации и просмотра жеста, необходимо дважды выполнить цикл. Стрелки должны появления и исчезновения между циклами. 
 *  Если руки пользователя видны с помощью камер HL2, но пользователи не выполняют необходимое взаимодействие, они будут отображаться через 10 секунд.
*   Если руки пользователя не видны в HL2 камерах, они будут отображаться через 5 секунд.  
*   Если руки пользователя заметно отправляются с помощью HL2 камер в середине анимации, анимация будет завершена и исчезать.
*   Если вы включаете речь, мы рекомендуем, чтобы он соответствовал жесту руки.
*   Если вы научились по крайней мере один раз, повторяйте жест только в том случае, если обнаружено, что пользователь зависает.
*   Если конкретные положения пальца и руки являются критически важными, пользователи могут четко видеть эти особенности анимации. Попробуйте англинг в руки, чтобы наиболее важные части были четко видны. 
* Если вы заметили искажения в руки, вам нужно переходить к параметрам качества Unity увеличить количество костей. 
 Перейдите к параметру Изменить > проекта Unity > качество > другие > веса Blend. Убедитесь, что выбрано "четыре кости" для просмотра гладких соединений. 

   ![Пример: окно "Параметры проекта"](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a>Чего следует избегать
* Масштабирование слишком больших стрелок
* поместив слишком близкое окно к пользователю
* Руки следует научиться только один раз. Чрезмерное обучение может привести к путанице и неправильной работе
*   Приведя его к Unity, скачайте последнюю версию МРТК здесь: https://github.com/microsoft/MixedRealityToolkit-Unity
    *   Материал: Teaching_Hand2
    *   Сценарии. см. рекомендации по МРТК для <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md"> мртк </a>
    *   Параметр для каждого проекта
        *   Для сцены задано значение UWP: инструкции см. в [проекте настройки Unity](../develop/unity/Configure-Unity-Project.md) для Windows Mixed Reality.

## <a name="see-also"></a>См. также статью
* [Принципы взаимодействия](interaction-fundamentals.md)
* [Процесс создания ресурсов](asset-creation-process.md)
* [Жесты](../gestures.md)
* [Установка инструментов](../develop/install-the-tools.md)
* [Настройка проекта Unity](../develop/unity/Configure-Unity-Project.md)
* [Обзор разработки в Unity](../develop/unity/unity-development-overview.md)
* [МРТК 101](../develop/unity/mrtk-101.md)