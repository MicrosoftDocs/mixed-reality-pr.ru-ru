---
title: Запись анимации входных данных
description: Документация по системе записи анимации ввода в МРТК
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 1a900b7b419a0aca45c3601ed583ef6c2e326574cb9e732edd0474afe117b895
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223075"
---
# <a name="input-animation-recording"></a>Запись анимации входных данных

МРТК включает в себя систему записи, с помощью которой можно хранить данные отслеживания головного и ручного хранения в файлах анимации. Затем записанные данные можно воспроизводить с помощью [системы имитации ввода](input-simulation-service.md).

Запись входных данных является полезным инструментом в различных ситуациях.

* Создание автоматических тестов для взаимодействия, манипуляций, поиска решений и т. д. Создание перемещения контроллеров и движений для этих тестов может занять много времени. Непосредственная запись данных может ускорить процесс и предоставить реальные данные.
* Обучение использованию элементов UX с помощью анимации.
  Показывая пользователям, как взаимодействовать с кнопками и другими объектами, можно сгладить кривую обучения.
* Отладка непредвиденного поведения, которое может быть обнаружено во время обычного использования.
  Система записи поддерживает концепцию последовательного буфера, которая позволяет записывать последние входные данные в фоновом режиме.
  См. раздел [служба регистрации входных данных](#input-recording-service).

## <a name="recording-and-playback-services"></a>Службы записи и воспроизведения

Предоставляются две системные службы ввода для записи и воспроизведения данных, соответственно.

### <a name="input-recording-service"></a>Служба записи ввода

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) принимает данные из основного преобразования камеры и активных контроллеров и сохраняет их во внутреннем буфере. После запроса эти данные сериализуются в двоичные файлы для хранения и последующего воспроизведения.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="Запись анимации ввода" width="80%" alt="Recording diagram" class="center" />
</a>

Чтобы начать запись входных данных, вызовите [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) функцию. [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) приостанавливает запись (но не удаляет данные, записанные на данный момент [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) ). при необходимости используйте для этого.

По умолчанию размер буфера записи ограничен 30 секундами. Это позволяет службе записи сохранять данные в фоновом режиме без накопления слишком большого объема данных, а затем при необходимости сохранить последние 30 секунд. Интервал времени можно изменить с помощью [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) свойства, или запись может быть неограниченной с помощью [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) параметра.

Данные в буфере записи можно сохранить в двоичном файле с помощью функции [савеинпутаниматион](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) .

Дополнительные сведения о формате двоичного файла см. в статье [Спецификация формата файла анимации ввода](input-animation-file-format.md).

### <a name="input-playback-service"></a>Входная служба воспроизведения

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) считывает двоичный файл со входными данными анимации, а затем применяет эти данные через [инпутсимулатионсервице](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) для повторного создания записанных перемещений.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="Воспроизведение обратной анимации ввода" width="80%" alt="Play Back diagram" class="center" />
</a>

Чтобы начать воспроизводить анимацию ввода, она должна быть загружена из файла с помощью функции [лоадинпутаниматион](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) .

Вызов метода [Play](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), [паузы](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)или [остановки](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) для управления воспроизведением анимации.

Текущее время анимации также можно контролировать непосредственно с помощью свойства [localtime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) .

> [!WARNING]
> Циклический перебор или сброс анимации ввода или настройки [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) непосредственно путем очистки временной шкалы могут привести к непредвиденным результатам при обработке сцены! Записываются только перемещения ввода, любые дополнительные изменения, такие как перемещение объектов или перевернутые коммутаторы, не будут сброшены. Обязательно перезагрузите сцену, если внесены необратимые изменения.

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>Средства редактора для записи и воспроизведения анимации ввода

В редакторе Unity существует ряд средств для записи и изучения анимации ввода. доступ к этим средствам можно получить в [окне средства моделирования ввода](input-simulation-service.md#input-simulation-tools-window), которое можно открыть из меню " _смешанная реальность набор средств > служебные программы" > "имитация входа_ ".

> [!NOTE]
> Запись и воспроизведение входных данных работают только в режиме воспроизведения.

Окно записи ввода имеет два режима:

* _Запись_ для записи входных данных в режиме воспроизведения и их сохранение в файлах анимации.

  При переключении на кнопку запись [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) включается для записи входных данных.
  При отключении кнопки записи отображается выбранный файл сохранение, а Записанная анимация ввода сохраняется в выбранном месте назначения.

  В этом режиме можно также изменить ограничение времени буфера.

* _Воспроизведение_ для загрузки файлов анимации и последующее повторное создание входных данных с помощью системы имитации ввода.

  Сначала необходимо загрузить анимацию в этом режиме. После записи входных данных в режиме записи Результирующая анимация загружается автоматически. Можно также нажать кнопку "Загрузить", чтобы выбрать существующий файл анимации.

  Кнопки управления временем слева направо:

  * _Сброс_ времени воспроизведения до начала анимации.
  * Постоянно _воспроизводить_ анимацию со временем.
  * _Шаг_ вперед на один шаг.

  Ползунок также можно использовать для очистки временной шкалы анимации.

> [!WARNING]
> Циклическая или сброс анимации ввода или Очистка временной шкалы может привести к непредвиденным результатам при управлении сценой. Записываются только перемещения ввода, любые дополнительные изменения, такие как перемещение объектов или перевернутые коммутаторы, не будут сброшены. Обязательно перезагрузите сцену, если внесены необратимые изменения.
