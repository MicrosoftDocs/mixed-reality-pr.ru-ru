---
title: Использование подключаемого модуля Опенкср в смешанной реальности для Unity
description: Узнайте, как включить подключаемый модуль Опенкср в смешанной реальности для проектов Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: опенкср, Unity, hololens, hololens 2, Mixed Reality, МРТК, набор средств для смешанной реальности, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы
ms.openlocfilehash: 1adfb979cfc22be5da18ed990c9db55e6bad97f3
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238136"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Использование подключаемого модуля Опенкср в смешанной реальности для Unity

Начиная с Unity версии 2020,2, пакет подключаемого модуля Опенкср Microsoft Mixed Reality доступен с помощью диспетчера пакетов Unity (УПМ).

## <a name="prerequisites"></a>предварительные требования

* Unity 2020,2 или более поздней версии
* Подключаемый модуль Unity Опенкср 0.1.2 или более поздней версии
* Visual Studio 2019 или более поздней версии
* Установка поддержки платформы **UWP** в Unity для приложений HoloLens 2

> [!NOTE]
> Если вы создаете приложения VR на компьютере с Windows, подключаемый модуль Опенкср в смешанной реальности не обязательно требуется. Однако необходимо установить подключаемый модуль, если вы настраиваете сопоставление контроллера для контроллеров HP reverbа G2 или создаете приложения, которые работают на гарнитурах HoloLens 2 и VR.

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a>Установка Опенкср с помощью средства "функция смешанной реальности"

Установите подключаемый модуль Опенкср с помощью нового приложения средства "функция смешанной реальности". Следуйте [инструкциям по установке и использованию](welcome-to-mr-feature-tool.md) и выберите пакет **подключаемого модуля Опенкср смешанной реальности** в категории "набор средств смешанной реальности":

![Окно пакетов инструмента "функция смешанной реальности" с выделенным подключаемым модулем Open XR](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a>Настройка управления подключаемым модулем XR для Опенкср

Чтобы задать Опенкср в качестве среды выполнения в Unity, сделайте следующее:

1. В редакторе Unity перейдите к **изменению > параметры проекта**
2. В списке параметров выберите **Управление подключаемым модулем XR** .
3. Установите флажки **инициализировать XR при запуске** и **опенкср (Предварительная версия)** .
4. Если нацеливание на HoloLens 2, убедитесь, что вы находитесь на платформе UWP, и выберите **набор функций Microsoft HoloLens** .

![Снимок экрана: панель "Параметры проекта", открытая в редакторе Unity с выделенным подключаемым модулем управления XR](images/openxr-img-05.png)

> [!IMPORTANT]
> Если рядом с **подключаемым модулем опенкср (Предварительная версия)** отображается красный значок предупреждения, щелкните значок и выберите **исправить все** перед продолжением. Для вступления изменений в силу может потребоваться перезапустить редактор Unity.

![Снимок экрана: окно проверки проекта Опенкср](images/openxr-img-06.png)

Теперь вы готовы начать разработку с помощью Опенкср в Unity!  Перейдите к следующему разделу, чтобы узнать, как использовать примеры Опенкср.

## <a name="optimization"></a>Optimization

Если вы разрабатываете для HoloLens 2, перейдите к **смешанной реальности> опенкср > применить Рекомендуемые параметры проекта для HoloLens 2** , чтобы получить лучшую производительность приложения.

![Снимок экрана: пункт меню "смешанная реальность", Открытый с выбранным Опенкср](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a>Испытайте примеры сцен для Unity

Чтобы использовать один или несколько примеров, установите [арфаундатион 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) из **диспетчера пакетов**:

![Снимок экрана: Диспетчер пакетов Unity открыт в редакторе Unity с выделенным элементом управления AR Foundation](images/openxr-img-09.png)

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

МРТК Unity поддерживает подключаемый модуль Mixed Reality Опенкср, начиная с выпуска 2.5.3.  

1. Снова откройте [средство "функция смешанной реальности](welcome-to-mr-feature-tool.md) " и выберите пакет **подключаемого модуля Опенкср смешанной реальности** в категории поддержка платформы.

<!-- MRTK plugins can be installed from the same scoped registries as you set up when [installing the Mixed Reality OpenXR plugin](#installing-the-mixed-reality-openxr-plugin). You can find more detailed information in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#registering-the-mixed-reality-component-server).

1. Add following packages in your **[projectRoot]/Packages/manifest.json** file:

```json
"dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.3",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.3",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.3",
    …
}
``` -->

2. Перейдите к скрипту компонента набора средств Микседреалити Toolkit в инспекторе и переключитесь в профиль **дефаултопенксрконфигуратионпрофиле** :

![Снимок экрана: переключение конфигурации МРТК в компоненте набора средств Mixed Reality в инспекторе](images/openxr-img-11.png)

### <a name="known-issues"></a>Известные проблемы 

При использовании функции отслеживания вручную добавьте следующую строку в файл **Assets/микседреалититулкит. Generated/link.xml** :

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a>Дальнейшие действия

Теперь, когда проект настроен для Опенкср и имеет доступ к примерам, ознакомьтесь с [возможностями](openxr-supported-features.md) , которые в настоящее время поддерживаются в нашем подключаемом модуле опенкср.

## <a name="have-feedback"></a>Хотите оставить отзыв?

Опенкср все еще экспериментально, поэтому мы будем рады получить отзывы, которые помогут улучшить его. Вы найдете нас на [форумах Unity](https://aka.ms/unityforums) , пометив сообщение на форуме с помощью **Microsoft**  +  **опенкср** и **HoloLens 2** или **Windows Mixed Reality**.

## <a name="see-also"></a>См. также

* [Настройка проекта без МРТК](configure-unity-project.md)
* [Рекомендуемые параметры для Unity](recommended-settings-for-unity.md)
* [Рекомендации по производительности для Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
