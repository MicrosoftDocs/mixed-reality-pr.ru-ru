---
title: Моделирование восприятия
description: Рекомендации по использованию библиотеки моделирования восприятия для автоматизации имитации входных данных для впечатляющих приложений
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, моделирование, тестирование
ms.openlocfilehash: d80ecbd4c8120c94959a56f4c7368f03cfe2cef1
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130158489"
---
# <a name="perception-simulation"></a>Моделирование восприятия

Вы хотите создать автоматический тест для приложения? Вы хотите, чтобы тесты переходили за пределы модульного тестирования на уровне компонентов и действительно протестировали свое приложение как можно более полное? Имитация восприятия — это то, что вы ищете. Библиотека моделирования восприятия отправляет в приложение пользовательские и мировые входные данные, что позволяет автоматизировать тесты. Например, можно имитировать входные данные человека, который смотрит в конкретную, повторяемую, а затем использовать жест или контроллер движения.

имитация восприятия может отправить смоделированные входные данные на физический HoloLens, эмулятор HoloLens (первый), HoloLens 2 Emulator или компьютер с установленным порталом смешанной реальности. Имитация восприятия обходит активные датчики на устройстве смешанной реальности и отправляет смоделированные входные данные приложениям, работающим на устройстве. Приложения получают эти события ввода с помощью тех же API-интерфейсов, которые они всегда используют, и не могут сообщать о различиях между запуском с реальными датчиками и имитацией имитация восприятия — это та же технология, которая используется эмуляторами HoloLens для отправки смоделированных входных данных на HoloLensную виртуальную машину.

Чтобы приступить к использованию моделирования в коде, начните с создания объекта Иперцептионсимулатионманажер. Из этого объекта можно выдавать команды для управления свойствами имитации "человека", включая позиционирование головной части, расположение руки и жесты. Можно также включить и управлять контроллерами движения.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>настройка Project Visual Studio для имитации восприятия
1. [установите эмулятор HoloLens](../install-the-tools.md) на компьютере разработчика. Эмулятор включает библиотеки, используемые для имитации восприятия.
2. создание нового Visual Studio классического проекта C# (Project консоли прекрасно работает для начала работы).
3. добавьте в проект следующие двоичные файлы в качестве ссылок (ссылка на Project >add->...). их можно найти в% programfiles (x86)% \ microsoft XDE \\ (версия), например **% programfiles (x86)% \ microsoft XDE \\ 10.0.18362.0** для HoloLens 2 Emulator.  (примечание. несмотря на то, что двоичные файлы являются частью HoloLens 2 Emulator, они также работают для Windows Mixed Reality на рабочем столе.) конкретного. Управляемая PerceptionSimulationManager.Interop.dll оболочка C# для имитации восприятия.
    b. PerceptionSimulationRest.dll-Library для настройки канала связи веб-сокета с HoloLens или эмулятором.
    c. SimulationStream.Interop.dll — общие типы для моделирования.
4. Добавьте в проект a двоичный PerceptionSimulationManager.dll реализации. сначала добавьте его в качестве двоичного файла в проект (Project >add->существующий элемент...). Сохраните его как ссылку, чтобы он не скопировал его в исходную папку проекта. ![Добавьте PerceptionSimulationManager.dll в проект как ссылку ](images/saveaslink.png) b. Затем убедитесь, что он скопирован в выходную папку при сборке. Он находится на странице свойств двоичного файла. ![Пометьте PerceptionSimulationManager.dll для копирования в выходной каталог](images/copyalways.png)
5. Задайте для активной платформы решения x64.  (Используйте Configuration Manager, чтобы создать запись платформы для x64, если она еще не создана.)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Создание объекта Иперцептионсимулатион Manager

Для управления имитацией вы получаете обновления объектов, полученных из объекта Иперцептионсимулатионманажер. Первым шагом является получение этого объекта и его подключение к целевому устройству или эмулятору. Вы можете получить IP-адрес эмулятора, нажав кнопку на портале устройства на [панели инструментов](using-the-hololens-emulator.md) .

