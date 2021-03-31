---
title: Использование подключаемого модуля Опенкср в смешанной реальности для Unity
description: Узнайте, как включить подключаемый модуль Опенкср в смешанной реальности для проектов Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы
ms.openlocfilehash: 6e300c6117e04e2a49b060bcd7a6d268204f14da
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "105937479"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Использование подключаемого модуля Опенкср в смешанной реальности для Unity

Начиная с Unity версии 2020,2, пакет подключаемого модуля Опенкср Microsoft Mixed Reality доступен с помощью диспетчера пакетов Unity (УПМ).

## <a name="prerequisites"></a>Предварительные требования

* Unity 2020,3 LTS или более поздней версии
* Подключаемый модуль Unity Опенкср 1.0.3 или более поздней версии
* Visual Studio 2019 или более поздней версии
* Установка поддержки платформы **UWP** в Unity для приложений HoloLens 2

> [!NOTE]
> Если вы создаете приложения VR на компьютере с Windows, подключаемый модуль Опенкср в смешанной реальности не обязательно требуется. Однако необходимо установить подключаемый модуль, если вы настраиваете сопоставление контроллера для контроллеров HP reverbа G2 или создаете приложения, которые работают на гарнитурах HoloLens 2 и VR.

<!-- ## Setting up your project with MRTK

MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions. MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform. The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.

> [!div class="nextstepaction"]
> [Set up your project using MRTK](tutorials/mr-learning-base-01.md)

Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details. -->

## <a name="manual-setup-without-mrtk"></a>Настройка вручную без МРТК

Установите подключаемый модуль Опенкср с помощью нового приложения средства "функция смешанной реальности". Следуйте [инструкциям по установке и использованию](welcome-to-mr-feature-tool.md) и выберите пакет **подключаемого модуля Опенкср смешанной реальности** в категории "набор средств смешанной реальности":

![Окно пакетов инструмента "функция смешанной реальности" с выделенным подключаемым модулем Open XR](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>Настройка целевого объекта сборки

Если вы нацелены на Desktop VR, мы рекомендуем использовать отдельную платформу ПК, выбранную по умолчанию, в новом проекте Unity:

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным компьютером, Mac & изолированной платформой](images/wmr-config-img-3.png)

Если вы намерены ориентироваться на HoloLens 2, необходимо переключиться на универсальная платформа Windows:

1.  Выберите **файл > параметры сборки...**
2.  Выберите **универсальная платформа Windows** в списке Платформа и выберите **параметр платформа** .
3.  Установка **архитектуры** **ARM 64**
4.  Задать **целевое устройство** в **HoloLens**
5.  Задать для **типа сборки** **D3D**
6.  Установить **последнюю версию** **пакета SDK для UWP**
7.  Задать для **конфигурации сборки** значение **Release** , так как имеются известные проблемы с производительностью при отладке

![Снимок экрана: окно "параметры сборки" открыто в редакторе Unity с выделенным универсальная платформа Windows](images/wmr-config-img-4.png)

После настройки платформы необходимо разрешить Unity создавать [иммерсивное представление](../../design/app-views.md) вместо 2D-представления при экспорте.

## <a name="configuring-xr-plugin-management-for-openxr"></a>Настройка управления подключаемым модулем XR для Опенкср

Чтобы задать Опенкср в качестве среды выполнения в Unity, сделайте следующее:

1. В редакторе Unity перейдите к **изменению > параметры проекта**
2. В списке параметров выберите **Управление подключаемым модулем XR** .
3. Установите флажки **инициализировать XR при запуске** и **опенкср**
4. Если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP, и выберите **набор функций Microsoft HoloLens** .

![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-img-05.png)

## <a name="optimization"></a>Optimization

Если вы разрабатываете для HoloLens 2, перейдите к **смешанной реальности> опенкср > применить Рекомендуемые параметры проекта для HoloLens 2** , чтобы получить лучшую производительность приложения.

![Снимок экрана: пункт меню "смешанная реальность", Открытый с выбранным Опенкср](images/openxr-img-08.png)

> [!IMPORTANT]
> Если рядом с **подключаемым модулем опенкср (Предварительная версия)** отображается красный значок предупреждения, щелкните значок и выберите **исправить все** перед продолжением. Для вступления изменений в силу может потребоваться перезапустить редактор Unity.

![Снимок экрана: окно проверки проекта Опенкср](images/openxr-img-06.png)

Теперь вы готовы начать разработку с помощью Опенкср в Unity!  Перейдите к следующему разделу, чтобы узнать, как использовать примеры Опенкср.

## <a name="try-out-the-unity-sample-scenes"></a>Испытайте примеры сцен для Unity

### <a name="hololens-2-samples"></a>Примеры HoloLens 2

1. В редакторе Unity перейдите к **окну > диспетчер пакетов** .
2. В списке пакетов выберите **подключаемый модуль Опенкср Mixed Reality** .
3. Выберите пример в списке **образцы** и нажмите кнопку **Импорт** .

![Снимок экрана: Диспетчер пакетов Unity открыт в редакторе Unity с выбранным подключаемым модулем смешанной реальности Опенкср и кнопка импорта выборки](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> При обновлении пакета Unity предоставляет возможность обновления импортированных образцов.  При обновлении импортированного образца будут перезаписаны все изменения, внесенные в образец и связанные ресурсы.

## <a name="using-mrtk-with-openxr-support"></a>Использование МРТК с поддержкой Опенкср

MRTK-Unity поддерживает подключаемый модуль Mixed Reality Опенкср, начиная с выпуска 2.5.3.

1. Снова откройте [средство "функция смешанной реальности](welcome-to-mr-feature-tool.md) ", чтобы установить набор средств Mixed Reality, если вы этого еще не сделали. Поддержка Опенкср находится в пакете **Foundation** .
2. Перейдите к скрипту компонента набора средств Микседреалити Toolkit в инспекторе и переключитесь в профиль **дефаултопенксрконфигуратионпрофиле** :

    ![Снимок экрана: переключение конфигурации МРТК в компоненте набора средств Mixed Reality в инспекторе](images/openxr-img-11.png)

    1. [Более подробные сведения о переходе на опенкср](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)см. в документации по мртк.

> [!NOTE]
> При обновлении предыдущей версии МРТК убедитесь, что в файле **Assets/микседреалититулкит. Generated/link.xml** указана следующая строка:
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Эта строка будет добавлена по умолчанию, если вы начали работу с МРТК 2.5.4 или более поздней версии.

## <a name="next-steps"></a>Дальнейшие действия

Теперь, когда проект настроен для Опенкср и имеет доступ к примерам, ознакомьтесь с [возможностями](openxr-supported-features.md) , которые в настоящее время поддерживаются в нашем подключаемом модуле опенкср.

## <a name="have-feedback"></a>Хотите оставить отзыв?

Опенкср все еще экспериментально, поэтому мы будем рады получить отзывы, которые помогут улучшить его. Вы найдете нас на [форумах Unity](https://aka.ms/unityforums) , пометив сообщение на форуме с помощью **Microsoft**  +  **опенкср** и **HoloLens 2** или **Windows Mixed Reality**.

## <a name="see-also"></a>См. также раздел

* [Настройка проекта без МРТК](configure-unity-project.md)
* [Рекомендуемые параметры для Unity](recommended-settings-for-unity.md)
* [Рекомендации по производительности для Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
