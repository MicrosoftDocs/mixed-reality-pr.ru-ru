---
title: Пространственные аудио учебники — 1. Добавление пространственного звука в проект
description: Добавьте подключаемый модуль Microsoft Спатиализер в проект Unity, чтобы получить доступ к аппаратной разгрузке HoloLens 2 ХРТФ.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Смешанная реальность, Unity, учебник, hololens2, Пространственный звук, МРТК, набор средств для смешанной реальности, UWP, Windows 10, ХРТФ, функция передачи, связанная с HEAD, переглагол, Microsoft Спатиализер
ms.openlocfilehash: 7ed1355e3c522fcd94a96dd761a8a9ebb01c4c4c
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590046"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Добавление пространственного звука в проект Unity

## <a name="overview"></a>Обзор

Добро пожаловать в учебник по пространственному аудио для Unity в HoloLens2. В этой серии руководств вы узнаете, как использовать разгрузку функций передачи, связанных с HEAD (ХРТФ), в HoloLens 2 и как включить пересылку при использовании разгрузки ХРТФ.

В [репозитории Microsoft Спатиализер GitHub](https://github.com/microsoft/spatialaudio-unity) есть завершенный проект Unity этой последовательности руководств.

Сведения о том, что означает спатиализеие звуков с помощью технологий пространственности на основе ХРТФ и рекомендации по их полезности, см. в статье о [проектировании пространственных звуков](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>Что такое разгрузка ХРТФ?

Для обработки звука с использованием алгоритмов на основе ХРТФ требуется большой объем специализированных вычислений. HoloLens 2 включает выделенное оборудование, которое можно использовать, чтобы избежать перегрузки процессора приложений, таким путем «разложить» обработку алгоритмов на основе ХРТФ.  Подключаемый модуль Microsoft спатиализер предоставляет приложению простой способ воспользоваться преимуществами выделенного оборудования ХРТФ, чтобы приложение могла использовать больше процессоров приложений для операций, отличных от пространственного звука.

## <a name="objectives"></a>Задачи

* Импорт и Включение подключаемого модуля Microsoft спатиализер
* Включение пространственного звука на рабочей станции разработчика

## <a name="prerequisites"></a>Предварительные условия

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](../../install-the-tools.md).
* Базовые навыки работы с C#.
* Устройство HoloLens 2, [настроенное для разработки](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019 LTS и модулем поддержки сборки универсальной платформы Windows.

Прежде чем продолжить, мы **настоятельно рекомендуем** завершить серию руководств по [началу](mr-learning-base-01.md) работы или выполнить некоторые базовые опыт работы с Unity и мртк.

> [!IMPORTANT]
>
> * Рекомендуемая версия Unity для этой серии руководств — Unity 2019 LTS. Это заменяет все требования к версии Unity и рекомендации, указанные выше.

## <a name="creating-and-preparing-the-unity-project"></a>Создание и подготовка проекта Unity

В рамках этого раздела вы создадите новый проект Unity и подготовите его к разработке MRTK.

Для этого сначала выполните инструкции из руководства [Инициализация проекта и первое приложение](mr-learning-base-02.md), за исключением раздела [Разработка приложения для устройства](mr-learning-base-02.md#building-your-application-to-your-hololens-2), то есть следующие действия:

1. [Создание проекта Unity](mr-learning-base-02.md#creating-the-unity-project) и присвоение ему подходящего имени, например *MRTK Tutorials*.

1. [Переключение платформы сборки.](mr-learning-base-02.md#configuring-the-unity-project)

1. [Импорт требуемых ресурсов TextMeshPro.](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Импорт набора средств для смешанной реальности (MRTK).](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Настройка проекта Unity.](mr-learning-base-02.md#configuring-the-unity-project)

1. [Создание и настройка сцены](mr-learning-base-02.md#creating-and-configuring-the-scene) и присвойте сцене подходящее имя, например *спатиалаудио*

Затем выполните инструкции по [изменению параметра "Показать сведения о пространственной поддержке](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) ", чтобы убедиться, что профиль конфигурации мртк для сцены **DefaultHoloLens2ConfigurationProfile** , и измените параметры экрана для сетки пространственной поддержки на **перекрытия**.

## <a name="adding-microsoft-spatializer-to-the-project"></a>Добавление Microsoft Спатиализер в проект

Скачайте и импортируйте Microsoft Спатиализер  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. спатиалаудио. спатиализер. Unity. 1.0.18. пакет unitypackage </a>

>[!TIP]
> Напоминание о том, как импортировать пользовательский пакет Unity, можно найти в разделе Импорт инструкций [учебных материалов](mr-learning-base-04.md#importing-the-tutorial-assets) .

## <a name="enable-the-microsoft-spatializer-plugin"></a>Включение подключаемого модуля Microsoft Спатиализер

После импорта **Microsoft спатиализер** необходимо включить его. Откройте **> параметры проекта-> аудио** и измените **подключаемый модуль Спатиализер** на "Microsoft спатиализер".

![Параметры проекта, отображающие подключаемый модуль спатиализер](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Включение пространственного звука на рабочей станции

В настольных версиях Windows Пространственный звук по умолчанию отключен. Включите его, щелкнув значок тома правой кнопкой мыши на панели задач. Чтобы получить лучшее представление о том, что вы услышите в HoloLens 2, выберите **Пространственный звук — > Windows Sonic для наушников**.

![Параметры пространственного звука рабочего стола](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> Этот параметр требуется только в том случае, если планируется тестирование проекта в редакторе Unity.

## <a name="congratulations"></a>Поздравляем!

В этом учебнике вы узнаете, как импортировать и включить подключаемый модуль Microsoft Спатиализер, а также включить Пространственный звук на рабочей станции.
В следующем учебнике вы узнаете, как добавить пространственный звук в проект Unity.

> [!div class="nextstepaction"]
> [Следующее руководство: 2. звуковое взаимодействие кнопки Спатиализинг](unity-spatial-audio-ch2.md)