![значок "открыть портал устройств" ](images/emulator-deviceportal.png) **откройте портал** устройств: откройте портал Windows устройств для HoloLens ос в эмуляторе.  для Windows Mixed Reality это можно получить в приложении Параметры в разделе "обновление & безопасности", а затем "для разработчиков" в разделе "Подключение using:" раздела "включение портала устройств".  Обязательно запишите IP-адрес и порт.

Во-первых, вы вызываете Рестсимулатионстреамсинк. Create для получения объекта Рестсимулатионстреамсинк. Это целевое устройство или эмулятор, которым вы управляете HTTP-соединением. команды будут переданы и обработаны на [портале устройств Windows](using-the-windows-device-portal.md) , работающем на устройстве или эмуляторе. Ниже приведены четыре параметра, которые необходимо создать для объекта.
* URI URI — IP-адрес целевого устройства (например, " https://123.123.123.123 " или " https://123.123.123.123:50080 ").
* System .net. NetworkCredential credentials — имя пользователя и пароль для подключения к [порталу устройств Windows](using-the-windows-device-portal.md) на целевом устройстве или эмуляторе. Если вы подключаетесь к эмулятору через свой локальный адрес (например, 168.*.*. *) на том же компьютере будут приниматься любые учетные данные.
* bool обычная — true для обычного приоритета, false для низкого приоритета. Обычно необходимо задать для этого параметра значение *true* для тестовых сценариев, что позволяет вашему тесту осуществлять управление.  эмулятор и эмуляция Windows Mixed Reality используют соединения с низким приоритетом.  Если в тесте также используется подключение с низким приоритетом, то последнее установленное соединение будет управляться.
* Для отмены асинхронной операции маркера токена System. Threading. CancellationToken.

Во вторых, вы создадите Иперцептионсимулатионманажер. Это объект, используемый для управления имитацией. Это также необходимо сделать в асинхронном методе.

## <a name="control-the-simulated-human"></a>Управление имитируемым человеком

Иперцептионсимулатионманажер имеет свойство человеческого, которое возвращает объект Исимулатедхуман. Для управления имитируемым человеком выполните операции с этим объектом. Вот несколько примеров.

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Простой пример консольного приложения C#

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>Расширенный пример консольного приложения C#

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>Примечание о 6-ДОФ контроллерах

Перед вызовом каких-либо свойств для методов смоделированного 6-ДОФ контроллера необходимо активировать контроллер.  Это приведет к исключению.  начиная с обновление Windows 10 за май 2019 г. можно установить и активировать смоделированные 6-доф контроллеры, задав для свойства Status объекта исимулатедсиксдофконтроллер значение симулатедсиксдофконтроллерстатус. Active.
в обновление Windows 10 за октябрь 2018 г. и более ранних версиях необходимо отдельно установить смоделированный 6-доф контроллер, вызвав средство перцептионсимулатиондевице, расположенное в папке \ Windows выполнять.  Использование этого средства выглядит следующим образом:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Например.

```
    PerceptionSimulationDevice.exe i 6dof 1
```

Поддерживаются следующие действия:
* i = установить
* q = запрос
* r = удалить

Поддерживаются следующие экземпляры:
* 1 = левый 6-ДОФ контроллер
* 2 = правильный 6-ДОФ контроллер

Код выхода процесса будет указывать на успех (нулевое возвращаемое значение) или ошибку (ненулевое возвращаемое значение).  При использовании действия "q" для запроса того, установлен ли контроллер, возвращаемое значение будет равно нулю (0), если контроллер еще не установлен, или один (1), если контроллер установлен.

при удалении контроллера обновление Windows 10 за октябрь 2018 г. или более ранней версии установите его состояние в Off через API, а затем вызовите средство перцептионсимулатиондевице.

Это средство необходимо запускать от имени администратора.




## <a name="api-reference"></a>Справочник по API

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft. Перцептионсимулатион. Симулатеддевицетипе

Описывает тип имитации устройства

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft. Перцептионсимулатион. Симулатеддевицетипе. Reference**

Фиктивное эталонное устройство, используемое по умолчанию для Перцептионсимулатионманажер

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft. Перцептионсимулатион. Хеадтраккермоде

Описывает режим «головной транспортер»

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft. Перцептионсимулатион. Хеадтраккермоде. Default**

