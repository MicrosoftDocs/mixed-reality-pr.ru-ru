---
title: Пространственные привязки Azure для Android и iOS
description: Пройдите этот курс и узнайте, как развернуть проект Unity с использованием Mixed Reality Toolkit (MRTK) и Пространственных привязок Azure для Android и iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: смешанная реальность, Unity, учебник, HoloLens, Android, iOS, MRTK, Mixed Reality Toolkit, UWP, Пространственные привязки Azure, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 6e9ae377a11d74fd9cdfca7ddb0379542d365e3365bdf07319bc8580b2e87420
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215883"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Пространственные привязки Azure для Android и iOS

В этом руководстве показано, как выполнить сборку проекта на устройствах Android и iOS с помощью пакетов AR Foundation, ARCore XR Plugin и ARKit XR Plugin.

## <a name="objectives"></a>Задачи

* Узнайте, как выполнить сборку проекта на своем устройстве Android с помощью пакетов Unity AR Foundation и ARCore XR Plugin.
* Узнайте, как выполнить сборку проекта на своем устройстве iOS с помощью пакетов Unity AR Foundation и ARKit XR Plugin.

## <a name="installing-inbuilt-unity-packages"></a>Установка встроенных пакетов Unity

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a>Настройка MRTK для камеры AR Foundation

Из этого раздела вы узнаете, как настроить MRTK для развертывания на мобильном устройстве.

В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**. Затем в окне Inspector (Инспектор) перейдите на вкладку **Camera** (Камера), клонируйте профиль камеры и присвойте ему понятное имя, например **AzureSpatialAnchors_ARCameraProfile**:

