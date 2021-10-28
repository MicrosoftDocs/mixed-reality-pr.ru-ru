---
title: Приложения и примеры функций смешанной реальности
description: Узнавайте первыми обо всех доступных примерах приложений и функций смешанной реальности Майкрософт для HoloLens.
author: qianw211
ms.author: v-qianwen
ms.date: 10/22/2021
ms.topic: article
keywords: смешанная реальность, unity, руководство, hololens, обучение, примеры, mrtk, режим исследований, hololens 2, qr-коды, webrtc, запись смешанной реальности, удаленное взаимодействие, средства пользовательского интерфейса
ms.localizationpriority: high
ms.openlocfilehash: 415250a69a9c82241cc2bad42e9f3f9a9416a0ad
ms.sourcegitcommit: 4f847aba212e97b1639299ddbe2b1a7b27c60f4d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2021
ms.locfileid: "130204068"
---
# <a name="mixed-reality-feature-samples-and-apps"></a>Приложения и примеры функций смешанной реальности

![Изображение пользователя в HoloLens, который манипулирует голограммой с помощью движений рук](unreal/images/unreal-developer.jpg)

Каждый проект разработки начинается с обзора того, что уже сделали другие разработчики. Смешанная реальность не исключение. Сейчас все наши руководства и примеры приложений встроены в Unity или Unreal. По мере разработки содержимого для других движков и платформ вы сможете находить соответствующие руководства по заголовку в содержании.