Отслеживание головок по умолчанию. Это означает, что система может выбрать оптимальный режим отслеживания головной системы на основе условий среды выполнения.

**Microsoft. Перцептионсимулатион. Хеадтраккермоде. Orientation**

Только отслеживание головной страницы. Это означает, что отслеживающее расположение может быть ненадежным, а некоторые функциональные возможности, зависящие от головного расположения, могут быть недоступны.

**Microsoft. Перцептионсимулатион. Хеадтраккермоде. положением**

Отслеживание позиционированных головок. Это означает, что положение и ориентация отслеживающей головки надежны

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft. Перцептионсимулатион. Симулатеджестуре

Описывает имитацию жеста

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**Microsoft. Перцептионсимулатион. Симулатеджестуре. None**

Значение Sentinel, используемое для обозначения отсутствия жестов.

**Microsoft. Перцептионсимулатион. Симулатеджестуре. Финжерпрессед**

Жест нажатия пальца.

**Microsoft. Перцептионсимулатион. Симулатеджестуре. Финжеррелеасед**

Жест отпуска пальца.

**Microsoft. Перцептионсимулатион. Симулатеджестуре. Home**

Жест домашнего или системного.

**Microsoft. Перцептионсимулатион. Симулатеджестуре. Max**

Максимально допустимый жест.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус

Возможные состояния имитации 6-ДОФ контроллера.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Off**

6-ДОФ контроллер отключен.

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Active**

Контроллер ДОФ включается и отключается.

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллерстатус. Траккинглост**

6-ДОФ контроллер включен, но не может быть записан.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон

Поддерживаемые кнопки на имитации 6-ДОФ контроллера.

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. None**

Значение Sentinel, используемое для отсутствия кнопок.

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Home**

Нажата кнопка Главная.

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Menu**

Нажата кнопка меню.

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. захват**

Нажата кнопка захвата.

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Таучпадпресс**

Сенсорная панель нажата.

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Select**

Нажата кнопка выбрать.

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Таучпадтауч**

Сенсорная панель затронута.

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. аналоговый стик**

Аналоговый стик нажат.

**Microsoft. Перцептионсимулатион. Симулатедсиксдофконтроллербуттон. Max**

Максимальная допустимая кнопка.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате

Состояние калибровки имитации глаз

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. недоступно**

Калибровка глаз недоступна.

**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. ready**

Эти глаза были откалиброваны.  Это значение по умолчанию.

**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. Настройка**

Эти глаза откалиброваны.

**Microsoft. Перцептионсимулатион. Симулатедэйескалибратионстате. Усеркалибратионнидед**

Необходимо откалибровать глаза.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци

Точность отслеживания соединения руки.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. недоступно**

Соединение не было отслеживанием.

**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. приблизительный**

Совместное размещение выводится.

**Microsoft. Перцептионсимулатион. Симулатедханджоинттраккингаккураци. Visible**

Совместное соединение полностью отслеживание.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft. Перцептионсимулатион. Симулатедхандпосе

Точность отслеживания соединения руки.

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Closed**

Соединения пальца руки настраиваются для отражения закрытого объекта.

**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Open**

Соединения пальца руки настраиваются для отражения открытой части.

**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Point**

Соединения пальца руки настраиваются в соответствии с указывающим на себя.

**Microsoft. Перцептионсимулатион. Симулатедхандпосе. сжатие**

Соединения пальца руки настраиваются в соответствии с набором сжатия.

**Microsoft. Перцептионсимулатион. Симулатедхандпосе. Max**

Максимальное допустимое значение для Симулатедхандпосе.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft. Перцептионсимулатион. Плайбаккстате

Описывает состояние воспроизведения.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft. Перцептионсимулатион. Плайбаккстате. Stopped**

Запись сейчас остановлена и готова к воспроизведению.

**Microsoft. Перцептионсимулатион. Плайбаккстате. Play**

Сейчас запись воспроизводится.

**Microsoft. Перцептионсимулатион. Плайбаккстате. приостановлено**

Запись в данный момент приостановлена.

**Microsoft. Перцептионсимулатион. Плайбаккстате. end**

Запись достигла конца.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft. Перцептионсимулатион. Vector3

