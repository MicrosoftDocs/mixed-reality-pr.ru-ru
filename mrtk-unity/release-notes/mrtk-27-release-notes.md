---
title: Заметки о выпуске MRTK 2.7
description: Заметки о выпуске для MRTK версии 2.7
author: RogPodge
ms.author: roliu
ms.date: 06/16/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK, XRSDK, устаревшая смешанная реальность, Leap Motion, Ultraleap, OpenXR
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 921cdb4d9643e55841bc7c979066c276f5fd80998ad97d19332c528cebe05c37
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203529"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Заметки о выпуске Microsoft Mixed Reality Toolkit 2.7

## <a name="whats-new-in-272"></a>Новые возможности версии 2.7.2

### <a name="fixed-a-upm-package-dependency-issue"></a>Исправлена проблема с зависимостью пакета UPM

С пакетами UPM в MRTK 2.7.1 возникала проблема, из-за которой зависимости настраивались неправильно. Эта проблема приводила к тому, что Mixed Reality Feature Tool не удавалось правильно импортировать пакеты MRTK 2.7.1. В версии 2.7.2 эта проблема устранена. В этой версии по сравнению с версией 2.7.1 отсутствуют изменения кода.


## <a name="whats-new-in-271"></a>Новые возможности версии 2.7.1

### <a name="show-version"></a>Show version (Показать версию)

Меню `Mixed Reality` > `Toolkit` теперь содержит запись `Show version...` (Показать версию), которая позволяет изучить пакет Mixed Reality Toolkit Foundation и определить, какая версия MRTK используется проектом.

![Меню Show version (Показать версию)](images/ShowVersionMenu.png)

![Диалоговое окно с версией MRTK](images/VersionDialog.png)

