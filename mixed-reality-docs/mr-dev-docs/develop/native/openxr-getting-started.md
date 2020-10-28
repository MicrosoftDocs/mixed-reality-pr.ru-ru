---
title: Начало работы с OpenXR
description: Начните использовать портативный Стандарт API Опенкср на гарнитурах Windows Mixed Reality и HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, Windows Mixed Reality, Опенкср Средства для разработчиков, DirectX, машинный код, собственное приложение, настраиваемое подсистема, по промежуточного слоя, начало работы, 101, предварительный просмотр расширений, версия среды выполнения Опенкср, состояние системы
ms.openlocfilehash: a641512bf36f2d791c009e6dfa83c1f9bd797547
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903140"
---
# <a name="getting-started-with-openxr"></a>Начало работы с OpenXR

Вы можете разрабатывать приложения, используя OpenXR с HoloLens 2 или иммерсивную гарнитуру Windows Mixed Reality с компьютером.  Если у вас нет доступа к гарнитуре, можно использовать эмулятор HoloLens 2 или симулятор Windows Mixed Reality.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Начало работы с Опенкср для HoloLens 2

Чтобы приступить к разработке приложений Опенкср для HoloLens 2:

1. Настройте HoloLens 2 или следуйте инструкциям по [установке последней версии эмулятора hololens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md).  Если на устройстве недавно обновлялась ОС или вы используете последний образ эмулятора, у вас уже есть Опенкср 1,0, готовых к работе.
1. Чтобы убедиться, что у вас установлена последняя версия среды выполнения Опенкср с любыми [расширениями](openxr.md#roadmap) , запустите приложение **магазина** из устройства или эмулятора, откройте меню в правом верхнем углу, щелкните **загрузки и обновления** и щелкните **получить обновления** .  Это гарантирует актуальность среды выполнения Опенкср на HoloLens.  Обратите внимание, что если вы используете эмулятор, образ эмулятора будет сброшен при каждом запуске, поэтому лучше всего убедиться, что у вас установлена [Последняя версия образа эмулятора HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Начало работы с Опенкср для головных телефонов Windows Mixed Reality

Чтобы приступить к разработке приложений Опенкср для впечатляющих головных телефонов Windows Mixed Reality:

1. Убедитесь, что вы используете по крайней мере Windows 10 с обновлением 2019 (1903), что является минимальным требованием для конечных пользователей Windows Mixed Reality запускать приложения Опенкср.  Если вы используете более раннюю версию Windows 10, то можете выполнить обновление с помощью <a href="https://www.microsoft.com/software-download/windows10" target="_blank">помощника по обновлению Windows 10</a>.
2. Настройте гарнитуру Windows Mixed Reality или следуйте инструкциям по [включению симулятора Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md).

Вот и все!  Среда выполнения Опенкср в Windows Mixed Reality устанавливается и автоматически становится активной для всех пользователей Windows Mixed Reality.  Затем Microsoft Store поддерживает обновление среды выполнения.

Если вам когда-либо потребуется снова активировать среду выполнения Опенкср в Windows Mixed Reality, запустите портал смешанной реальности из меню "Пуск" и щелкните "исправить" в баннере в верхней части окна.  Если эта кнопка отсутствует, среда выполнения Опенкср уже активна.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>Получение Средства для разработчиков Опенкср для Windows Mixed Reality

Чтобы испытать среду выполнения Опенкср в Windows Mixed Reality, можно установить <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">опенкср средства для разработчиков для приложения Windows Mixed Reality</a>.  Это приложение содержит демонстрационную сцену, в которой реализованы различные функции Опенкср, а также страница состояния системы, которая содержит основные сведения об активной среде выполнения и текущей гарнитуре.

При использовании эмулятора HoloLens 2 проще всего установить Опенкср Средства для разработчиков для Windows Mixed Reality с помощью [портала устройств Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md), перейдя на страницу "опенкср" и нажав кнопку "установить" в разделе "компоненты разработчика". (это также работает на физическом устройстве HoloLens 2.)

![Опенкср Средства для разработчиков для приложения Windows Mixed Reality](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Создание примера приложения Опенкср

Не забудьте [установить средства](../install-the-tools.md) , необходимые для разработки опенкср, если это еще не сделано.

Проект <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> демонстрирует простой пример OpenXR с двумя файлами проекта Visual Studio — один для классического приложения Win32, а другой для приложения UWP HoloLens 2.  Так как решение содержит проект HoloLens UWP, для его полного открытия вам потребуется [Рабочая нагрузка "разработка универсальная платформа Windows](../install-the-tools.md#installation-checklist) ", установленная в Visual Studio.

Обратите внимание, что хотя файлы проекта Win32 и UWP являются отдельными из-за различий в упаковке и развертывании, код приложения внутри каждого проекта практически одинаков.

После создания рабочего стола Win32 Опенкср. EXE, вы можете использовать его с головной гарнитурой VR на любой платформе Desktop VR, которая поддерживает Опенкср, будь то гарнитура Windows Mixed Reality или любая другая гарнитура.

После создания пакета приложения UWP Опенкср можно [развернуть этот пакет](../platform-capabilities-and-apis/using-visual-studio.md) на устройстве hololens 2 или в эмуляторе hololens 2.

## <a name="learning-the-openxr-api"></a>Изучение API Опенкср

Обзор API Опенкср см. в 60-минутном видео, посвященном коду примера <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">басикксрапп</a> в Visual Studio.  В видео показано, как каждый из основных компонентов API Опенкср можно использовать в собственном механизме, а также демонстрирует некоторые приложения, созданные на Опенкср сегодня.
>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>Интеграция загрузчика Опенкср в проект

Чтобы приступить к работе с Опенкср в существующем проекте, необходимо включить загрузчик Опенкср.  Загрузчик обнаруживает активную среду выполнения Опенкср на устройстве и предоставляет доступ к основным функциям и функциям расширения, которые она реализует.

Вы можете либо [ссылаться на официальный пакет NuGet опенкср](#reference-official-openxr-nuget-package) из проекта Visual Studio, либо [включить официальный источник опенкср Loader](#include-official-openxr-loader-source)  из репозитория кхронос GitHub.  Любой из этих подходов предоставит вам доступ к основным функциям Опенкср 1,0, а также опубликованным `KHR` `EXT` и `MSFT` расширениям.

Если вы хотите поэкспериментировать с `MSFT_preview` расширениями, вы можете [скопировать их в опенкср Preview](#using-preview-extensions) из репозитория GitHub смешанной реальности.

### <a name="reference-official-openxr-nuget-package"></a>Ссылка на официальный пакет NuGet Опенкср

<a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank">Пакет NuGet **Опенкср. Loader**</a> — это самый простой способ ссылки на предварительно созданный загрузчик опенкср. DLL в решении Visual Studio C++.  Это обеспечит доступ к основным функциям Опенкср 1,0, а также опубликованным `KHR` `EXT` и `MSFT` расширениям.

Чтобы добавить ссылку на пакет NuGet Опенкср. Loader в решение Visual Studio C++, сделайте следующее:
1. В **Обозреватель решений** щелкните правой кнопкой мыши проект, который будет использовать опенкср, и выберите пункт **Управление пакетами NuGet...** .
1. Перейдите на вкладку **Обзор** и выполните поиск **опенкср. Loader** .
1. Выберите пакет **опенкср. Loader** и щелкните установить в области сведений справа.
1. Нажмите кнопку ОК, чтобы принять изменения в проекте.
1. Добавьте `#include <openxr/openxr.h>` в исходный файл, чтобы начать использовать API опенкср.

Чтобы увидеть пример API Опенкср в действии, ознакомьтесь с примером приложения <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">басикксрапп</a> .

### <a name="include-official-openxr-loader-source"></a>Включить официальный источник загрузчика Опенкср

Значение, если необходимо самостоятельно создать загрузчик, например, чтобы избежать дополнительного загрузчика. DLL, вы можете извлечь официальные источники загрузчика Кхронос Опенкср в проект.  Это обеспечит доступ к основным функциям Опенкср 1,0, а также опубликованным `KHR` `EXT` и `MSFT` расширениям.

Чтобы начать работу, следуйте инструкциям в <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">репозитории Кхронос опенкср-SDK на сайте GitHub</a>.  Проект настроен для сборки с помощью CMak. Если вы используете MSBuild, необходимо скопировать код в свой проект.

## <a name="using-preview-extensions"></a>Использование расширений для предварительного просмотра

`MSFT_preview`Расширения, перечисленные в схеме [расширения](openxr.md#roadmap) , являются экспериментальными расширениями поставщиков, которые можно просмотреть для сбора отзывов.  Эти расширения предназначены только для устройств разработчика и будут удалены при поставке настоящего расширения.

Если вы заинтересованы в ознакомлении с доступными `MSFT_preview` расширениями, выполните следующие действия, чтобы обновить проект:
1. Выполните любой из описанных выше подходов, чтобы интегрировать загрузчик Опенкср в проект.
1. Замените стандартные заголовки Опенкср в проекте на <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">заголовки предварительной версии из репозитория Опенкср смешанной реальности на сайте GitHub</a>.

Чтобы активировать поддержку расширенной версии на целевом компьютере HoloLens 2 или Desktop, выполните следующие действия.
  1. Чтобы убедиться, что у вас установлена последняя версия среды выполнения Опенкср с любыми [расширениями](openxr.md#roadmap) , запустите приложение **магазина** на целевом устройстве или в эмуляторе, откройте меню в правом верхнем углу, щелкните **загрузки и обновления** и щелкните **получить обновления** .
  1. Установите <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">средства для разработчиков опенкср для приложения Windows Mixed Reality</a> из Microsoft Store на целевое устройство и запустите его.
  1. Перейдите на вкладку **Параметры разработчика** и включите параметр **использовать последнюю предварительную версию среды выполнения опенкср** .  Это позволит среде выполнения предварительной версии на устройстве с активированными расширениями предварительного просмотра.
     ![Опенкср Средства для разработчиков для вкладки параметров разработчика приложения Windows Mixed Reality](images/mixed-reality-openxr-developer-tools-settings.png)
  1. Убедитесь, что **версия среды выполнения** , отображаемая на вкладке **состояние системы** [средства для разработчиков опенкср для Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) , теперь соответствует требуемой версии расширений предварительного просмотра, которые вы планируете использовать.  Если это так, вы увидите расширение в списке **расширений** .  Обратите внимание, что после того, как стабильное расширение станет доступным, его предварительное расширение будет удалено.<br />
     ![Опенкср Средства для разработчиков для вкладки "состояние системы приложений Windows Mixed Reality"](images/mixed-reality-openxr-developer-tools-status.png)

Документацию по этим расширениям и примеры использования этих расширений см. в <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">репозитории Опенкср смешанной реальности</a> .

## <a name="troubleshooting"></a>Устранение неполадок

Если у вас возникли проблемы с Опенксрной разработкой, ознакомьтесь с [советами по устранению неполадок](openxr-troubleshooting.md).