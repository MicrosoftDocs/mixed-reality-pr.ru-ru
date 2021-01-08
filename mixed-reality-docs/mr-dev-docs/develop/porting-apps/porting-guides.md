---
title: Перенос приложений VR в Windows Mixed Reality
description: Пошаговое руководство, объясняющее, как перенести существующее иммерсивное приложение на Windows Mixed Reality.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: порт, Unity, Нереал, по промежуточного слоя, ядро, UWP, Win32, перенос, 1-й Gen, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, миграция, Windows 10, сопоставление входных данных
ms.openlocfilehash: f1cb7cd96ee1d6e32c9ef1f8d3e0e1b2654e0a79
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009874"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Перенос приложений VR в Windows Mixed Reality

Windows 10 включает поддержку для впечатляющих и holographic головных телефонов. Если вы создали содержимое для других устройств, таких как Окулус Рифт или HTC Naopak, они имеют зависимости от библиотек, существующих над API платформы операционной системы. Применяя существующие приложения Win32 Unity версии к Windows Mixed Reality, предполагается изменение целевой платформы на использование пакетов SDK VR, зависящих от поставщика, к API-интерфейсам версии Unity Cross-Vendor.

## <a name="porting-requirements"></a>Требования к переносу

На высоком уровне следующие шаги участвуют в переносе существующего содержимого:
1. **Убедитесь, что на компьютере работает обновление Windows 10 Creators Update (16299).** Мы больше не рекомендуем получать предварительные сборки от программы предварительной оценки, так как эти сборки не будут самыми стабильными при разработке смешанной реальности.
2. **Обновите версию графического или игрового модуля до последней версии.** Обработчики игр должны поддерживать версию пакета SDK для Windows 10 10.0.15063.0 (выпущена в апреле 2017) или более поздней версии.
3. **Обновите любое промежуточное по, подключаемые модули или компоненты.** Если приложение содержит какие-либо компоненты, рекомендуется выполнить обновление до последней версии.
4. **Удалите зависимости от повторяющихся пакетов SDK**. В зависимости от устройства, для которого предназначено содержимое, необходимо удалить или условно откомпилировать этот пакет SDK, чтобы вместо этого можно было ориентироваться на интерфейсы API Windows. Пример такого сценария — Стеамвр.
5. **Работа с проблемами сборки.** На этом этапе упражнение по переносу зависит от вашего приложения, подсистемы и зависимостей компонентов.

## <a name="common-porting-steps"></a>Общие этапы переноса

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Убедитесь, что у вас есть правильное оборудование для разработки

На странице [Установка средств](../install-the-tools.md#immersive-vr-headset-requirements) перечислены рекомендуемые средства разработки.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. обновление до последнего рейса Windows 10

Платформа Windows Mixed Reality все еще находится под активной разработкой. Мы рекомендуем [присоединиться к программе предварительной](https://insider.windows.com/) оценки Windows, чтобы получить доступ к рейсу о быстром выпуске Windows.
1. Установка [обновления Windows 10 для дизайнеров](https://www.microsoft.com/software-download/windows10)
2. [Присоединяйтесь](https://insider.windows.com/) к программе предварительной оценки Windows.
3. Включить [режим разработчика](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. Переключиться на [быстрые авиарейсы по Windows](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) с помощью **параметров > Update & Security Section**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. обновление до последней сборки Visual Studio
* Если вы используете Visual Studio, обновитесь до последней сборки
* См. раздел [Установка средств на](../install-the-tools.md#installation-checklist) странице Visual Studio 2019.

### <a name="4-choose-the-correct-adapter"></a>4. Выберите правильный адаптер.
* В таких системах, как записные книжки с двумя графическими процессорами, следует [выбрать правильный адаптер](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Это относится к Unity и собственным приложениям DirectX, где ID3D11Device создается явно или неявно (Media Foundation) для своей функциональности.

## <a name="unity-porting-guidance"></a>Руководство по переносу Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Руководство по нереальному переносу

> [!IMPORTANT]
> Если вы используете контроллеры HP reverbы G2, обратитесь к [этой статье](../unreal/unreal-reverb-g2-controllers.md) для получения дополнительных инструкций по сопоставлению входных данных.

## <a name="see-also"></a>См. также раздел
* [Минимальные рекомендации по совместимости Windows Mixed Reality с оборудованием ПК](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Основные сведения о производительности смешанной реальности](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Рекомендации по повышению производительности для Unity](../unity/performance-recommendations-for-unity.md)
* [Контроллеры движения](../../design/motion-controllers.md)
* [Жесты и контроллеры движения в Unity](../unity/gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. Инпуттраккинг](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Руководства по переносу приложений](porting-guides.md)