Описывает вектор с тремя компонентами, который может описывать точку или вектор в трехмерном пространстве.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft. Перцептионсимулатион. Vector3. X**

Координата X вектора.

**Microsoft. Перцептионсимулатион. Vector3. Y**

Координата Y вектора.

**Microsoft. Перцептионсимулатион. Vector3. Z**

Координата Z вектора.

**Microsoft. Перцептионсимулатион. Vector3. #ctor (System. Single, System. Single, System. Single)**

Создайте новый Vector3.

Параметры
* x — компонент x вектора.
* y — компонент y вектора.
* z — компонент z вектора.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft. Перцептионсимулатион. Rotation3

Описывает поворот трех компонентов.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft. Перцептионсимулатион. Rotation3. шаг**

Компонент шаг поворота вокруг оси X.

**Microsoft. Перцептионсимулатион. Rotation3. значения нутации**

Компонент значения нутации вращения, который находится справа вокруг оси Y.

**Microsoft. Перцептионсимулатион. Rotation3. рулон**

Компонент рулона поворота, который находится справа вокруг оси Z.

**Microsoft. Перцептионсимулатион. Rotation3. #ctor (System. Single, System. Single, System. Single)**

Создайте новый Rotation3.

Параметры
* шаг — компонент шага поворота.
* значения нутации — компонент значения нутации вращения.
* рулон — компонент рулона поворота.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион

Описывает конфигурацию соединения с имитацией руки.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. положением**

Расположение соединения.

**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. вращение**

Поворот соединения.

**Microsoft. Перцептионсимулатион. Симулатедханджоинтконфигуратион. Траккингаккураци**

Точность отслеживания соединения.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft. Перцептионсимулатион. Фрустум

Описывает представление фрустум, как обычно используется камерой.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft. Перцептионсимулатион. Фрустум. Near**

Минимальное расстояние, которое содержится в фрустум.

**Microsoft. Перцептионсимулатион. Фрустум. FAR**

Максимальное расстояние, которое содержится в фрустум.

**Microsoft. Перцептионсимулатион. Фрустум. Фиелдофвиев**

Горизонтальное поле представления фрустум в радианах (меньше PI).

**Microsoft. Перцептионсимулатион. Фрустум. Аспектратио**

Отношение горизонтального поля представления к вертикальному полю представления.

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a>Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион

Описывает конфигурацию экрана имитации гарнитуры.

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Лефтэйепоситион**

Преобразование из центра заголовка к левому глазу в целях отрисовки стерео.

**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Лефтэйеротатион**

Поворот левого глаза в целях отрисовки стерео.

**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Ригхтэйепоситион**

Преобразование из центра заголовка к нужному глазу в целях отрисовки стерео.

**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Ригхтэйеротатион**

Поворот правильного глаза в целях отрисовки стерео.

**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. IPD**

Значение IPD, сообщаемое системой в целях отрисовки стерео.

**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Апплеетрансформс**

Должны ли значения, предоставленные для преобразования влево и вправо, считаться допустимыми и примененными к работающей системе.

**Microsoft. Перцептионсимулатион. Симулатеддисплайконфигуратион. Апплипд**

Должно ли значение, указанное для IPD, считаться допустимым и примененным к работающей системе.


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер

Корень для создания пакетов, используемых для управления устройством.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. Device**

Извлеките объект имитации устройства, который интерпретирует имитацию человека и имитации мира.

**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. человеческий**

Извлеките объект, управляющий имитацией человека.

**Microsoft. Перцептионсимулатион. Иперцептионсимулатионманажер. Reset**

Сбрасывает состояние имитации до состояния по умолчанию.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft. Перцептионсимулатион. Исимулатеддевице

Интерфейс, описывающий устройство, которое интерпретирует имитацию мира и имитацию человека

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft. Перцептионсимулатион. Исимулатеддевице. Хеадтраккер**

Извлеките головной датчик из имитации устройства.

**Microsoft. Перцептионсимулатион. Исимулатеддевице. Хандтраккер**

Получите датчик руки от имитации устройства.

**Microsoft. Перцептионсимулатион. Исимулатеддевице. Сетсимулатеддевицетипе (Microsoft. Перцептионсимулатион. SimulatedDeviceType)**

