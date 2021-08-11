---
title: 212. HoloLens (1-го поколения). Ввод — голос
description: выполните приведенное ниже пошаговое руководство по программированию с помощью Unity, Visual Studio и HoloLens, чтобы получить сведения о концепциях голоса.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-unity, academy, руководство, речь, HoloLens, mixed reality, unity, гарнитура смешанной реальности, гарнитура windows Mixed reality, гарнитура виртуальной реальности, Windows 10
ms.openlocfilehash: 75a1d32ae72a07b68fc65c40035109c468adb1080070240827eeb253eb4a03f4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207370"
---
# <a name="hololens-1st-gen-input-212-voice"></a>HoloLens (1-й общий) вход 212: Voice

>[!IMPORTANT]
>учебники по смешанной реальности Academy были разработаны с учетом HoloLens (1-го поколения), Unity 2017 и впечатляющих головных телефонов смешанной реальности.  Поэтому мы считаем, что важно оставить эти руководства для разработчиков, которые ищут рекомендации по разработке для этих устройств. эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2 и могут быть несовместимы с более новыми версиями Unity.  Они будут сохранены для работы на поддерживаемых устройствах. Опубликован [новый цикл руководств](mrlearning-base.md) для HoloLens 2.

[Ввод голоса](../../../design/voice-input.md) дает нам еще один способ взаимодействия с нашими голограммами. Речевые команды работают очень естественным образом. Разработайте свои речевые команды, чтобы они были:

* Natural
* Легко запомнить
* Соответствующий контекст
* Достаточно отличается от других параметров в том же контексте

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

В статье об основных возможностях [101](../../../develop/unity/tutorials/holograms-101.md)мы использовали кэйвордрекогнизер для создания двух простых голосовых команд. В MR input 212 мы подробнее рассмотрим следующие вопросы:

* разработка голосовых команд, оптимизированных для HoloLensного модуля распознавания речи.
* Предоставьте пользователю сведения о том, какие речевые команды доступны.
* Подтвердите, что мы слышали о команде пользователя.
* Сведения о том, что говорят пользователь, с помощью распознавателя диктофона.
* Используйте распознаватель грамматики для прослушивания команд на основе спецификации или грамматики распознавания речи, файла.

В этом курсе мы перейдем к обозревателю моделей, который мы создали в [MR input 210](holograms-210.md) и [MR input 211](holograms-211.md).

>[!IMPORTANT]
>видеоматериалы, внедренные в каждую из приведенных ниже глав, были записаны с использованием более старой версии Unity и набор средств смешанной реальности. Хотя пошаговые инструкции являются точными и актуальными, в соответствующих видеоматериалах могут отображаться сценарии и визуальные элементы, которые являются неактуальными. Видеоматериалы по-прежнему включены в постерити, так как эти концепции все еще применимы.


## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td>212. Ввод в смешанной реальности: голосовые команды</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>Предварительные условия

