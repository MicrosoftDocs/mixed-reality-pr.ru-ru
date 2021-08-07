---
title: Перенос приложений VR в Windows Mixed Reality
description: Пошаговое руководство, объясняющее, как перенести существующее иммерсивное приложение в Windows Mixed Reality.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: порт, unity, нереал, по промежуточного слоя, подсистема, UWP, Win32, перенос, HoloLens 1-ом, гарнитура смешанной реальности, гарнитура windows mixed reality, миграция, Windows 10, сопоставление входных данных
ms.openlocfilehash: c8f0ed76fc7288ed406e2044eb2f3edb8982865b5c956f460d2bc1b815e503df
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213521"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Перенос приложений VR в Windows Mixed Reality

Windows 10 включает поддержку для впечатляющих и holographic головных телефонов. Если вы создали содержимое для других устройств, таких как Окулус Рифт или HTC Naopak, они имеют зависимости от библиотек, существующих над API платформы операционной системы. перевод существующих приложений Win32 Unity версии в Windows Mixed Reality включает в себя перенацеленное использование пакетов sdk vr, зависящих от поставщика, для api-интерфейсов версии unity cross-vendor.

## <a name="porting-requirements"></a>Требования к переносу

На высоком уровне следующие шаги участвуют в переносе существующего содержимого:
1. **убедитесь, что на компьютере работает Windows 10 Fall Creators Update (16299).** Мы больше не рекомендуем получать предварительные сборки от программы предварительной оценки, так как эти сборки не будут самыми стабильными при разработке смешанной реальности.
2. **Обновите версию графического или игрового модуля до последней версии.** обработчики игр должны поддерживать Windows 10 SDK версии 10.0.15063.0 (выпущена в апреле 2017) или более поздней версии.
3. **Обновите любое промежуточное по, подключаемые модули или компоненты.** Если приложение содержит какие-либо компоненты, рекомендуется выполнить обновление до последней версии.
4. **Удалите зависимости от повторяющихся пакетов SDK**. в зависимости от устройства, для которого предназначено содержимое, необходимо удалить или условно откомпилировать этот пакет SDK, чтобы вместо этого можно было ориентироваться на Windows api. Пример такого сценария — Стеамвр.
5. **Работа с проблемами сборки.** На этом этапе упражнение по переносу зависит от вашего приложения, подсистемы и зависимостей компонентов.

## <a name="common-porting-steps"></a>Общие этапы переноса

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Убедитесь, что у вас есть правильное оборудование для разработки

На странице с [руководством по VR](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) .

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. Обновите до последнего рейса Windows 10

платформа Windows Mixed Reality по-прежнему находится под активной разработкой. мы рекомендуем [присоединиться к программе предварительной оценки Windows](https://insider.windows.com/) , чтобы получить доступ к рейсу Windowsной предварительной оценки.
1. установка [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [присоединяйтесь](https://insider.windows.com/) к программе предварительной оценки Windows.
3. Включить [режим разработчика](/windows/uwp/get-started/enable-your-device-for-development)
4. переключиться на [Windows "быстрый рейс](/archive/blogs/uktechnet/joining-insider-preview) " в **разделе Параметры > обновление & безопасности**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. обновление до последней сборки Visual Studio
* если вы используете Visual Studio, выполните обновление до последней сборки
* см. раздел [установка средств на](../install-the-tools.md#installation-checklist) странице Visual Studio 2019.

### <a name="4-choose-the-correct-adapter"></a>4. Выберите правильный адаптер.
* В таких системах, как записные книжки с двумя графическими процессорами, следует [выбрать правильный адаптер](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Это относится к Unity и собственным приложениям DirectX, где ID3D11Device создается явно или неявно (Media Foundation) для своей функциональности.

## <a name="unity-porting-guidance"></a>Руководство по переносу Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Руководство по нереальному переносу

> [!IMPORTANT]
> Если вы используете контроллеры HP reverbы G2, обратитесь к [этой статье](../unreal/unreal-reverb-g2-controllers.md) для получения дополнительных инструкций по сопоставлению входных данных.

## <a name="see-also"></a>См. также раздел
* [Windows Mixed Reality минимальные рекомендации по совместимости оборудования пк](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Основные сведения о производительности смешанной реальности](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Рекомендации производительности для Unity](../unity/performance-recommendations-for-unity.md)
* [Контроллеры движения](../../design/motion-controllers.md)
* [Контроллеры движения в Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. Инпуттраккинг](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Руководства по переносу приложений](porting-guides.md)