Задайте свойства виртуального устройства в соответствии с указанным типом устройства.

Параметры
* тип — новый тип имитации устройства.

### <a name="microsoftperceptionsimulationisimulateddevice2"></a>Microsoft. Перцептионсимулатион. ISimulatedDevice2

Дополнительные свойства доступны путем приведения Исимулатеддевице к ISimulatedDevice2.

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

**Microsoft. Перцептионсимулатион. ISimulatedDevice2. Исусерпресент**

Получение или задание того, активно ли имитация людьмиа на гарнитуре.

**Microsoft. Перцептионсимулатион. ISimulatedDevice2. Дисплайконфигуратион**

Получение или установка свойств имитации дисплея.

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft. Перцептионсимулатион. Исимулатедхеадтраккер

Интерфейс, описывающий часть имитации устройства, которая отслеживает заголовку имитации человека.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft. Перцептионсимулатион. Исимулатедхеадтраккер. Хеадтраккермоде**

Извлекает и устанавливает текущий режим трассировки головного подразделения.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft. Перцептионсимулатион. Исимулатедхандтраккер

Интерфейс, описывающий часть имитации устройства, которая отслеживает руки имитации человека

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Ворлдпоситион**

Получение расположения узла относительно мира в метрах.

**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. положением**

Извлечение и задание положения объекта Tracker для имитации относительно центра головки.

**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. шаг**

Извлеките и задайте шаг вниз для смоделированного средства записи.

**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Фрустумигноред**

Получите и задайте значение, определяющее, пропускается ли фрустум транспортера для имитации. Если игнорируется, обе руки всегда видимы. Если параметр не пропускается (по умолчанию), руки отображаются только в том случае, если они находятся в фрустуме средства записи.

**Microsoft. Перцептионсимулатион. Исимулатедхандтраккер. Фрустум**

Получите и задайте свойства фрустум, используемые для определения, видны ли руки для имитации средства записи.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft. Перцептионсимулатион. Исимулатедхуман

Интерфейс верхнего уровня для управления имитацией человека.

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }s
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**Microsoft. Перцептионсимулатион. Исимулатедхуман. Ворлдпоситион**

Извлечение и Установка расположения узла относительно мира в метрах. Это расположение соответствует точке в центре метров человека.

**Microsoft. Перцептионсимулатион. Исимулатедхуман. Direction**

Извлеките и задайте направление имитации человеческих лиц в мире. 0 радианы отменяют отрицательную ось Z. Положительные радианы поворачиваются по часовой стрелке относительно оси Y.

**Microsoft. Перцептионсимулатион. Исимулатедхуман. Height**

Получение и задание высоты имитации человека в метрах.

**Microsoft. Перцептионсимулатион. Исимулатедхуман. LeftHand**

Получите левую руку имитации человека.

**Microsoft. Перцептионсимулатион. Исимулатедхуман. Ригхсанд**

Получите правую руку имитации человека.

**Microsoft. Перцептионсимулатион. Исимулатедхуман. Head**

Получите заголовок имитации человека.

**Microsoft. Перцептионсимулатион. Исимулатедхуман. Move (Microsoft. Перцептионсимулатион. Vector3)**

Перемещение имитации человека относительно его текущего положения в метрах.

Параметры
* перевод — перевод, который необходимо переместить, относительно текущего положения.

**Microsoft. Перцептионсимулатион. Исимулатедхуман. вращение (System. Single)**

Поворот имитации человека относительно текущего направления по часовой стрелке по оси Y

Параметры
* радианы — величина поворота вокруг оси Y.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft. Перцептионсимулатион. ISimulatedHuman2

Дополнительные свойства доступны путем приведения Исимулатедхуман к ISimulatedHuman2.

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft. Перцептионсимулатион. ISimulatedHuman2. Лефтконтроллер**

Получите левый 6-ДОФ контроллер.

**Microsoft. Перцептионсимулатион. ISimulatedHuman2. Ригхтконтроллер**

Получите подходящий 6-ДОФ контроллер.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft. Перцептионсимулатион. Исимулатедханд