![Unity с выбранным созданным профилем ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> Сведения о том, как правильно клонировать профили MRTK, см. в статье [Настройка профилей MRTK](mr-learning-base-03.md).

Оставляя выбранной вкладку **Camera** (Камера) в окне инспектора, разверните раздел **Camera Setting Providers** (Поставщики параметров камеры) и щелкните "-", чтобы удалить **Windows Mixed Reality Camera Setting** (Параметры камеры Windows Mixed Reality) или **XR SDK Windows Mixed Reality Camera Setting** (Параметры камеры XR SDK Windows Mixed Reality):

![Профиль ARCameraProfile в Unity с добавленным поставщиком данных ](images/mr-learning-asa/asa-05-section2-step1-2.png)

Затем нажмите кнопку **+ Add Camera Setting Provider** (Добавить поставщика параметров камеры), а затем разверните добавленный раздел **New data provider** (Новый поставщик данных):

![Добавлена камера AR для Android](images/mr-learning-asa/asa-05-section2-step1-3.png)

В раскрывающемся списке **Type** (Тип) измените тип на **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:

![Выбор типа поставщика данных для профиля ARCameraProfile в Unity](images/mr-learning-asa/asa-05-section2-step1-4.png)

Выполните обновление описаний скриптов UnityAR в MRTK, вызвав элемент меню: **Mixed Reality** (Смешанная реальность)  >  **Toolkit** (Набор средств)  >  **Utilities** (Служебные программы)  >  **UnityAR** > Update Scripting Defines (Обновить описания скриптов)

## <a name="building-your-application-to-your-android-device"></a>Создание приложения для устройства Android

Из этого раздела вы узнаете, как настроить проект для сборки и развертывания на устройстве Android.

В меню Unity щелкните **File (Файл)**  > **Build Settings... (Параметры сборки...)** , чтобы открыть окно параметров сборки. Переключите платформу на Android.

![Окно параметров сборки Unity с выбранной платформой Android](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> Сведения о процедуре можно найти в разделе [Переключение платформы сборки](mr-learning-base-02.md#switching-the-build-platform).

Закройте окно Build Settings (Параметры сборки).

В меню Unity выберите **Mixed Reality** (Смешанная реальность)  >  **Toolkit** (Набор средств)  >  **Utilities** (Служебные программы)  >  **Configure Project for MRTK** (Настройка проекта для MRTK), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Убедитесь, что выбраны все параметры, а затем нажмите кнопку **Apply** (Применить), чтобы применить эти параметры.

![Конфигуратор проекта Unity MRTK 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player (Проигрыватель)**  >  **Other Settings (Другие параметры)** . Выберите элемент **Vulkan** и удалите его, щелкнув символ **-** .

![Другие параметры Unity с выбранным API Vulcan](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

В окне Build Settings (Параметры сборки) нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке). Затем с помощью USB-кабеля подключите к компьютеру устройство Android и выберите его в раскрывающемся списке **Run Device** (Запустить устройство).

![Окно параметров сборки в Unity с добавленной сценой и выбранным устройством выполнения](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Если устройство не отображается в раскрывающемся списке Run Device (Запустить устройство), возможно, потребуется нажать кнопку Refresh (Обновить) рядом с раскрывающимся списком.

В окне Build Settings (Параметры сборки) нажмите кнопку **Build And Run** (Сборка и запуск), чтобы открыть окно сборка Android.

Выберите подходящее расположение для хранения сборки, например _D:\MixedRealityLearning\Builds_. Присвойте сборке APK понятное имя, например _MRTKTutorials-AzureSpatialAnchors_. Затем нажмите кнопку **Save** (Сохранить), чтобы запустить процесс сборки.

![Окно параметров сборки Unity с окном сохранения для Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> Если в окне консоли Unity появится сообщение об ошибке, связанной с модулями пакетов SDK, NDK и JDK для Android, необходимо открыть Unity Hub и установить соответствующие модули Android Build Support.

По завершении сборки приложения должны автоматически загрузиться на устройство Android.

## <a name="building-your-application-to-your-ios-device"></a>Создание приложения для устройства iOS

Из этого раздела вы узнаете, как настроить проект для сборки и развертывания на устройстве iOS.

В меню Unity щелкните **File (Файл)**  > **Build Settings... (Параметры сборки...)** , чтобы открыть окно параметров сборки. Переключите платформу на iOS.

![Окно параметров сборки Unity с выбранным вариантом iOS](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> Сведения о процедуре можно найти в разделе [Переключение платформы сборки](mr-learning-base-02.md#switching-the-build-platform).

Закройте окно Build Settings (Параметры сборки).

В меню Unity выберите **Mixed Reality** (Смешанная реальность)  >  **Toolkit** (Набор средств)  >  **Utilities** (Служебные программы)  >  **Configure Project for MRTK** (Настройка проекта для MRTK), чтобы открыть окно **MRTK Project Configurator** (Конфигуратор проектов MRTK). Убедитесь, что выбраны все параметры, а затем нажмите кнопку **Apply** (Применить), чтобы применить эти параметры.

![Окно конфигурации проекта MRTK в Unity для iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

В меню Unity щелкните **Edit** > **Project Settings...** (Правка > Параметры проекта...), чтобы открыть окно параметров проигрывателя, а затем найдите раздел **Player (Проигрыватель)**  >  **Other Settings (Другие параметры)** . Снимите флажок **Strip Engine Code** (Удалить код обработчика), чтобы отключить его.

![Другие параметры Unity с отключенным параметром Strip Engine Code (Удалить код обработчика)](images/mr-learning-asa/asa-05-section4-step1-3.png)

Закройте окно Player Settings (Параметры проигрывателя) и снова откройте окно **Build Settings** (Параметры сборки).

В окне Build Settings (Параметры сборки) нажмите кнопку **Add Open Scenes** (Добавить открытые сцены), чтобы добавить текущую сцену в список **Scenes In Build** (Сцены в сборке).

![Окно параметров сборки Unity с добавленной сценой](images/mr-learning-asa/asa-05-section4-step1-4.png)

В окне Build Settings (Параметры сборки) нажмите кнопку **Build** (Сборка), чтобы открыть окно сборки iOS.

Выберите подходящее расположение для хранения проекта Xcode, например _D:\MixedRealityLearning\Builds_. Создайте папку и присвойте ей понятное имя, например _MRTKTutorials-AzureSpatialAnchors_. Затем нажмите кнопку **Select Folder** (Выбрать папку), чтобы начать сборку.

![Окно параметров сборки Unity с окном сохранения для iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

После сборки выполните инструкции из раздела [Экспорт проект Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project), чтобы научиться развертывать проекты Xcode на устройствах iOS.

## <a name="congratulations"></a>Поздравляем!

Из этого руководства вы узнали, как выполнить сборку проекта на устройствах Android и iOS с помощью пакетов AR Foundation, ARCore XR Plugin и ARKit XR Plugin.
