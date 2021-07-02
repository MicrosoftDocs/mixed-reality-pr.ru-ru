---
title: Пространственные аудио учебники — 1. Добавление пространственного звука в проект
description: добавьте подключаемый модуль Microsoft спатиализер в проект Unity, чтобы получить доступ к разгрузки HoloLens 2 хртф оборудования.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, unity, учебник, hololens2, пространственный аудио, мртк, набор средств для смешанной реальности, UWP, Windows 10, хртф, функция передачи, связанная с head, переглагол, Microsoft спатиализер
ms.openlocfilehash: a61e709f24c2162bc6e6e1248de658128674d49e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175375"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Добавление пространственного звука в проект Unity

## <a name="overview"></a>Обзор

Добро пожаловать в учебник по пространственному аудио для Unity в HoloLens2. в этой серии руководств вы узнаете, как использовать разгрузку функций передачи, связанных с head (хртф), в HoloLens 2 и как включить пересылку при использовании разгрузки хртф.

в [репозитории Microsoft спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity) есть завершенный проект Unity этой последовательности руководств.

Сведения о том, что означает спатиализеие звуков с помощью технологий пространственности на основе ХРТФ и рекомендации по их полезности, см. в статье о [проектировании пространственных звуков](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>Что такое разгрузка ХРТФ?

Для обработки звука с использованием алгоритмов на основе ХРТФ требуется большой объем специализированных вычислений. HoloLens 2 включает выделенное оборудование, которое можно использовать, чтобы избежать перегрузки процессора приложений, что позволяет «разгружать» обработку алгоритмов на основе хртф.  Подключаемый модуль Microsoft спатиализер предоставляет приложению простой способ воспользоваться преимуществами выделенного оборудования ХРТФ, чтобы приложение могла использовать больше процессоров приложений для операций, отличных от пространственного звука.

## <a name="objectives"></a>Задачи

* Импорт и Включение подключаемого модуля Microsoft спатиализер
* Включение пространственного звука на рабочей станции разработчика

## <a name="prerequisites"></a>Предварительные условия

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).
* Базовые навыки работы с C#.
* Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">центр unity</a> с unity 2020/2019 LTS, подключенный, и добавлен модуль поддержки универсальная платформа Windows сборки

Прежде чем продолжить, мы **настоятельно рекомендуем** завершить серию руководств по [началу](mr-learning-base-01.md) работы или выполнить некоторые базовые опыт работы с Unity и мртк.

> [!Important]
> эта серия руководств поддерживает поддержку unity 2020 LTS (в настоящее время 2020.3. x), если используется подключаемый модуль Open XR или Windows XR, а также Unity 2019 LTS (в настоящее время 2019.4. x), если используется устаревший подключаемый модуль WSA или Windows XR. Это заменяет все требования к версии Unity, указанные выше.

## <a name="creating-and-preparing-the-unity-project"></a>Создание и подготовка проекта Unity

В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.

Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:

1. [Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.
2. [Переключение платформы сборки.](mr-learning-base-02.md#configuring-the-unity-project)
3. [Импорт требуемых ресурсов TextMeshPro.](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [импорт набор средств смешанной реальности и настройка проекта Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Создание и настройка сцены](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) и присвойте сцене подходящее имя, например *спатиалаудио*

Затем выполните инструкции по [изменению параметра "Показать сведения о пространственной поддержке](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) ", чтобы убедиться, что профиль конфигурации мртк для сцены **DefaultHoloLens2ConfigurationProfile** , и измените параметры экрана для сетки пространственной поддержки на **перекрытия**.

## <a name="adding-microsoft-spatializer-to-the-project"></a>Добавление Microsoft Спатиализер в Project

Скачайте и импортируйте Microsoft Спатиализер  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. спатиалаудио. спатиализер. Unity. 1.0.18. пакет unitypackage </a>

>[!TIP]
> Сведения о том, как правильно импортировать пользовательский пакет Unity, см. в разделе [Импорт ресурсов для руководства](mr-learning-base-04.md#importing-the-tutorial-assets).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Включение подключаемого модуля Microsoft Спатиализер

после импорта microsoft спатиализер в проект unity появится окно **конфигуратора мртк Project** , чтобы выбрать **Microsoft спатиализер**, а  затем нажать кнопку применить, чтобы применить параметр:

![конфигуратор Project мртк](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

вы также можете вручную включить microsoft спатиализер: Open **Edit-> Project Параметры-> Audio**, а также изменить **подключаемый модуль спатиализер** на "Microsoft спатиализер".

![Project Параметры показан подключаемый модуль спатиализер](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a>Включение пространственного звука на рабочей станции

в настольных версиях Windows пространственный звук по умолчанию отключен. Включите его, щелкнув значок тома правой кнопкой мыши на панели задач. чтобы получить лучшее представление о том, что вы услышите на HoloLens 2, выберите **Windows Sonic для наушников пространственный звук — >**.

![Параметры пространственного звука рабочего стола](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> Этот параметр требуется только в том случае, если планируется тестирование проекта в редакторе Unity.

## <a name="congratulations"></a>Поздравляем!

В этом учебнике вы узнаете, как импортировать и включить подключаемый модуль Microsoft Спатиализер, а также включить Пространственный звук на рабочей станции.
В следующем учебнике вы узнаете, как добавить пространственный звук в проект Unity.

> [!div class="nextstepaction"]
> [Следующее руководство: 2. звуковое взаимодействие кнопки Спатиализинг](unity-spatial-audio-ch2.md)