* [Примеры использования примеров приложений](#sample-application-case-studies)
* [Примеры возможностей](#feature-samples)

## <a name="sample-application-case-studies"></a>Примеры использования примеров приложений

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>Примеры возможностей

Для каждого сценария разработки, приведенного ниже, доступны примеры функций, которые соответствуют определенным реализациям, описанным в нашей документации. Они поддерживают разные платформы разработки и аппаратные устройства.

| Сценарий | Пример функции | Подсистема | Описание |
| --- | --- | ---- | --- |
| [**Создание базовых сценариев смешанной реальности в Unity**](#build-basic-openxr-scenarios) | [Примеры OpenXR с Unity](#build-basic-openxr-scenarios) | Unity C# | Начало работы с кросс-платформенными средствами разработчиков с использованием последней версии Unity 2020.LTS и подключаемого модуля OpenXR. |
| **Стратегии привязки** | [Локальная привязка](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples#sample-for-anchors-and-anchor-persistence) |  | Сохранение и совместное использование пространственных привязок между сеансами приложений и устройствами. См. статью [Пространственные привязки](/windows/mixed-reality/design/spatial-anchors). |
|    | [Примеры для службы "Пространственные привязки Azure"](https://github.com/Azure/azure-spatial-anchors-samples) |  | Создание приложений смешанной реальности с отслеживанием положения в пространстве с помощью основных возможностей службы [Пространственные привязки Azure](/azure/spatial-anchors/overview). |
| | [QR-коды](#qr-codes) | Unity C# | Обнаружение QR-кодов в среде. |
| [**Совместная работа в смешанной реальности**](#collaboration-in-mixed-reality) | [Удостоверение пользователя](#user-identity) | Unity C# | Настройка устройства HoloLens 2 с помощью учетных данных Azure Active Directory (AAD). |
| | [Примеры WebRTC](#webrtc) | Unity C# | Интеграция пирингового аудио, видео и данных коммуникаций в реальном времени в приложение смешанной реальности. |
| | [Примеры для службы "Пространственные привязки Azure"](https://github.com/Azure/azure-spatial-anchors-samples) |  | Создание приложений смешанной реальности с отслеживанием положения в пространстве с помощью основных возможностей службы [Пространственные привязки Azure](/azure/spatial-anchors/overview). |
| [**Пространственное взаимодействие**](#spatial-interaction---basic-hologram-sample) | [Пример простой голограммы](#spatial-interaction---basic-hologram-sample) | Windows 10 C++ | Отрисовка вращающегося куба в Windows Mixed Reality. |
|  [**Интерпретация сцены или объекта**](#scene-understanding) | [Примеры интерпретации сцены](#scene-understanding) | Unity C# | Помощь в разработке приложений смешанной реальности для разных сред. |
|    | [Примеры для службы "Объектные привязки Azure"](https://github.com/Azure/azure-object-anchors) | Unity C# | Обнаружение объекта в физическом мире с использованием трехмерной модели и оценка его состояния 6DoF с помощью службы [Объектные привязки Azure](/azure/object-anchors/overview). |
| [**Наложения контекстных данных**](#contextual-data-overlays) | [QR-коды](#qr-codes) | Unity C# | Обнаружение QR-кодов в среде. |
| | [Пример средства для отслеживания плаката](#poster-tracker-sample)  | Unity C# | Сопоставление голограммы с реальным объектом. |
| | [Создание цифровых двойников в смешанной реальности](#build-mixed-reality-digital-twins) | Unity C# | Узнайте, как создать приложение смешанной реальности с помощью Azure Digital Twins и Unity, платформы трехмерного содержимого, работающей в режиме реального времени. |
| [**Захват данных камеры**](#camera-captures) | [Пример съемки в смешанной реальности](#holographic-mixed-reality-capture) | Windows 10 C++ | Захватывайте данные смешанной реальности от первого лица в виде фотографии или видео. |
| | [Пример представления Spectator (Наблюдатель)](#spectator-view) | Unity C# | Съемка и отрисовка голограмм с правильным размером и ориентацией. |
| | [Примеры режима исследования](#research-mode) | Windows 10 C++ | Предоставление доступа к основным датчикам на устройстве HoloLens для исследовательских приложений. |
| [**Голографическое удаленное взаимодействие**](#holographic-remoting) | [Holographic Remoting Player](#holographic-remoting) |  Windows 10 C++ | Потоковая передача голографического содержимого с ПК на Microsoft HoloLens в реальном времени по подключению Wi-Fi. |
| | [Примеры для службы "Удаленная отрисовка Azure"](/azure/remote-rendering/samples/sample-model) | Unity C# | Тестирование службы "Удаленная отрисовка Azure" с использованием ресурсов для приведенных здесь примеров данных. |
| **Управление задачами и рекомендации** | [Dynamics 365 Remote Assist;](/dynamics365/mixed-reality/remote-assist/ra-overview) | | Повысьте эффективность совместной работы из разных расположений с помощью Dynamics 365 Remote Assist на устройствах HoloLens, HoloLens 2, Android или iOS. |
| | [Dynamics 365 Guides](/dynamics365/mixed-reality/guides/) | | Помощь операторам в обучении во время работы путем предоставления голографических инструкций в нужном месте и в нужное время. |
| **Голограммы с фиксацией в мировой системе координат** | [Примеры физики с фиксацией в мировой системе координат](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Samples/WorldLockedPhysicsSample.html) | Unity C# | Несколько виртуальных физических взаимодействий на основе поддержки фиксации в мировой системе координат с помощью World Locking Tools. |
| | [Пример закрепления в пространстве](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Samples/SpacePin.html) | Unity C# | Описание работы реального приложения, для которого требуется выполнить привязку крупного объекта или объектов с признаками в реальном мире. Пример с закреплением в пространстве предоставляет упрощенный и более точный обзор этой функции.  |
| | [Пример закрепления лучей](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Samples/RayPins.html) | Unity C# | Демонстрация настройки закрепления в пространстве путем перемещения маркеров объектов вручную с помощью возможностей MRTK. |
| | [Пример использования World Locking Tools со службой "Пространственные привязки Azure"](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Samples/WLT_ASA_Sample.html) | Unity C# | Обеспечение стабильной системы координат, которую можно сохранять между сеансами и передавать на другие устройства в приложении.  Это возможно благодаря сочетанию возможностей World Locking Tools для Unity (WLT) и службы "Пространственные привязки Azure" (ASA). |

### <a name="build-basic-openxr-scenarios"></a>Создание базовых сценариев OpenXR

Если вы еще не знакомы с созданием базовых сценариев смешанной реальности, эти примеры помогут вам начать.

Для разработчиков, работающих с Unity 2020 для создания приложений HoloLens 2 или смешанной реальности, можно использовать подключаемый модуль OpenXR вместо WindowsXR, чтобы улучшить совместимость между платформами. Подключаемый модуль OpenXR для смешанной реальности также хорошо работает с последней версией Mixed Reality Toolkit (2.7.x).

| Справочная статья | Образец | Платформа | Описание | 
| --- | --- | --- | --- |
| [Использование подключаемого модуля OpenXR](./unity/xr-project-setup.md) | [Смешанная реальность OpenXR с примерами Unity](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) | Unity C# | Эти примеры проектов демонстрируют, как создавать приложения Unity для HoloLens 2 или гарнитур смешанной реальности с помощью подключаемого модуля OpenXR для смешанной реальности. <br> <br> Рассматриваются следующие примеры сценариев: <br> <br> <ul> <li> [Использование соединений для отслеживания рук и входных данных сетки в Unity](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples#sample-for-hand-tracking) </li> <li> [Использование привязки и сохранения привязки](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples#sample-for-anchors-and-anchor-persistence) </li> <li> [Использование ARPlaneManager на HoloLens 2](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples#sample-for-arfoundation-compatibility) </li> <li> [Использование ARRaycastManager на HoloLens 2](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples#sample-for-arfoundation-compatibility) </li> <li> [Использование отслеживания глаз на HoloLens 2](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples#sample-for-eye-tracking) </li> <li> [Использование камеры с определяемым местоположением в Unity](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples#sample-for-locatable-camera)  </li> |
| См. [пример файла сведений](https://github.com/jessemcculloch/UnityOpenXRMRTKBase#unityopenxrmrtkbase). | [Базовый проект Unity с MRTK OpenXR](https://github.com/microsoft/UnityOpenXRMRTKBase) | Unity C# | Этот репозиторий содержит проект Unity, настроенный с пакетами Microsoft Mixed Reality Toolkit Foundations и Standard Assets, а также пакетом Microsoft OpenXR Plugin. |
| [Что такое MRTK?](/windows/mixed-reality/mrtk-unity/) | [Использование Unity 2020.3 и MRTK 2.7.2](https://github.com/microsoft/MixedRealityToolkit-Unity#example-scenes) | Unity C# | MRTK-Unity — это проект, управляемый Майкрософт, который предоставляет набор компонентов и функций для ускорения кросс-платформенной разработки приложений смешанной реальности в Unity. |
| См. [пример файла сведений](https://github.com/maluoi/openxr-explorer#openxr-explorer). | [OpenXR Explorer](https://github.com/maluoi/openxr-explorer#msdynttrid=udu2MjGd1z293SGMmgAul0BalrUKvy4iwBnBrc3lEn4) | C++, Windows, Linux, OpenXR | OpenXR Explorer — это удобное средство отладки для разработчиков OpenXR. Оно позволяет легко переключаться между средами выполнения OpenXR, отображает список поддерживаемых расширений среды выполнения и дает возможность изучать общие свойства и перечисления с прямыми ссылками на важные данные спецификации OpenXR. |
| [Что такое OpenXR?](../develop/native/openxr.md#what-is-openxr) | [Примеры OpenXR для разработчиков смешанной реальности](https://github.com/microsoft/OpenXR-MixedReality) | C++ | В этих примерах OpenXR используются C++17 и Direct3D 11. Один и тот же исходный код работает в приложениях UWP, выполняющихся на устройствах HoloLens 2, и приложениях Win32, выполняющихся на рабочем столе Windows с иммерсивной гарнитурой Windows Mixed Reality. |

### <a name="collaboration-in-mixed-reality"></a>Совместная работа в смешанной реальности

В смешанной реальности все участники могут виртуально общаться, обмениваться мнениями и совместно работать.  В приведенных здесь примерах демонстрируются некоторые функции, которые поддерживают такую совместную работу.

#### <a name="user-identity"></a>Удостоверение пользователя 

Этот пример настраивает ваше устройство HoloLens 2 с использованием учетных данных Azure Active Directory (AAD), а затем настраивает устройство для входа по сетчатке глаза.

| Справочная статья | Образец |
| --- | --- |
| [Общий обзор платформы удостоверений Майкрософт](/azure/active-directory/develop/v2-overview) | [Вход через AAD на HoloLens 2](https://github.com/peted70/aad-hololens) |

#### <a name="webrtc"></a>WebRTC

Проект MixedReality-WebRTC — это набор компонентов, которые помогают разработчикам приложений смешанной реальности интегрировать в приложения пиринговое аудио, видео и данные коммуникаций в реальном времени. Компоненты WebRTC основаны на протоколе WebRTC для коммуникаций в реальном времени (RTC), которые поддерживаются большинством современных веб-браузеров.

| Справочная статья | Образец |
| --- | --- |
| [WebRTC](https://microsoft.github.io/MixedReality-WebRTC) | [Примеры приложений WebRTC](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="spatial-interaction---basic-hologram-sample"></a>Пространственное взаимодействие — пример базовой голограммы

Этот пример выполняется в Windows Mixed Reality и отрисовывает вращающийся куб. Вы можете взаимодействовать с кубом, помещая его в новое положение, в том числе с использованием разных методов ввода. Этот пример работает на компьютерах с подключенной гарнитурой, а также на Microsoft HoloLens.

| Справочная статья | Образец |
| --- | --- |
| См. [пример файла сведений](https://github.com/microsoft/Windows-universal-samples/tree/main/Samples/BasicHologram#basic-hologram-sample). | [Универсальные примеры для Windows — базовая голограмма](https://github.com/microsoft/Windows-universal-samples/tree/main/Samples/BasicHologram) |

### <a name="scene-understanding"></a>Интерпретация сцены

Интерпретация схемы предоставляет разработчикам смешанной реальности структурированное и общее представление среды.  Интерпретация сцены предназначена для разработки интуитивно простых приложений для определенных сред, объединяя возможности существующих сред выполнения смешанной реальности. Такие среды выполнения являются очень точными, но менее структурированными средами выполнения пространственных сопоставлений и новыми средами выполнения на основе ИИ.

| Справочная статья | Образец | Платформа | Описание |
| --- | --- | --- | --- |
| [Интерпретация сцены](../design/scene-understanding.md) | [Примеры интерпретации сцены смешанной реальности (пакет SDK для интерпретации сцены)](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) | Unity C# и пакет SDK для интерпретации сцены | Пример приложения на основе Unity, демонстрирующий интерпретацию сцены в HoloLens 2. |
| [Наблюдатель интерпретации сцены (MRTK)](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) | [Пример интерпретации сцены (MRTK + пакет SDK для интерпретации сцены)](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity) |Unity C#, MRTK + пакет SDK для интерпретации сцены | Пример MRTK с пакетом SDK для интерпретации сцены. |

### <a name="contextual-data-overlays"></a>Наложения контекстных данных

Контекстные данные — это фоновая информация, которая позволяет получить более полное представление о событии, лице или предмете.  В дополненной реальности такую информацию можно отображать и точно сопоставлять с физическими объектами для предоставления полезных сведений, инструкций, служебных записей и других важных данных.

#### <a name="qr-codes"></a>QR-коды

HoloLens 2 может обнаруживать QR-коды в среде вокруг гарнитуры, определяя систему координат в реальном расположении каждого кода.

| Справочная статья | Образец |
| --- | --- |
| [QR-коды](advanced-concepts/qr-code-tracking-overview.md) | [Отслеживание QR-кодов в Unity](https://github.com/microsoft/MixedReality-QRCode-Sample) |

#### <a name="poster-tracker-sample"></a>Пример средства для отслеживания плаката

Часто бывает полезно привязать голограмму к объекту реального мира или привязать несколько устройств HoloLens к общему набору мировых координат, чтобы все участники видели одни голограммы в одном расположении. Например, в сцене Unity вы можете добавить "плакат" и привязать к нему свою сцену (например, игровую доску), а затем добавить голограммы к нему или вокруг него. Затем вы можете распечатать плакат, положить его на стол и запустить средство калибровки или привязки, которое переместит голографическую версию плаката таким образом, чтобы он совпал с физической версией плаката. Это приведет к перемещению всех связанных голограмм на правильное расположение.

| Справочная статья | Образец |
| --- | --- |
| См. [пример файла сведений](https://github.com/microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample#postercalibrationsample). | [Пример калибровки плаката](https://github.com/microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample) |

#### <a name="build-mixed-reality-digital-twins"></a>Создание цифровых двойников в смешанной реальности

В этой примере описывается, как создать приложение смешанной реальности для HoloLens 2 с помощью Azure Digital Twins и Unity, платформы трехмерного содержимого, работающей в режиме реального времени. 

| Справочная статья | Образец |
| --- | --- |
| [Полная схема обучения](/learn/paths/build-mixed-reality-azure-digital-twins-unity/) | [Создание цифровых двойников для смешанной реальности с помощью Azure Digital Twins и Unity](https://github.com/MicrosoftDocs/mslearn-mr-adt-in-unity) |


### <a name="camera-captures"></a>Захват данных с камеры

Неструктурированные данные с датчиков среды, которые захватывает устройство смешанной реальности, преобразуются в абстрактные или голографические представления физического мира вокруг нас. 

#### <a name="holographic-mixed-reality-capture"></a>Запись голограмм с помощью приложения "Съемка смешанной реальности"

Съемка смешанной реальности позволяет в реальном времени записывать процесс взаимодействия пользователя с реальностью, объединяющей реальный и цифровой миры, в формате фото и видео, а также в реальном времени обмениваться этими данными с другими пользователями.

| Справочная статья | Образец |
| --- | --- |
| [Съемка смешанной реальности](advanced-concepts/mixed-reality-capture-overview.md) | [Примеры для приложения "Съемка смешанной реальности"](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

#### <a name="spectator-view"></a>Зрительское представление

Представление Spectator (Наблюдатель) отрисовывает голограммы из Unity над цветовой рамкой с карты захвата. В этом примере используются данные калибровки из приложения калибровки для отрисовки голограмм с правильным размером и ориентацией.  

| Справочная статья | Пример приложения |
| --- | --- |
| См. [пример настройки](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md#spectator-view-mobile-setup). | [Настройка представления Spectator для мобильного устройства](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md#spectator-view-mobile-setup) |

#### <a name="research-mode"></a>Режим исследования

Режим исследования реализован в первом поколении HoloLens для обеспечения доступа к ключевым датчикам на устройстве специально для исследовательских приложений, которые не предназначены для развертывания. Примеры приложений, приведенные ниже, демонстрируют возможности получения доступа к потокам и их записи в режиме исследования, а также использования [встроенных и внешних объектов](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).

| Справочная статья | Пример приложения |
| --- | --- |
| [Режим исследования](advanced-concepts/research-mode.md) | [HoloLens (1-го поколения)](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [Режим исследования](advanced-concepts/research-mode.md) | [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |


### <a name="holographic-remoting"></a>Голографическое удаленное взаимодействие

Holographic Remoting Player — это дополнительное приложение, которое подключается к приложениям и играм для ПК с поддержкой голографического удаленного взаимодействия. Голографическое удаленное взаимодействие в реальном времени отправляет поток голографического содержимого с компьтера на Microsoft HoloLens по Wi-Fi. Оно поддерживается в HoloLens (1-го поколения) и HoloLens 2.


| Справочная статья | Образец |
| --- | --- |
| [Голографическое удаленное взаимодействие](advanced-concepts/holographic-remoting-player.md) | [Примеры голографического удаленного взаимодействия](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |