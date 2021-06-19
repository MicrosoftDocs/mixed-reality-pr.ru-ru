---
title: Настройка конфигурации XR
description: Оставайтесь в курсе последних рекомендаций по конфигурации Unity XR для разработки приложений HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: микседреалититулкит, микседреалититулкит-Unity, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, Unity
ms.openlocfilehash: df7c5039c6cdcfa1e39dc96f0829611dd5209772
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394568"
---
# <a name="setting-up-your-xr-configuration"></a>Настройка конфигурации XR

При запуске нового проекта Unity у вас есть три разных варианта для обработки потребностей XR: 
* Подключаемый модуль Опенкср
* Подключаемый модуль Windows XR
* Устаревший подключаемый модуль XR

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Настройка проекта с помощью МРТК

MRTK для Unity предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий. MRTK версии 2 предназначен для ускорения разработки приложений для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR. Цель проекта — упростить разработку приложений смешанной реальности и вносить вклад в сообщество по мере развития навыков.

> [!div class="nextstepaction"]
> [Ознакомьтесь с нашими руководствами по МРТК](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=winxr)

Дополнительные сведения о функциях см. в [документации по MRTK ](/windows/mixed-reality/mrtk-unity).

### <a name="using-mrtk-with-openxr-support"></a>Использование МРТК с поддержкой Опенкср

Выпуск MRTK-Unity 2,7 обеспечивает лучшую поддержку для подключаемого модуля Опенкср в смешанной реальности.

Снова откройте [средство "функция смешанной реальности](welcome-to-mr-feature-tool.md) ", чтобы установить набор средств Mixed Reality, если вы этого еще не сделали. Поддержка Опенкср находится в пакете **Foundation** .

[Более подробные сведения о переходе на опенкср](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)см. в документации по мртк.

> [!NOTE]
> При обновлении предыдущей версии МРТК, более ранней, чем **2.5.3**, убедитесь, что в файле **Assets/микседреалититулкит. generated/link.xml** указана следующая строка:
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Эта строка будет добавлена по умолчанию, если вы начали работу с МРТК 2.5.4 или более поздней версии.

## <a name="manual-setup-without-mrtk"></a>Настройка вручную без МРТК

Хотя корпорация Майкрософт и сообщество создали средства конвертер, такие как набор средств для [смешанной реальности (мртк)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) , который автоматически настраивает среду ВМР, многие разработчики хотят создавать свои впечатления с нуля.

[!INCLUDE[](includes/xr/manual-setup.md)]
