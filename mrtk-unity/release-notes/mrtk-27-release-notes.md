---
title: Заметки о выпуске МРТК 2,7
description: Заметки о выпуске МРТК версии 2,7
author: RogPodge
ms.author: roliu
ms.date: 05/27/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, разработка, МРТК, КСРСДК, устаревший XR, LEAP Motion, Ултралеап
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 92c8705c70a2a6c1e25f1ed6b1f87eac1e5726e0
ms.sourcegitcommit: 11d5d7c3fdd59c1ebcfca34dbb6d84c05b481e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/10/2021
ms.locfileid: "111897407"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Заметки о выпуске Microsoft Mixed Reality Toolkit 2,7

## <a name="whats-new-in-270"></a>Новые возможности в 2.7.0

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>Опенкср теперь официально поддерживается в МРТК

Так как новые подключаемые модули Опенкср становятся более и более зрелыми МРТК, теперь официально поддерживает Опенкср. По сравнению с предыдущими выпусками мы добавили в проекты следующие возможности с помощью Опенкср:

- [Поддержка модели контроллера движения, предоставляемой системой](#support-for-the-system-provided-motion-controller-model-on-openxr)
- Поддержка жестов Винмр (выбор, удержание, манипуляция и навигация) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [Поддержка хаптикс контроллера](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [Поддержка сочлененной сетки в HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- Поддержка пространственного сопоставления в HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- Поддержка сцены на сценах в HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>Устаревшие поставщики данных XR и XR SDK теперь можно использовать в одном и том же профиле.

Поставщики данных теперь также будут загружаться только при выборе соответствующего конвейера, что позволяет использовать как устаревшие поставщики данных XR и XR SDK в одном профиле. В соответствии с этим устаревшие поставщики данных XR и XR SDK теперь организованы на разных вкладках в представлении профиля, помогая пользователям определить, есть ли у них правильный профиль для целевого конвейера XR.

![Поставщики данных предыдущих версий и XR SDK теперь могут быть объединены в одном профиле.](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

Для этого поставщики данных, имеющие значение null, теперь больше не будут загружаться и отображаться в инспекторе профилей. Пользователи могут переключаться `Show null data providers in the profile inspector` в разделе **Edit-> Project Settings (> Mixed Reality Toolkit)** для отладки непредвиденных поведений с отсутствующими поставщиками данных.

![Поставщики данных со значением NULL теперь скрыты по умолчанию. ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
 ![ переключатель Показать поставщики данных со значением NULL в инспекторе профилей](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>Добавлены параметры интерфейса и связанное поведение содержимого сцены смешанной реальности.

Теперь пользователи могут настроить [Параметры взаимодействия](../features/experience-settings/experience-settings.md), что позволит Мртк отображать [содержимое сцены смешанной реальности](../features/experience-settings/scene-content.md) в соответствии с целевым интерфейсом.

Если параметры масштабирования пользователя, указанные выше, не соответствуют новому профилю параметров интерфейса, им будет предложено исправить его в инспекторе

![Масштабирование возможностей миграции](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>Переработанный Конфигуратор теперь помогает пользователю выполнить процесс установки.

Новое конфигуратор МРТК предоставляет пользователям пошаговые инструкции для правильной настройки проекта для разработки XR и использования с МРТК. Он охватывает выбор конвейера XR, получение подключаемых модулей для платформы, импорт Текстмешпро, отображение примеров (при использовании УПМ) и других ранее рекомендованных параметров для проекта.

![Конфигуратор, отображающий список конвейеров](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>Активная точка телепортируйтесь с градиентом

В новом [компоненте хот-спота телепортируйтесь](../features/teleport-system/teleport-hotspot.md) был установлен градиент. Вы можете добавить хот-спот телепортируйтесь в GameObject, чтобы обеспечить пользователю определенную позицию и ориентацию при телепортироваться к этому расположению.

![Пример хот HotSpot для телепортируйтесь](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Вдаваясь с градиентом

Теперь функция и пример вдаваясь перестали быть экспериментальными. В образец сцены включены новые примеры кнопок стиля объемные HoloLens 2.

![Вдаваясь Hero](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Добавлена поддержка модулей Unity для Motion версии 4.6.0, 4.7.0, 4.7.1 и 4.8.0

Поддержка последних версий [модулей Unity в LEAP](https://developer.leapmotion.com/unity) теперь СОВМЕСТИМА с мртк 2.7.0.  Дополнительные сведения см. [в статье Настройка мртк для LEAP Motion](../supported-devices/leap-motion-mrtk.md) .

Большое спасибо @jackyangzzh за участие в новой леапмотионориентатионексампле сцене!

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Целевые события речи больше не ограничены для указателей взгляда

Ранее целевые события распознавания речи могли быть вызваны только для объектов, которые были сосредоточены на указателе взгляда. Теперь объекты могут получить события распознавания речи, если они связаны любым указателем.

![События речи с дальней указателем](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>Перенос Тексттоспич из ХТК в МРТК

Видеомагнитофон Тексттоспич Script теперь доступен в МРТК, чтобы помочь вам создавать речь из текста на платформе UWP с помощью [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) . Также добавлен пример сцены для демонстрации этой функции.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>Поддержка предоставляемой системой модели контроллера движения на Опенкср

Добавлена поддержка, как в редакторе, так и во время выполнения, для предоставляемой системой модели контроллера движения на Опенкср.

![Окно редактора, отображающее две модели контроллеров движения](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>Поддержка сетки с сочленением HoloLens 2 в Опенкср

![Сетка "рука", выполняющаяся на устройстве в МРТК примере сцены](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>Поддержка хаптикс контроллера в устаревших ВМР, подключаемом модуле Windows XR и Опенкср

Добавлена поддержка хаптикс контроллера для устаревших ВМР, подключаемого модуля Windows XR и Опенкср. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Поддержка отслеживания взгляда в подключаемом модуле Windows XR

Добавлена поддержка глаза при использовании минимальных версий подключаемого модуля Windows XR 2.7.0 (Unity 2019), 4.4.2 (Unity 2020) и 5.2.2 (Unity 2021). [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>Важные исправлений и изменения

- Обнаружение сжатия стало более гладким. Теперь нельзя случайно удалить жест сжатия. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- Объекты с компонентом манипулятора объекта теперь постоянно поддерживают скорость выпуска при установке флага. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- Обратная страфинг теперь проверяет наличие пола, помогая предотвратить ситуации, когда камера может обрезать окружение или когда пользователь наводит указатель мыши на пустое место. [#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- Иснеаробжект теперь является виртуальным свойством, что обеспечивает большую гибкость при расширении сферы или указателя. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- Теперь на кнопках отображается правильное ключевое слово при отображении команды распознавания речи. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Контроллеры Окулус теперь используют собственный автономный визуализатор, предотвращая конфликт визуализации МРТК с визуализацией пакета интеграции Окулус. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Сценарии, связанные с клавиатурой, были изменены в соответствии с поведением в последних версиях Unity (2019.4.25 + & 2020.3.2 +). В выпуске по-прежнему есть ошибка автоматического завершения и поле ввода TMP (они являются внешними по МРТК), влияющие на HoloLens. Дополнительные сведения см. в разделе [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) и [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Улучшена производительность прокрутки коллекции объектов. Также исправлена проблема, из – за которой GameObject в коллекции теряет материалы при дублировании. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- В демонстрационном сценарии демонстрации сцены добавлена `GetSceneObjectsOfType` функция для получения всех наблюдаемых объектов сцены определенного типа. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- В средстве сборки командной строки в сборку будут включаться только сцены, заданные `sceneList` `sceneListFile` флагами или (при наличии любого флага). [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- В средстве сборки имеется новый параметр для указания пути к `nuget.exe` и использования для выполнения восстановления пакета вместо `msbuild` параметра (по умолчанию). [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Исправлена проблема, при которой использование подключаемого модуля XR для Windows может привести к устаревшим соединениям и удвоенным сеткам руки. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Исправлена проблема, при которой при использовании функции автоматического удаленного взаимодействия подключаемого модуля Windows XR отсутствует возможность входа и взаимодействия. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- Исправлена проблема, при которой Буилддеплойвиндов попытается запросить недопустимый ключ реестра для пути Windows SDK. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Средства импорта Глтф для МРТК теперь являются необязательными. Если имеется несколько Глтф импортеров, МРТК можно отключить, добавив `MRTK_GLTF_IMPORTER_OFF` в пользовательский скрипт символы. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- Исправлена проблема, когда контроллеры Кнукклес в Опенвр не были правильно обнаружены. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Уменьшите число распределений по кадрам при визуализации сетки "рука" [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Добавлен пункт меню для запуска пакета примеров МРТК (в диспетчере пакетов Unity), чтобы упростить импорт примеров [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Сокращение количества предупреждений во время загрузки при использовании Unity 2020,3.
- Добавлена документация по функциям окна сборки: [посетите страницу](/windows/mixed-reality/mrtk-unity/features/tools/build-window) .

## <a name="known-issues"></a>Известные проблемы

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>В демонстрациях аудио отсутствует файл асмдеф (пакет УПМ)

При импорте МРТК с помощью средства "функция смешанной реальности" образцы и демонстрации добавляются в проект с помощью пользовательского интерфейса диспетчера пакетов Unity. После импорта демонстрационных аудио `WindowsMicrophoneStreamDemo.unity` сцены будут работать неправильно. Это результат отсутствующего асмдеф-файла для образца.

Чтобы обойти эту [ошибку](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908), выполните следующие действия.

- Копировать библиотеку, Паккажекаче/com.microsoft.mixedreality.toolkit.examples@ [...] /мртк. Примеры. асмдеф в папку "Assets/Samples/примеры набора средств смешанной реальности"
- Переименование скопированного файла в примеры
- Открытие файла примеров
- В поле Имя замените содержимое примерами.
- Нажмите кнопку Применить.
- Сборка и развертывание

Эта проблема будет исправлена в предстоящем выпуске МРТК.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>Окно сборки МРТК активирует неопределенное диалоговое окно "Импорт ресурсов" в Unity 2020,3

Существует известная [Ошибка](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) в окне сборки Мртк в Unity 2020,3, где после успешного выполнения сборки UWP диалоговое окно "Импорт ресурсов" не завершается. Эта проблема изучается в связи с Unity.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Предупреждения модуля подготовки холста для визуализации текста в Unity 2020

Следующее предупреждение регистрируется в большинстве МРТК примеров сцен при использовании Unity 2020:

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

Предупреждение модуля подготовки холста Добавлено в [текстмешпро версии 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3).  Эти предупреждения не влияют на примеры сцен МРТК и могут быть удалены из консоли. Дополнительные сведения см. в описании [проблемы 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) .