Интерфейс, описывающий руки имитации человека

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**Microsoft. Перцептионсимулатион. Исимулатедханд. Ворлдпоситион**

Получение расположения узла относительно мира в метрах.

**Microsoft. Перцептионсимулатион. Исимулатедханд. положением**

Получение и установка положения смоделированной руки относительно человека в метрах.

**Microsoft. Перцептионсимулатион. Исимулатедханд. Activated**

Извлечение и задание того, активирована ли рука в настоящий момент.

**Microsoft. Перцептионсимулатион. Исимулатедханд. Visible**

Извлеките, является ли рука в настоящий момент видимой для SimulatedDevice (т. е. находится ли оно в положении, которое должно быть обнаружено Хандтраккер).

**Microsoft. Перцептионсимулатион. Исимулатедханд. Енсуревисибле**

Переместите руку так, чтобы она была видна SimulatedDevice.

**Microsoft. Перцептионсимулатион. Исимулатедханд. Move (Microsoft. Перцептионсимулатион. Vector3)**

Переместить положение моделируемой руки относительно ее текущей должности в метрах.

Параметры
* перевод — величина, на которую переводятся смоделированные руки.

**Microsoft. Перцептионсимулатион. Исимулатедханд. Перформжестуре (Microsoft. Перцептионсимулатион. Симулатеджестуре)**

Выполните жест, используя имитацию руки.  Она будет обнаружена системой только в том случае, если она включена.

Параметры
* жест — жест, который необходимо выполнить.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft. Перцептионсимулатион. ISimulatedHand2

Дополнительные свойства доступны путем приведения Исимулатедханд к ISimulatedHand2.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft. Перцептионсимулатион. ISimulatedHand2. Orientation**

Возвращает или задает поворот моделируемой руки.  Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft. Перцептионсимулатион. ISimulatedHand3

Дополнительные свойства доступны путем приведения Исимулатедханд к ISimulatedHand3.
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft. Перцептионсимулатион. ISimulatedHand3. Жетжоинтконфигуратион**

Получение конфигурации соединения для указанного соединения.

**Microsoft. Перцептионсимулатион. ISimulatedHand3. Сетжоинтконфигуратион**

Задает конфигурацию соединения для указанного соединения.

**Microsoft. Перцептионсимулатион. ISimulatedHand3. Сесандпосе**

Задайте для параметра "рука" известное значение с необязательным флагом для анимации.  Примечание. анимация не приведет к тому, что присоединения будут немедленно отражены в своих окончательно Объединенных конфигурациях.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft. Перцептионсимулатион. Исимулатедхеад

Интерфейс, описывающий заголовок имитации человека.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft. Перцептионсимулатион. Исимулатедхеад. Ворлдпоситион**

Получение расположения узла относительно мира в метрах.

**Microsoft. Перцептионсимулатион. Исимулатедхеад. вращение**

Извлеките поворот моделируемой головки. Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.

**Microsoft. Перцептионсимулатион. Исимулатедхеад. диаметр**

Получение диаметра смоделированного головного элемента. Это значение используется для определения центра заголовка (точки вращения).

**Microsoft. Перцептионсимулатион. Исимулатедхеад. вращение (Microsoft. Перцептионсимулатион. Rotation3)**

Поворот смоделированной головки относительно текущего поворота. Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.

Параметры
* вращение — величина поворота.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft. Перцептионсимулатион. ISimulatedHead2

Дополнительные свойства доступны путем приведения Исимулатедхеад к ISimulatedHead2.

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft. Перцептионсимулатион. ISimulatedHead2. глаза**

Извлеките глаза имитации человека.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер

Интерфейс, описывающий ДОФ контроллер, связанный с имитируемым человеком.

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Ворлдпоситион**

Получение расположения узла относительно мира в метрах.

**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. status**

Возвращает или задает текущее состояние контроллера.  Для состояния контроллера должно быть задано значение, отличное от OFF, прежде чем все вызовы для перемещения, вращения или нажатия кнопки будут выполнены.

**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. положением**

Получение или установка положения имитации контроллера относительно человека в метрах.

**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Orientation**

Получение или установка ориентации имитации контроллера.

**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Move (Microsoft. Перцептионсимулатион. Vector3)**