* Windows 10 пк, настроенный с [установленными инструментами](../../../develop/install-the-tools.md).
* Некоторые основные возможности программирования на C#.
* Вы должны были выполнить [Основные сведения о MR 101](../../../develop/unity/tutorials/holograms-101.md).
* Необходимо завершить [Ввод MR 210](holograms-210.md).
* Необходимо завершить [Ввод MR 211](holograms-211.md).
* устройство HoloLens, [настроенное для разработки](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Файлы проекта

* Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) , необходимые для проекта. Требуется Unity 2017,2 или более поздней версии.
* Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он будет [доступен на GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Ошибки и примечания

* параметр "включить Только мой код" должен быть отключен (*снят*) в Visual Studio в разделе сервис->параметры — >отладка для попадания в код точек останова в коде.

## <a name="unity-setup"></a>Установка Unity

### <a name="instructions"></a>Инструкции

1. Запустите Unity.
2. Выберите **Открыть**.
3. перейдите в папку **холографикакадеми-Голограммы-212-Voice** , которая была отменена в архиве.
4. Найдите и выберите **начальную** / папку **обозревателя моделей** .
5. Нажмите кнопку **выбрать папку** .
6. на панели **Project** разверните папку **сцены** .
7. Дважды щелкните **моделексплорер** сцену, чтобы загрузить его в Unity.

### <a name="building"></a>Сборка

1. в Unity выберите **файл > сборка Параметры**.
2. Если « **сцены» или «моделексплорер** » в окне « **Построение**» не отображаются, щелкните **Добавить открытые сцены** , чтобы добавить сцену.
3. если вы специально разрабатываете для HoloLens, задайте для параметра **целевое устройство** значение **HoloLens**. В противном случае оставьте его на **любом устройстве**.
4. Убедитесь, что для **типа сборки** задано значение **D3D** и **пакет SDK** установлен в значение " **Последняя установленная версия** " (это должен быть пакет SDK 16299 или более поздней версии).
5. Щелкните **Построить**.
6. Создайте **новую папку** с именем App.
7. Щелкните папку **приложения** одним щелчком мыши.
8. Нажмите кнопку **выбрать папку** , и Unity начнет создание проекта для Visual Studio.

После завершения Unity появится окно проводника.

1. Откройте папку **приложения** .
2. откройте **решение моделексплорер Visual Studio**.

При развертывании в HoloLens:

1. с помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.
2. Щелкните стрелку раскрывающегося списка рядом с кнопкой локальный компьютер и выберите **Удаленный компьютер**.
3. введите **IP-адрес устройства HoloLens** и задайте для параметра режим проверки подлинности значение **универсальный (незашифрованный протокол)**. Нажмите кнопку **Выбрать**. если вы не знакомы с IP-адресом устройства, найдите **Параметры > сеть & интернет > дополнительные параметры**.
4. В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**. При первом развертывании на устройстве необходимо [связать его с Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).
5. После развертывания приложения закройте **фитбокс** с помощью **жеста выбора**.

При развертывании на иммерсивное головной телефон:

1. с помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x64**.
2. Убедитесь, что для целевого объекта развертывания задано значение **локальный компьютер**.
3. В верхней строке меню щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.
4. После развертывания приложения закройте **фитбокс** , изменив триггер на контроллере движения.

>[!NOTE]
>на панели «Visual Studio ошибки» можно заметить некоторые красные ошибки. Их можно спокойно игнорировать. Переключитесь на панель вывода для просмотра фактического хода построения. Ошибки на панели вывода потребует внесения исправления (чаще всего они вызваны ошибкой в скрипте).

## <a name="chapter-1---awareness"></a>Глава 1 — осведомленность

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Задачи

* Узнайте об отделах **и Ототказах** от дизайна речевых команд.
* Используйте **кэйвордрекогнизер** для добавления речевых команд на основе взгляда.
* Предоставление пользователям сведений о голосовых командах с помощью **обратной связи** курсора.

### <a name="voice-command-design"></a>Проектирование команд Voice

В этой главе вы узнаете о проектировании речевых команд. При создании команд Voice:

#### <a name="do"></a>DO

* Создание кратких команд. Вы не хотите использовать *"Воспроизвести текущее выбранное видео"*, так как эта команда не является краткой и будет легко забыта пользователем. Вместо этого следует использовать: *"воспроизвести видео"*, так как он является кратким и имеет несколько слогов.
* Используйте простой словарь. Всегда старайтесь использовать обычные слова и фразы, которые пользователю легко обнаружить и запомнить. Например, если в приложении имеется объект Note, который можно было бы отобразить или скрыть в представлении, команда *«Показать* веб-публикацию» не будет использована, так как ««» является редко используемым термином. Вместо этого для отображения примечания в приложении следует использовать команду *"Показать Примечание"*.
* Соблюдать единообразие. Речевые команды должны поддерживать согласованность в приложении. Imagine, что в приложении есть два сцены, и оба сцены содержат кнопку для закрытия приложения. Если первая сцена использовала команду *"Exit"* для активации кнопки, но Вторая сцена использовала команду *"закрыть приложение"*, то пользователь будет очень путать. Если одна и та же функциональность сохраняется в нескольких сценах, то для ее активации следует использовать одну и ту же голосовую команду.

#### <a name="dont"></a>Не надо

* Используйте отдельные команды для слогов. Например, если вы создавали голосовую команду для воспроизведения видео, следует избегать использования простой команды *«Play»*, так как это лишь один слог, и его легко пропустить в системе. Вместо этого следует использовать: *"воспроизвести видео"*, так как он является кратким и имеет несколько слогов.
* Используйте системные команды. Команда *"Select"* зарезервирована системой для активации события TAP для текущего объекта, на который он нацелен. Не используйте повторно команду *"Select"* в ключевом слове или фразе, так как она может не работать должным образом. Например, если для выбора куба в приложении выбрано голосовое меню *"выбрать куб"*, но пользователь просматривает сферу при распространеннаяе команды, то вместо этого будет выбрана сфера. Аналогично, для команд на панели приложений включена поддержка голоса. Не используйте следующие голосовые команды в представлении CoreWindow:
    1. Назад
    2. Средство прокрутки
    3. Инструмент масштабирования
    4. Инструмент перетаскивания
    5. Adjust
    6. Удалить
* Используйте похожие звуки. Старайтесь не использовать речевые команды, рхиме. Если у вас есть приложение для покупок, которое поддерживало *"показывать магазин"* и *"показывать больше"* в качестве голосовых команд, необходимо отключить одну из команд во время использования другой. Например, можно использовать кнопку *"Показать магазин"* , чтобы открыть магазин, а затем отключить эту команду при отображении хранилища, чтобы команда *"Показать больше"* могла использоваться для просмотра.

### <a name="instructions"></a>Инструкции

* На панели **Иерархия** Unity используйте средство поиска для поиска объекта **holoComm_screen_mesh** .
* Дважды щелкните объект **holoComm_screen_mesh** , чтобы просмотреть его в **сцене**. Это контрольное значение-космонавтам, которое будет отвечать на команды Voice.
* На панели **инспектора** выберите компонент **источник речевого ввода (скрипт)** .
* Разверните раздел **Ключевые слова** , чтобы просмотреть поддерживаемую голосовую команду: **Open Communicator**.
* Щелкните шестеренки справа, а затем выберите **изменить скрипт**.
* Изучите **спичинпутсаурце. CS** , чтобы понять, как она использует **кэйвордрекогнизер** для добавления речевых команд.

### <a name="build-and-deploy"></a>Построение и Развертывание

* в Unity используйте **Параметры сборки файлов >** для перестроения приложения.
* Откройте папку **приложения** .
* откройте **решение моделексплорер Visual Studio**.

(если вы уже создали или развернули этот проект в Visual Studio во время настройки, то можете открыть этот экземпляр VS и нажать кнопку "перезагрузить все" при появлении соответствующего запроса).

* в Visual Studio выберите **отладка-> запуск без отладки** или нажмите клавиши **Ctrl + F5**.
* после того как приложение будет развернуто на HoloLens, закройте поле вписать с помощью жеста [касания](../../../design/gaze-and-commit.md#composite-gestures) .
* Взгляните на контрольное значение-космонавтам.
* Если контрольное значение находится в фокусе, убедитесь, что курсор меняется на микрофон. Это дает отзыв о том, что приложение прослушивает голосовые команды.
* Убедитесь, что в контрольном списке отображается подсказка. это помогает пользователям обнаружить команду *"открыть Communicator"* .
* пока облаками в контрольном списке, скажите *"открыть Communicator"* , чтобы открыть панель Communicator.

## <a name="chapter-2---acknowledgement"></a>Глава 2. подтверждение

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Задачи

* Запишите сообщение, используя ввод с микрофона.
* Отправьте отзыв пользователю о том, что приложение ожидает передачи голоса.

>[!NOTE]
>Для записи приложения с микрофона необходимо объявить возможность использования **микрофона** . Это делается для тех, у вас уже есть входные данные в MR 212, но не забывайте об этом с учетом собственных проектов.
>
>1. в редакторе Unity перейдите к параметрам проигрывателя, перейдя в раздел "изменение > Project Параметры > player".
>2. щелкните вкладку "универсальная платформа Windows".
>3. в разделе "возможности публикации Параметры >" проверьте возможность использования **микрофона** .

### <a name="instructions"></a>Инструкции

* Убедитесь, что на панели **Иерархия** Unity выбран объект **holoComm_screen_mesh** .
* На панели **инспектора** найдите компонент **-космонавтам Watch (скрипт)** .
* щелкните маленький куб "синий", который установлен в качестве значения свойства **Communicator Prefab** .
* на панели **Project** теперь у **Communicator** prefab должен быть фокус.
* щелкните **Communicator** prefab на панели **Project** , чтобы просмотреть ее компоненты в **инспекторе**.
* Взгляните на компонент **диспетчера микрофонов (script)** . Это позволит нам записывать голоса пользователя.
* обратите внимание, что объект **Communicator** имеет компонент **обработчика речевого ввода (Script)** для реагирования на команду **отправить сообщение** .
* взгляните на компонент **Communicator (скрипт)** и дважды щелкните сценарий, чтобы открыть его в Visual Studio.

Communicator. cs отвечает за установку правильных состояний кнопки на устройстве Communicator. Это позволит нашим пользователям записывать сообщение, воспроизводить его и отправить сообщение в-космонавтам. Он также запускает и останавливает анимированную волновую форму для подтверждения пользователю о том, что речь заключалась.

* в **Communicator. cs** удалите следующие строки (81 и 82) из метода **Start** . Это приведет к включению кнопки "запись" в Communicator.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Построение и Развертывание

* в Visual Studio перестройте приложение и разверните его на устройстве.
* взгляните на контрольное значение-космонавтам и скажите *"открыть Communicator"* , чтобы отобразить Communicator.
* Нажмите кнопку **записи** (микрофон), чтобы начать запись сообщения текстовом для-космонавтам.
* Начните говорить и убедитесь, что анимация Wave воспроизводится на Communicator, что позволяет отправить отзыв пользователю о том, что речь идет о своей речи.
* Нажмите кнопку **остановить** (левый квадрат) и убедитесь, что анимация Wave не выполняется.
* Нажмите кнопку **воспроизведения** (правый треугольник), чтобы воспроизвести записанное сообщение и услышать его на устройстве.
* Нажмите кнопку " **прерывать** " (правый прямоугольник), чтобы прерывать воспроизведение записанного сообщения.
* Скажите *"отправить сообщение"* , чтобы закрыть Communicator и получить ответ "полученное сообщение" от-космонавтам.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Глава 3. Основные сведения и распознаватель диктофона

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Задачи

* Используйте распознаватель диктофона для преобразования речи пользователя в текст.
* Отображение гипотетического и окончательного результатов распознавателя диктовки в Communicator.

В этой главе мы будем использовать распознаватель диктофона для создания сообщения для-космонавтам. При использовании распознавателя диктовки Помните, что:

* Для работы распознавателя диктофона необходимо подключение к WiFi.
* Время ожидания происходит по истечении заданного периода времени. Существует два времени ожидания, которые следует учитывать:
  * Если распознаватель запускается и не слышит звук в течение первых пяти секунд, время ожидания истечет.
  * Если распознаватель предоставил результат, а затем слышит бездействия в течение двадцати секунд, время ожидания истечет.
* В каждый момент времени может выполняться только один тип распознавателя (ключевое слово или Диктовка).

>[!NOTE]
>Для записи приложения с микрофона необходимо объявить возможность использования **микрофона** . Это делается для тех, у вас уже есть входные данные в MR 212, но не забывайте об этом с учетом собственных проектов.
>
>1. в редакторе Unity перейдите к параметрам проигрывателя, перейдя в раздел "изменение > Project Параметры > player".
>2. щелкните вкладку "универсальная платформа Windows".
>3. в разделе "возможности публикации Параметры >" проверьте возможность использования **микрофона** .

### <a name="instructions"></a>Инструкции

Мы планируем изменить **микрофонеманажер. CS** для использования распознавателя диктофона. Вот что мы добавим:

1. При нажатии **кнопки записи** мы начнем **диктатионрекогнизер**.
2. Показывает **гипотезу** об понятии диктатионрекогнизер.
3. Заблокируйте **результаты** того, что диктатионрекогнизер понимает.
4. Проверьте время ожидания от Диктатионрекогнизер.
5. После нажатия **кнопки "прерывать"** или истечения времени ожидания в сеансе MIC следует **Отключить диктатионрекогнизер**.
6. Перезапустите **кэйвордрекогнизер**, который будет прослушивать команду **отправки сообщения** .

Давайте приступим. Выполните все упражнения кода для 3. a в **микрофонеманажер. CS** или скопируйте и вставьте законченный код, приведенный ниже:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>Построение и Развертывание

* перестройте в Visual Studio и разверните на устройстве.
* Отклонить поле вписать с помощью жеста касания.
* Взгляните на контрольное значение-космонавтам и скажите *«Open Communicator»*.
* Нажмите кнопку **запись** (микрофон), чтобы записать сообщение.
* Начните говорить. **Распознаватель диктовки** будет интерпретировать ваш речевой ввод и показывать гипотетическую текст в Communicator.
* Попробуйте сказать *"отправить сообщение"* во время записи сообщения. Обратите внимание, что **распознаватель ключевых слов** не отвечает, так как **распознаватель диктовки** все еще активен.
* Подождите несколько секунд. Следите за тем, как распознаватель диктовки завершает свою гипотезу и показывает окончательный результат.
* Начните говорить, а затем приостановитесь на 20 секунд. Это приведет к превышению времени ожидания **распознавателя диктофона** .
* Обратите внимание, что после превышения времени ожидания **распознаватель ключевых слов** снова включается. Теперь Communicator будет отвечать на команды Voice.
* Скажите *"отправить сообщение"* , чтобы отправить сообщение в-космонавтам.

## <a name="chapter-4---grammar-recognizer"></a>Глава 4-распознаватель грамматики

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Задачи

* Используйте распознаватель грамматики для распознавания речи пользователя в соответствии с уточнением или спецификацией распознавания речи, файлом.

>[!NOTE]
>Для записи приложения с микрофона необходимо объявить возможность использования **микрофона** . Это делается для тех, у вас уже есть входные данные в MR 212, но не забывайте об этом с учетом собственных проектов.
>
>1. в редакторе Unity перейдите к параметрам проигрывателя, перейдя в раздел "изменение > Project Параметры > player".
>2. щелкните вкладку "универсальная платформа Windows".
>3. в разделе "возможности публикации Параметры >" проверьте возможность использования **микрофона** .

### <a name="instructions"></a>Инструкции

1. На панели **Иерархия** найдите **Jetpack_Center** и выберите ее.
2. Найдите сценарий **действия тагалонг** на панели **инспектора** .
3. Щелкните маленький круг справа от **объекта, чтобы добавить тег** в поле.
4. В появившемся окне найдите **сргстулбокс** и выберите его из списка.
5. Взгляните на файл **SRGSColor.xml** в папке **стреамингассетс**
    1. Спецификацию модели SRGS можно найти на веб-сайте W3C [здесь](https://www.w3.org/TR/speech-grammar/).

В нашем файле SRGS есть три типа правил:

* Правило, которое позволяет сказать один цвет из списка из двенадцати цветов.
* Три правила, которые ожидают сочетание правила цвета и одной из трех фигур.
* Корневое правило Колорчусер, которое прослушивает любое сочетание трех правил "цвет + форма". Эти фигуры можно сказать в любом порядке и в любой сумме от одного до трех. Это единственное правило, которое прослушивается, так как оно указано в качестве корневого правила в начале файла в исходном &lt; теге грамматики &gt; .

### <a name="build-and-deploy"></a>Построение и Развертывание

* перестройте приложение в Unity, а затем выполните сборку и развертывание из Visual Studio для работы с приложением на HoloLens.
* Отклонить поле вписать с помощью жеста касания.
* Взгляните на Jetpack-космонавтам и выполните жест касания.
* Начните говорить. **Распознаватель грамматики** будет интерпретировать речь и изменить цвета фигур на основе распознавания. Пример команды: "синий круг, желтый квадрат".
* Выполните еще один жест касания, чтобы закрыть панель элементов.

## <a name="the-end"></a>Конец

Поздравляем! Теперь вы выполнили **Ввод MR 212: Voice**.

* Вы узнаете об отделах речи и запретах на команды Voice.
* Вы узнали, как использовались подсказки, чтобы пользователи могли знать о голосовых командах.
* Вы видели несколько типов отзывов, используемых для подтверждения того, что речь пользователя познакомились.
* Вы знаете, как переключаться между распознавателем ключевых слов и распознавателем диктовки и как эти две функции понимают и обрабатывают ваш речевой ввод.
* Вы узнали, как использовать файл SRGS и распознаватель грамматики для распознавания речи в приложении.