> [!NOTE]
> Если MRTK был клонирован из [репозитория GitHub](https://aka.ms/mrtk), сведения о версии будут отсутствовать.
>
> ![Не удается определить версию](images/CannotDetermineVersion.png)

### <a name="authors-list"></a>Список авторов

Начиная с MRTK версии 2.7.1, файл со списком авторов включается в пакет Mixed Reality Toolkit Foundation.

### <a name="integrated-openxr-project-setup-into-the-configurator-setup-flow"></a>Настройка проекта OpenXR интегрирована в процесс настройки конфигуратора

Начиная с MRTK версии 2.7.1, пользователи подключаемого модуля OpenXR для смешанной реальности получают инструкции по настройке такого модуля в MRTK. Для пользователей, которые будут использовать HoloLens 2, доступен вариант с автоматическим применением рекомендуемых параметров.

![Окно конфигуратора с инструкциями по настройке OpenXR](images/configuratorMROpenXR.png)

### <a name="notable-bugfixes-and-changes"></a>Важные исправления и изменения

- Класс Unity Joystick Manager помечен как поддерживаемый в конвейере пакета SDK смешанной реальности [№ 9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954), [№ 9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994).
- Добавлены проверки в код интерактивного инспектора, чтобы предотвратить появление ошибок со значением NULL [№ 9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943).
- Добавлен поставщик сеток OpenXR в пример сцены с шейдером пульса [№ 9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902).
- Восстановлен профиль физического взаимодействия с помощью рук в примере сцены [№ 9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915).
- Скрипты HandConstraint* были оптимизированы [№ 9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935).
- Исправлены некоторые ошибки, влияющие на создание и клонирование профилей [№ 9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982).


## <a name="whats-new-in-270"></a>Новые возможности в версии 2.7.0

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR теперь официально поддерживается в MRTK

Так как функциональность новых подключаемых модулей OpenXR постоянно совершенствуется, MRTK теперь официально поддерживает OpenXR. По сравнению с прошлыми выпусками мы добавили следующие возможности в проекты, использующие OpenXR:

- [Поддержка предоставляемой системой модели контроллера движений](#support-for-the-system-provided-motion-controller-model-on-openxr).
- Поддержка жестов WinMR (выбор, удержание, манипулирование и навигация) [№ 9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843).
- [Поддержка тактильной обратной связи контроллера](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr).
- [Поддержка суставной виртуальной руки в HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr).
- Поддержка пространственного сопоставления в HoloLens 2 [№ 9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [№ 9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827).
- Поддержка интерпретации сцены в HoloLens 2 [№ 9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744).

Если вы планируете использовать HoloLens 2 или гарнитуры смешанной реальности Windows с OpenXR, обязательно установите **подключаемый модуль OpenXR для смешанной реальности версии 0.9.5 или выше** с помощью [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool). В противном случае вы не сможете использовать некоторые из описанных выше возможностей.

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>Поставщики данных устаревшей смешанной реальности и пакета SDK смешанной реальности теперь можно использовать в одном профиле

Поставщики данных теперь также будут загружаться при выборе соответствующего конвейера, что позволяет поставщикам данных устаревшей смешанной реальности и пакета SDK смешанной реальности параллельно существовать в одном профиле. Для этого поставщики данных устаревшей смешанной реальности и пакета SDK смешанной реальности теперь разнесены на разные вкладки в представлении профиля, благодаря чему пользователи могут определить, выбран ли у них правильный профиль для нужного конвейера смешанной реальности.

![Поставщиков данных устаревшей смешанной реальности и пакета SDK смешанной реальности теперь можно объединить в одном профиле](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

Для этого поставщики данных со значениями NULL теперь не будут загружаться в инспектор профилей и отображаться в нем. Пользователи могут переключить параметр `Show null data providers in the profile inspector` (Показывать поставщики данных со значениями NULL в инспекторе профилей), выбрав **Edit -> Project Settings -> Mixed Reality Toolkit** (Правка -> Параметры проекта -> Mixed Reality Toolkit), чтобы выполнить отладку неожиданного поведения с отсутствующими поставщиками данных.

![Поставщики данных со значениями NULL теперь скрыты по умолчанию](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
![Переключение отображения поставщиков данных со значениями NULL в инспекторе профилей](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>Добавлены параметры взаимодействия и связанное поведение содержимого сцены смешанной реальности

Пользователи теперь могут настроить [параметры взаимодействия](../features/experience-settings/experience-settings.md), которые позволяют MRTK отображать [содержимое сцены смешанной реальности](../features/experience-settings/scene-content.md) с учетом целевого взаимодействия.

Если предыдущие параметры шкалы взаимодействия пользователя не соответствуют новому профилю параметров взаимодействия, в инспекторе отобразится запрос на их исправление

![Перенос шкалы взаимодействия](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>Обновленный конфигуратор теперь помогает пользователю выполнить настройку

Новый конфигуратор MRTK предоставляет пошаговые рекомендации по надлежащей настройке проекта для разработки смешанной реальности и ее использования с MRTK. Он включает такие действия, как выбор конвейера смешанной реальности, получение подключаемых модулей для платформы, импорт TextMeshPro, отображение примеров (при использовании UPM) и других ранее включенных рекомендуемых параметров для проекта.

![Конфигуратор отображает список конвейеров](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>Точка телепорта улучшена

Новый [компонент точки телепорта](../features/teleport-system/teleport-hotspot.md) улучшен. Вы можете добавить точку телепорта в GameObject, чтобы настроить для пользователя расположение и ориентацию в определенной позиции при телепорте.

![Пример точки телепорта](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Остановка взгляда улучшена

Функция остановки взгляда и ее пример теперь вышли из экспериментальной версии. Новые примеры объемных кнопок в стиле HoloLens 2 теперь включены в пример сцены.

![Карточка остановки взгляда](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Добавлена поддержка для модулей Unity Leap Motion версий 4.6.0, 4.7.0, 4.7.1 и 4.8.0

Поддержка для последних версий [модулей Unity Leap Motion](https://developer.leapmotion.com/unity) теперь совместима с MRTK 2.7.0. Дополнительные сведения см. в статье [Как настроить MRTK для Leap Motion](../supported-devices/leap-motion-mrtk.md).

Благодарим @jackyangzzh за новую сцену LeapMotionOrientationExample!

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Вызванные заданные события речи больше не ограничены указателями взгляда

Ранее заданные события речи могли быть вызваны только для объектов, на которых был установлен фокус указателя взгляда. Теперь объекты могут получать события речи, если на них установлен фокус любого указателя.

![События речи с дальними указателями](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>Выполнено портирование TextToSpeech из HTK в MRTK

Популярный скрипт TextToSpeech наконец доступен в MRTK. Он упрощает создание речи из текста на платформе UWP с помощью [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer). Также добавлен пример сцены для демонстрации этой функции.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>Поддержка предоставляемой системой модели контроллера движений в OpenXR

Включена поддержка (в редакторе и среде выполнения) предоставляемой системой модели контроллера в OpenXR.

![Окно редактора с отображением двух моделей контроллера движений](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>Поддержка суставной виртуальной руки HoloLens 2 в OpenXR

![Виртуальная рука, выполняющаяся на устройстве в примере сцены MRTK](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>Поддержка тактильной обратной связи контроллера в устаревшем модуле WMR, подключаемом модуле Windows XR и OpenXR

Включена поддержка тактильной обратной связи контроллера в устаревшем модуле WMR, подключаемом модуле Windows XR и OpenXR. [№ 9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Поддержка отслеживания взгляда в подключаемом модуле Windows XR

Включена поддержка отслеживания взгляда при использовании минимальных версий подключаемого модуля Windows XR 2.7.0 (Unity 2019), 4.4.2 (Unity 2020) и 5.2.2 (Unity 2021). [№ 9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>Важные исправления и изменения

- Обнаружение уменьшения стало более плавным. Теперь сложнее случайно прервать жест уменьшения. [№ 9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- Объекты с компонентом Object Manipulator теперь стабильно поддерживают скорость при отпускании, если задан флаг. [№ 9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- При движении назад теперь выполняется проверка на наличие пола, что позволяет предотвратить ситуации, в которых камера может застрять в объектах окружения или над пустым пространством.[№ 9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject теперь является виртуальным свойством, что повышает гибкость при расширении указателя сферы или указателя тычка. [№ 9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- Кнопки теперь отображают правильное ключевое слово при отображении доступной речевой команды. [№ 9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Контроллеры Oculus теперь используют собственный автономный визуализатор, что предотвращает конфликты визуализаций MRTK с визуализацией пакета интеграции Oculus. [№ 9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Скрипты, связанные с клавиатурой, были изменены в соответствии с поведением в последних версиях Unity (2019.4.25 и выше и 2020.3.2 и выше). На момент выпуска все еще существует ошибка с автозавершением и ошибка с полем ввода (которые не зависят от MRTK), влияющие на работу HoloLens. Дополнительные сведения см. в описании проблемы [№ 9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) и [№ 9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Улучшена производительность прокрутки коллекции объектов. Также исправлена проблема, из-за которой GameObject в коллекции утрачивал материал при копировании. [№ 9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [№ 9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- В демонстрационный скрипт интерпретации сцены добавлена функция `GetSceneObjectsOfType` для получения всех наблюдаемых объектов сцены определенного вида. [№ 9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [№ 9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- В средстве сборки командной строки в сборку будут включены только сцены, указанные с помощью флагов `sceneList` или `sceneListFile` (при наличии каких-либо флагов). [№ 9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- В средстве сборки доступна новая возможность для указания пути к файлу `nuget.exe` и его использования для восстановления пакета (вместо использования `msbuild` по умолчанию). [№ 9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Исправлена проблема, из-за которой использование подключаемого модуля Windows XR Plugin могло приводить к неподвижности сочленений руки и дублированию виртуальных рук. [№ 9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Исправлена проблема, из-за которой использование функции автоматического удаленного взаимодействия в подключаемом модуле Windows XR приводило к отсутствующим входным данным и взаимодействиям. [№ 9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- Исправлена проблема, из-за которой класс BuildDeployWindow пытался отправить запрос к недопустимому разделу реестра для пути пакета SDK Windows. [№ 9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Средства импорта glTF в MRTK теперь необязательны. Если доступно несколько средств импорта glTF, средства импорта MRTK теперь можно отключить, добавив `MRTK_GLTF_IMPORTER_OFF` в пользовательские символы определения скрипта (Scripting Define Symbols). [№ 9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- Исправлена проблема, из-за которой контроллеры Knuckles в OpenVR не обнаруживались надлежащим образом. [№ 9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Уменьшено число покадровых размещений при визуализации виртуальной руки [№ 9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Добавлен пункт меню для запуска пакета с примерами MRTK (в диспетчере пакетов Unity), чтобы упростить импорт примеров [№ 9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Уменьшено число предупреждений о времени загрузки при использовании Unity 2020.3.
- Добавлена документация по функции окна сборки: [посетить страницу](../features/tools/build-window.md)

## <a name="known-issues"></a>Известные проблемы

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>В аудиодемонстрациях отсутствует ASMDEF-файл (пакет UPM)

При импорте MRTK через Mixed Reality Feature Tool примеры и демонстрации добавляются в проект с помощью пользовательского интерфейса диспетчера пакетов Unity. После импорта аудиодемонстраций сцена `WindowsMicrophoneStreamDemo.unity` не будет работать надлежащим образом. Это вызвано отсутствием ASMDEF-файла для примера.

Чтобы устранить эту [проблему](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908), выполните следующие шаги:

- Скопируйте файл Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...]/MRTK.Examples.asmdef в свою папку Assets/Samples/Mixed Reality Toolkit Examples.
- Переименуйте скопированный файл в Examples.
- Откройте файл Examples.
- В поле Name (Имя) замените содержимое на Examples.
- Нажмите кнопку Apply (Применить).
- Сборка и развертывание

Эта проблема будет исправлена в следующем выпуске MRTK.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>Окно сборки MRTK вызывает бесконечный запуск диалогового окна Importing assets (Импорт активов) в Unity 2020.3

Существует известная [проблема](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) с окном сборки MRTK в Unity 2020.3, из-за которой после успешной сборки UWP диалоговое окно Importing assets (Импорт активов) не закрывается. Мы изучаем эту проблему совместно с командой Unity.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Предупреждения Text Mesh Pro Canvas Renderer в Unity 2020

Следующее предупреждение отображается в большинстве примеров сцен MRTK при использовании Unity 2020:

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

Предупреждение Canvas Renderer было добавлено в [TextMeshPro версии 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3). Эти предупреждения не влияют на работу примеров сцен MRTK, поэтому их можно удалять из консоли. Дополнительные сведения см. в описании [проблемы 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811).