Переместить положение имитации контроллера относительно его текущего положения в метрах.

Параметры
* перевод — это величина, на которую нужно перевести имитируемый контроллер.

**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Прессбуттон (Симулатедсиксдофконтроллербуттон)**

Нажмите кнопку на имитации контроллера.  Она будет обнаружена системой только в том случае, если контроллер включен.

Параметры
* Кнопка для нажатия кнопки.

**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Релеасебуттон (Симулатедсиксдофконтроллербуттон)**

Выпустите кнопку на имитации контроллера.  Она будет обнаружена системой только в том случае, если контроллер включен.

Параметры
* Кнопка для выпуска.

**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Жеттаучпадпоситион (out float, out float)**

Получить расположение имитации пальца на сенсорной панели имитации контроллера.

Параметры
* x — горизонтальное расположение пальца.
* y — вертикальное расположение пальца.

**Microsoft. Перцептионсимулатион. Исимулатедсиксдофконтроллер. Сеттаучпадпоситион (float, float)**

Установите расположение имитации пальца на сенсорной панели имитации контроллера.

Параметры
* x — горизонтальное расположение пальца.
* y — вертикальное расположение пальца.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft. Перцептионсимулатион. ISimulatedSixDofController2

Дополнительные свойства и методы доступны путем приведения Исимулатедсиксдофконтроллер к ISimulatedSixDofController2.

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft. Перцептионсимулатион. ISimulatedSixDofController2. Жетсумбстиккпоситион (out float, out float)**

Получение расположения имитации аналогового стика на имитации контроллера.

Параметры
* x — горизонтальное расположение стика.
* y — вертикальное расположение стика.

**Microsoft. Перцептионсимулатион. ISimulatedSixDofController2. Сетсумбстиккпоситион (float, float)**

Задайте расположение имитации аналогового стика на имитации контроллера.

Параметры
* x — горизонтальное расположение стика.
* y — вертикальное расположение стика.

**Microsoft. Перцептионсимулатион. ISimulatedSixDofController2. Баттерилевел**

Получение или установка уровня заряда батареи для имитации контроллера.  Значение должно быть больше 0,0 и меньше или равно 100,0.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft. Перцептионсимулатион. Исимулатедэйес

Интерфейс, описывающий глаза имитации человека.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft. Перцептионсимулатион. Исимулатедэйес. вращение**

Извлеките поворот имитации глаз. Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.

**Microsoft. Перцептионсимулатион. Исимулатедэйес. вращение (Microsoft. Перцептионсимулатион. Rotation3)**

Поворот имитации глаз относительно текущего вращения. Положительные радианы при просмотре по оси поворачиваются по часовой стрелке.

Параметры
* вращение — величина поворота.

**Microsoft. Перцептионсимулатион. Исимулатедэйес. Калибратионстате**

Возвращает или задает состояние калибровки для имитации глаз.

**Microsoft. Перцептионсимулатион. Исимулатедэйес. Ворлдпоситион**

Получение расположения узла относительно мира в метрах.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft. Перцептионсимулатион. Исимулатионрекординг

Интерфейс для взаимодействия с одной записью, загруженной для воспроизведения.

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**Типы Microsoft. Перцептионсимулатион. Исимулатионрекординг.**

Возвращает список типов данных в записи.

**Microsoft. Перцептионсимулатион. Исимулатионрекординг. State**

Извлекает текущее состояние записи.

**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Play**

Запустите воспроизведение. Если запись приостановлена, воспроизведение будет возобновлено из приостановленного расположения. При остановке воспроизведение начнется с самого начала. Если воспроизведение уже проигрывается, этот вызов игнорируется.

**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Pause**

Приостанавливает воспроизведение в текущем расположении. Если запись остановлена, вызов игнорируется.

**Microsoft. Перцептионсимулатион. Исимулатионрекординг. Seek (System. UInt64)**

Выполняет поиск записи в указанное время (в 100-наносекундах секунд с начала) и приостанавливается в этом расположении. Если время превышает окончание записи, оно приостанавливается на последнем кадре.

Параметры
* такты — время поиска.

**Microsoft. Перцептионсимулатион. Исимулатионрекординг. останавливаться**

Останавливает воспроизведение и сбрасывает текущую точку в начало.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft. Перцептионсимулатион. Исимулатионрекордингкаллбакк

Интерфейс для получения изменений состояния во время воспроизведения.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft. Перцептионсимулатион. Исимулатионрекордингкаллбакк. Плайбаккстатечанжед (Microsoft. Перцептионсимулатион. PlaybackState)**

Вызывается при изменении состояния воспроизведения Исимулатионрекординг.

Параметры
* newState — новое состояние записи.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер

Корневой объект для создания объектов имитации восприятия.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Креатеперцептионсимулатионманажер (Microsoft. PerceptionSimulation. ISimulationStreamSink)**

Создать на объекте для создания смоделированных пакетов и доставки их в предоставленный приемник.

Параметры
* приемник — приемник, который будет принимать все созданные пакеты.

Возвращаемое значение

Созданный диспетчер.

**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Креатеперцептионсимулатионрекординг (System. String)**

Создание приемника, в котором хранятся все полученные пакеты в файле по указанному пути.

Параметры
* путь — путь к создаваемому файлу.

Возвращаемое значение

Созданный приемник.

**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Лоадперцептионсимулатионрекординг (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**

Загрузка записи из указанного файла.

Параметры
* путь — путь к загружаемому файлу.
* Factory — фабрика, используемая записью для создания Исимулатионстреамсинк при необходимости.

Возвращаемое значение

Загруженная запись.

**Microsoft. Перцептионсимулатион. Перцептионсимулатионманажер. Лоадперцептионсимулатионрекординг (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**

Загрузка записи из указанного файла.

Параметры
* путь — путь к загружаемому файлу.
* Factory — фабрика, используемая записью для создания Исимулатионстреамсинк при необходимости.
* обратный вызов — обратный вызов, который получает обновления, которые обновляют состояние записи.

Возвращаемое значение

Загруженная запись.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft. Перцептионсимулатион. Стреамдататипес

Описывает различные типы потоковых данных.

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

**Microsoft. Перцептионсимулатион. Стреамдататипес. None**

Значение Sentinel, используемое для обозначения отсутствия типов данных потока.

**Microsoft. Перцептионсимулатион. Стреамдататипес. Head**

Поток данных для положения и ориентации головного элемента.

**Microsoft. Перцептионсимулатион. Стреамдататипес. руки**

Поток данных для расположения и жестов стрелок.

**Microsoft. Перцептионсимулатион. Стреамдататипес. Спатиалмаппинг**

Поток данных для пространственного сопоставления среды.

**Microsoft. Перцептионсимулатион. Стреамдататипес. Калибровка**

Поток данных для калибровки устройства. Пакеты калибровки принимаются только системой в удаленном режиме.

**Microsoft. Перцептионсимулатион. Стреамдататипес. Environment**

Поток данных для среды устройства.

**Microsoft. Перцептионсимулатион. Стреамдататипес. Сиксдофконтроллерс**

Поток данных для контроллеров движения.

**Microsoft. Перцептионсимулатион. Стреамдататипес. глаза**

Поток данных с глазами имитации человека.

**Microsoft. Перцептионсимулатион. Стреамдататипес. Дисплайконфигуратион**

Поток данных с конфигурацией экрана устройства.

**Microsoft. Перцептионсимулатион. Стреамдататипес. ALL**

Значение Sentinel, используемое для указания всех записанных типов данных.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft. Перцептионсимулатион. Исимулатионстреамсинк

Объект, получающий пакеты данных из потока имитации.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft. Перцептионсимулатион. Исимулатионстреамсинк. Онпаккетрецеивед (длина uint, Byte [], пакет)**

Получает один пакет, который внутренне типизирован и имеет версию.

Параметры
* Длина — Длина пакета.
* пакет — данные пакета.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft. Перцептионсимулатион. Исимулатионстреамсинкфактори

Объект, создающий Исимулатионстреамсинк.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft. Перцептионсимулатион. Исимулатионстреамсинкфактори. Креатесимулатионстреамсинк ()**

Создает единственный экземпляр Исимулатионстреамсинк.

Возвращаемое значение

Созданный приемник.