---
ms.openlocfilehash: c205e3b812eeb7a85bfe361d4fd83f9aec7b7999
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244962"
---
# <a name="unity"></a>[Unity](#tab/unity)

![Баннер с логотипом Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1. Скачайте последнюю версию.

В качестве лучшей версии для запуска новых проектов мы рекомендуем [Unity LTS (долгосрочная поддержка)](https://unity3d.com/unity/qa/lts-releases). Затем ее можно обновить до последней версии, чтобы получить новые стабильные исправления.
* Сейчас рекомендуем использовать сборку **[Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)** , необходимую для MRTK версии 2 (см. ниже).
* Если вам по определенным причинам требуется использовать другую версию Unity, с этим не возникнет затруднений, так как Unity поддерживает параллельную установку различных версий.

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. Установка Mixed Reality Feature Tool

Средство [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md) предоставляет новый способ для обнаружения и добавления пакетов функций смешанной реальности в проекты Unity. 

Вы можете искать пакеты по имени или категории, просматривать их зависимости и даже проверять предлагаемые изменения в файле манифеста проектов перед импортом. Когда вы подтвердите список нужных пакетов, средство Mixed Reality Feature Tool скачает их в выбранный вами проект.

#### <a name="importing-the-mixed-reality-toolkit"></a>Импорт набора средств для смешанной реальности (MRTK)

![MRTK](../../design/images/MRTK_UX_Hero.png)

[Набор средств для смешанной реальности](../unity/mrtk-getting-started.md) (MRTK) — это кросс-платформенный пакет разработки с открытым кодом для приложений смешанной реальности. 

* Установите пакет Mixed Reality Toolkit, следуя [инструкциям по установке и использованию](../unity/welcome-to-mr-feature-tool.md#system-requirements), и выберите пакет **Mixed Reality Toolkit Foundation**.

Мы рекомендуем изучить раздел по началу работы, следуя нашим курируемым этапам разработки для[HoloLens](../unity/unity-development-overview.md#1-getting-started) или [виртуальной реальности](../unity/unity-development-wmr-overview.md#1-getting-started). Если вы уже работаете с этими этапами, выполните остальные шаги по настройке (см. ниже) и перейдите к [руководствам по началу работы с HoloLens 2](../unity/tutorials/mr-learning-base-01.md).

> [!IMPORTANT]
> Обратите внимание, что инструкции по установке приведены для последнего стабильного сочетания выпусков MRTK и Unity — **MRTK 2.5.1** и **Unity 2019.4 LTS**.

> [!NOTE]
> Если вы не хотите использовать MRTK для Unity, вам придется [самостоятельно написать скрипты для всех взаимодействий и моделей поведения](../unity/configure-unity-project.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Баннер Unity](../images/MRTK-Unity-Banner.png)<br>**Набор средств для смешанной реальности — Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a>Другие средства [необязательно]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Вспомогательный набор средств для смешанной реальности (GitHub)</a> — фрагменты кода и компоненты, которые не могут работать непосредственно в HoloLens или иммерсивных гарнитурах (гарнитурах виртуальной реальности), но могут объединяться с ними для взаимодействия в Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Набор средств для смешанной реальности — общий (GitHub)</a>. Это коллекция общих скриптов и компонентов.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Настройте компьютер для разработки приложений смешанной реальности.

Этот пакет SDK для Windows 10 лучше всего использовать в операционной системе Windows 10. Он также поддерживается в следующих операционных системах: Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Обратите внимание, что не все средства поддерживаются в операционных системах более ранних версий.

> [!NOTE]
> Вы можете разрабатывать и развертывать приложения для HoloLens, иммерсивных гарнитур виртуальной реальности или для устройств обоих типов. Убедитесь, что выполнены все указанные ниже требования в соответствии с вашими потребностями.

#### <a name="for-hololens-development"></a>Для разработки решений для HoloLens

При настройке компьютера для разработки решений для HoloLens убедитесь, что он соответствует системным требованиям для <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> и <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Если вы хотите запустить приложение на устройстве HoloLens, вам потребуется выполнить [инструкции по настройке портала устройств Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Если вы планируете использовать [эмулятор HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), убедитесь, что ваш компьютер соответствует [его системным требованиям](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Сведения о начале работы с эмулятором HoloLens см. в [этой статье](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

Если вы планируете разработку приложений для иммерсивных гарнитур (гарнитур виртуальной реальности) HoloLens и Windows Mixed Reality, ознакомьтесь с системными рекомендациями и требованиями в приведенном ниже разделе.

#### <a name="hololens-troubleshooting"></a>Устранение неполадок с HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>Неактивная кнопка для включения режима разработчика

Если вы сталкиваетесь с проблемами при включении режима разработчика на устройстве, возможно, у вас нет прав [владельца устройства](/hololens/security-adminless-os). В многопользовательском режиме то лицо, которое использует устройство первым, назначается владельцем. Все последующие пользователи не будут иметь нужных разрешений для включения режима разработчика или внесения других изменений в конфигурацию. Однако существует исключение, при котором первый пользователь может не быть владельцем устройства в среде с Autopilot. Подробные сведения см. в [документации по безопасности HoloLens](/hololens/security-adminless-os#device-owner).

Ниже представлены возможные решения.

* Владелец устройства должен включить режим разработчика перед передачей устройства другим пользователям или разработчикам.
* Рекомендация ИТ-администратору или администратору MDM включить параметр политики CSP [ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) для конкретного устройства или группы устройств, с которыми работают разработчики. 
    * Эту политику можно задать с помощью [пакетов подготовки](/hololens/hololens-provisioning) или через [MDM для устройств HoloLens](/hololens/hololens-mdm-configure)
* Использование решения [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery).

> [!NOTE]
> Дополнительные сведения об управлении устройствами HoloLens см. в **[этом обзоре](/hololens/hololens-csp-policy-overview)** .

##### <a name="i-cant-deploy-over-usb"></a>Не удается выполнить развертывание по USB

Если вы не можете развернуть приложение непосредственно по USB, убедитесь, что вы выполнили все приведенные выше требования к установке, и следуйте инструкциям из нашего [пошагового руководства](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).

#### <a name="immersive-vr-headset-requirements"></a>Требования к иммерсивной гарнитуре виртуальной реальности

>[!NOTE]
>Приведенные ниже рекомендации являются действующими минимальными и рекомендуемыми характеристиками для *компьютера, где будут разрабатываться приложения* для иммерсивных гарнитур (гарнитур виртуальной реальности). Эти рекомендации регулярно обновляются.

>[!WARNING]
>Не путайте их с [минимальными рекомендациями по совместимости аппаратного обеспечения компьютера](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), в которых изложены *спецификации компьютера потребителя*, на которые следует ориентироваться при работе с приложением или игрой, используемых с иммерсивной гарнитурой (виртуальная реальность).

Если на компьютере для разработки решений для иммерсивных гарнитур отсутствуют полноразмерные порты HDMI и (или) USB 3.0, для подключения гарнитуры вам потребуются [адаптеры](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).

Сейчас есть [известные проблемы](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) с некоторыми аппаратными конфигурациями, особенно на ноутбуках с гибридной графикой.

<table>
<tr>
<th></th><th> Минимальные требования</th><th> Рекомендуется</th>
</tr><tr>
<td> Процессор</td><td> <b>Ноутбук:</b> двухъядерный ЦП Intel Core i5 для мобильных систем 7-го поколения с технологией Hyper-Threading. <b>Настольный компьютер:</b> двухъядерный ЦП Intel i5 для настольных систем 6-го поколения с технологией Hyper-Threading <b>или</b> эквивалентный четырехъядерный процессор AMD FX4350 с частотой 4,2 ГГц.</td><td> <b>Настольный компьютер:</b> Intel i7 для настольных систем 6-го поколения (6 ядер) <b>или</b> AMD Ryzen 5 1600 (6 ядер, 12 потоков).</td>
</tr><tr>
<td> Графический процессор</td><td> <b>Ноутбук:</b> графический процессор, эквивалентный NVIDIA GTX 965M, AMD RX 460M (2 ГБ) или более мощным процессорам с поддержкой DX12; <b>настольный компьютер:</b> графический процессор, эквивалентный NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 ГБ) или более мощным процессорам с поддержкой DX12</td><td><b>Настольный компьютер:</b> графический процессор, эквивалентный NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 ГБ) или более мощным процессорам с поддержкой DX12</td>
</tr><tr>
<td> Версия WDDM драйвера графического процессора</td><td colspan="2"> Драйвер WDDM 2.2</td>
</tr><tr>
<td> Тепловая мощность</td><td colspan="2"> 15 Вт или выше</td>
</tr><tr>
<td> Порты для графического отображения</td><td colspan="2"> 1 доступный порт графического отображения для гарнитуры (HDMI 1.4 или DisplayPort 1.2 для гарнитур с частотой 60 Гц, HDMI 2.0 или DisplayPort 1.2 для гарнитур с частотой 90 Гц)</td>
</tr><tr>
<td> Разрешение дисплея</td><td colspan="2"> Разрешение: SVGA (800 x 600) или большая глубина цвета: 32 бита цвета на пиксель</td>
</tr><tr>
<td> Память</td><td> 8 ГБ ОЗУ или более</td><td> 16 ГБ ОЗУ или более</td>
</tr><tr>
<td> Хранение</td><td colspan="2"> &gt;10 ГБ дополнительного пространства</td>
</tr><tr>
<td> USB-порты</td><td colspan="2"> 1 доступный USB-порт для гарнитуры (USB 3.0 Type-A)<b>Примечание. Сила тока USB должна составлять минимум 900 мА</b>.</td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (для подключения периферийных устройств)</td>
</tr>
</table>

Если у вас нет опыта разработки с использованием MRTK в Unity, мы рекомендуем вам изучить наш обзор разработки для Unity:

> [!div class="nextstepaction"]
> [Начало работы с Unity для HoloLens](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [Начало работы с Unity для виртуальной реальности](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы следуете изложенным нами этапам разработки в Unity для HoloLens, вашей следующей задачей будет изучение руководств по HoloLens 2.

> [!div class="nextstepaction"]
> [Серия руководств по HoloLens 2](../unity/tutorials/mr-learning-base-01.md)

Если вы следуете этапам разработки в Unity для виртуальной реальности, настройте свой проект.

> [!div class="nextstepaction"]
> [Настройка проекта для WMR](../unity/configure-unity-project.md)

Вы можете в любой момент вернуться к этапам разработки в Unity для [HoloLens](../unity/unity-development-overview.md#1-getting-started) и [виртуальной реальности](../unity/unity-development-wmr-overview.md#1-getting-started).

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1. Скачайте последнюю версию.

Мы рекомендуем установить [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) или более поздней версии, чтобы воспользоваться всеми преимуществами встроенной поддержки HoloLens.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Импортируйте набор средств для смешанной реальности (MRTK).
![MRTK](../../design/images/MRTK_UX_Hero.png)

Набор средств для смешанной реальности (MRTK) — это кроссплатформенный пакет SDK с открытым кодом для приложений смешанной реальности. MRTK предоставляет кросс-платформенную систему ввода, базовые компоненты и общие строительные блоки для пространственных взаимодействий. Набор используется для ускорения разработки приложений, предназначенных для Microsoft HoloLens, иммерсивных гарнитур (гарнитур виртуальной реальности) Windows Mixed Reality и платформы OpenVR.

Для выполнения установки мы рекомендуем изучить [раздел по началу работы](../unreal/unreal-development-overview.md#1-getting-started) нашего [обзора разработки для Unreal](../unreal/unreal-development-overview.md). Если вы уже работаете с этим обзором, выполните остальные шаги по настройке (см. ниже) и перейдите к [руководствам по началу работы с HoloLens 2](../unreal/tutorials/unreal-uxt-ch1.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Изображение с логотипом Unity](../images/MRTK-Unreal-Banner.png)<br>**Набор средств для смешанной реальности — Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Если вы не хотите использовать MRTK для Unreal, вам придется самостоятельно написать скрипты для всех взаимодействий и моделей поведения.

#### <a name="other-tools-optional"></a>Другие средства [необязательно]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Вспомогательный набор средств для смешанной реальности (GitHub)</a> — фрагменты кода и компоненты, которые не могут работать непосредственно в HoloLens или иммерсивных гарнитурах (гарнитурах виртуальной реальности), но могут объединяться с ними для взаимодействия в Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Набор средств для смешанной реальности (общий (GitHub))</a> — это коллекция общих скриптов и компонентов.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Настройте компьютер для разработки приложений смешанной реальности.

Этот пакет SDK для Windows 10 лучше всего использовать в операционной системе Windows 10. Он также поддерживается в следующих операционных системах: Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Обратите внимание, что не все средства поддерживаются в операционных системах более ранних версий.

> [!NOTE]
> Вы можете разрабатывать и развертывать приложения для HoloLens, иммерсивных гарнитур виртуальной реальности или для устройств обоих типов. Убедитесь, что выполнены все указанные ниже требования в соответствии с вашими потребностями.

#### <a name="for-hololens-development"></a>Для разработки решений для HoloLens

При настройке компьютера для разработки решений для HoloLens убедитесь, что он соответствует системным требованиям для [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) и <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Если вы хотите запустить приложение на устройстве HoloLens, вам потребуется выполнить [инструкции по настройке портала устройств Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Если вы планируете использовать [эмулятор HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), убедитесь, что ваш компьютер соответствует [его системным требованиям](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Если вы планируете разработку приложений для иммерсивных гарнитур (гарнитур виртуальной реальности) HoloLens и Windows Mixed Reality, ознакомьтесь с системными рекомендациями и требованиями в приведенном ниже разделе.

#### <a name="hololens-troubleshooting"></a>Устранение неполадок с HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>Неактивная кнопка для включения режима разработчика

Если вы сталкиваетесь с проблемами при включении режима разработчика на устройстве, возможно, у вас нет прав [владельца устройства](/hololens/security-adminless-os). В многопользовательском режиме то лицо, которое использует устройство первым, назначается владельцем. Все последующие пользователи не будут иметь нужных разрешений для включения режима разработчика или внесения других изменений в конфигурацию. Однако существует исключение, при котором первый пользователь может не быть владельцем устройства в среде с Autopilot. Подробные сведения см. в [документации по безопасности HoloLens](/hololens/security-adminless-os#device-owner).

Ниже представлены возможные решения.

* Владелец устройства должен включить режим разработчика перед передачей устройства другим пользователям или разработчикам.
* Рекомендация ИТ-администратору или администратору MDM включить параметр политики CSP [ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) для конкретного устройства или группы устройств, с которыми работают разработчики. 
    * Эту политику можно задать с помощью [пакетов подготовки](/hololens/hololens-provisioning) или через [MDM для устройств HoloLens](/hololens/hololens-mdm-configure)
* Использование решения [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery).

> [!NOTE]
> Дополнительные сведения об управлении устройствами HoloLens см. в **[этом обзоре](/hololens/hololens-csp-policy-overview)** .

##### <a name="i-cant-deploy-over-usb"></a>Не удается выполнить развертывание по USB

Если вы не можете развернуть приложение непосредственно по USB, убедитесь, что вы выполнили все приведенные выше требования к установке, и следуйте инструкциям из нашего [пошагового руководства](../unreal/tutorials/unreal-uxt-ch6.md).

#### <a name="immersive-vr-headset-requirements"></a>Требования к иммерсивной гарнитуре виртуальной реальности

>[!NOTE]
>Приведенные ниже рекомендации являются действующими минимальными и рекомендуемыми характеристиками для *компьютера, где будут разрабатываться приложения* для иммерсивных гарнитур (гарнитур виртуальной реальности). Эти рекомендации регулярно обновляются.

>[!WARNING]
>Не путайте их с [минимальными рекомендациями по совместимости аппаратного обеспечения компьютера](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), в которых изложены *спецификации компьютера потребителя*, на которые следует ориентироваться при работе с приложением или игрой, используемых с иммерсивной гарнитурой (виртуальная реальность).

Если на компьютере для разработки решений для иммерсивных гарнитур отсутствуют полноразмерные порты HDMI и (или) USB 3.0, для подключения гарнитуры вам потребуются [адаптеры](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).

Сейчас есть [известные проблемы](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) с некоторыми аппаратными конфигурациями, особенно на ноутбуках с гибридной графикой.

<table>
<tr>
<th></th><th> Минимальные требования</th><th> Рекомендуется</th>
</tr><tr>
<td> Процессор</td><td> <b>Ноутбук:</b> двухъядерный ЦП Intel Core i5 для мобильных систем 7-го поколения с технологией Hyper-Threading. <b>Настольный компьютер:</b> двухъядерный ЦП Intel i5 для настольных систем 6-го поколения с технологией Hyper-Threading <b>или</b> эквивалентный четырехъядерный процессор AMD FX4350 с частотой 4,2 ГГц.</td><td> <b>Настольный компьютер:</b> Intel i7 для настольных систем 6-го поколения (6 ядер) <b>или</b> AMD Ryzen 5 1600 (6 ядер, 12 потоков).</td>
</tr><tr>
<td> Графический процессор</td><td> <b>Ноутбук:</b> графический процессор, эквивалентный NVIDIA GTX 965M, AMD RX 460M (2 ГБ) или более мощным процессорам с поддержкой DX12; <b>настольный компьютер:</b> графический процессор, эквивалентный NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 ГБ) или более мощным процессорам с поддержкой DX12</td><td><b>Настольный компьютер:</b> графический процессор, эквивалентный NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 ГБ) или более мощным процессорам с поддержкой DX12</td>
</tr><tr>
<td> Версия WDDM драйвера графического процессора</td><td colspan="2"> Драйвер WDDM 2.2</td>
</tr><tr>
<td> Тепловая мощность</td><td colspan="2"> 15 Вт или выше</td>
</tr><tr>
<td> Порты для графического отображения</td><td colspan="2"> 1 доступный порт графического отображения для гарнитуры (HDMI 1.4 или DisplayPort 1.2 для гарнитур с частотой 60 Гц, HDMI 2.0 или DisplayPort 1.2 для гарнитур с частотой 90 Гц)</td>
</tr><tr>
<td> Разрешение дисплея</td><td colspan="2"> Разрешение: SVGA (800 x 600) или большая глубина цвета: 32 бита цвета на пиксель</td>
</tr><tr>
<td> Память</td><td> 8 ГБ ОЗУ или более</td><td> 16 ГБ ОЗУ или более</td>
</tr><tr>
<td> Хранение</td><td colspan="2"> &gt;10 ГБ дополнительного пространства</td>
</tr><tr>
<td> USB-порты</td><td colspan="2"> 1 доступный USB-порт для гарнитуры (USB 3.0 Type-A)<b>Примечание. Сила тока USB должна составлять минимум 900 мА</b>.</td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (для подключения периферийных устройств)</td>
</tr>
</table>

Если у вас нет опыта разработки с использованием MRTK в Unreal, мы рекомендуем вам изучить наш обзор разработки для Unreal:

> [!div class="nextstepaction"]
> [Начало работы с Unreal](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы следуете изложенным нами этапам разработки для Unreal, вашей следующей задачей будет изучение руководств по HoloLens 2.

> [!div class="nextstepaction"]
> [Серия руководств по HoloLens 2](../unreal/tutorials/unreal-uxt-ch1.md)

Вы можете в любой момент вернуться к [этапам разработки для Unreal](../unreal/unreal-development-overview.md#1-getting-started).

# <a name="native-openxr"></a>[Нативные решения (OpenXR)](#tab/native)

 ![Разработка нативных приложений](../images/native_logo_banner.png)

Для нативной разработки с использованием OpenXR вам не нужно скачивать движок. Все необходимое для начала разработки с помощью OpenXR можно найти в [этом документе](../native/openxr-getting-started.md).

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1. Настройте компьютер для разработки приложений смешанной реальности.

Этот пакет SDK для Windows 10 лучше всего использовать в операционной системе Windows 10. Он также поддерживается в следующих операционных системах: Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Обратите внимание, что не все средства поддерживаются в операционных системах более ранних версий.

#### <a name="for-hololens-development"></a>Для разработки решений для HoloLens

При настройке компьютера для разработки решений для HoloLens убедитесь, что он соответствует системным требованиям для <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Если вы хотите запустить приложение на устройстве HoloLens, вам потребуется выполнить [инструкции по настройке портала устройств Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Если вы планируете использовать [эмулятор HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), убедитесь, что ваш компьютер соответствует [его системным требованиям](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Если вы планируете разработку приложений для иммерсивных гарнитур (гарнитур виртуальной реальности) HoloLens и Windows Mixed Reality, ознакомьтесь с системными рекомендациями и требованиями в приведенном ниже разделе.

> [!NOTE]
> Вы можете разрабатывать и развертывать приложения для HoloLens, иммерсивных гарнитур виртуальной реальности или для устройств обоих типов. Убедитесь, что выполнены все указанные ниже требования в соответствии с вашими потребностями.

#### <a name="hololens-troubleshooting"></a>Устранение неполадок с HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>Неактивная кнопка для включения режима разработчика

Если вы сталкиваетесь с проблемами при включении режима разработчика на устройстве, возможно, у вас нет прав [владельца устройства](/hololens/security-adminless-os). В многопользовательском режиме то лицо, которое использует устройство первым, назначается владельцем. Все последующие пользователи не будут иметь нужных разрешений для включения режима разработчика или внесения других изменений в конфигурацию. Однако существует исключение, при котором первый пользователь может не быть владельцем устройства в среде с Autopilot. Подробные сведения см. в [документации по безопасности HoloLens](/hololens/security-adminless-os#device-owner).

Ниже представлены возможные решения.

* Владелец устройства должен включить режим разработчика перед передачей устройства другим пользователям или разработчикам.
* Рекомендация ИТ-администратору или администратору MDM включить параметр политики CSP [ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) для конкретного устройства или группы устройств, с которыми работают разработчики. 
    * Эту политику можно задать с помощью [пакетов подготовки](/hololens/hololens-provisioning) или через [MDM для устройств HoloLens](/hololens/hololens-mdm-configure)
* Использование решения [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery).

> [!NOTE]
> Дополнительные сведения об управлении устройствами HoloLens см. в **[этом обзоре](/hololens/hololens-csp-policy-overview)** .

#### <a name="immersive-vr-headset-requirements"></a>Требования к иммерсивной гарнитуре виртуальной реальности

>[!NOTE]
>Приведенные ниже рекомендации являются действующими минимальными и рекомендуемыми характеристиками для *компьютера, где будут разрабатываться приложения* для иммерсивных гарнитур (гарнитур виртуальной реальности). Эти рекомендации регулярно обновляются.

>[!WARNING]
>Не путайте их с [минимальными рекомендациями по совместимости аппаратного обеспечения компьютера](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), в которых изложены *спецификации компьютера потребителя*, на которые следует ориентироваться при работе с приложением или игрой, используемых с иммерсивной гарнитурой (виртуальная реальность).

Если на компьютере для разработки решений для иммерсивных гарнитур отсутствуют полноразмерные порты HDMI и (или) USB 3.0, для подключения гарнитуры вам потребуются [адаптеры](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).

Сейчас есть [известные проблемы](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) с некоторыми аппаратными конфигурациями, особенно на ноутбуках с гибридной графикой.

<table>
<tr>
<th></th><th> Минимальные требования</th><th> Рекомендуется</th>
</tr><tr>
<td> Процессор</td><td> <b>Ноутбук:</b> двухъядерный ЦП Intel Core i5 для мобильных систем 7-го поколения с технологией Hyper-Threading. <b>Настольный компьютер:</b> двухъядерный ЦП Intel i5 для настольных систем 6-го поколения с технологией Hyper-Threading <b>или</b> эквивалентный четырехъядерный процессор AMD FX4350 с частотой 4,2 ГГц.</td><td> <b>Настольный компьютер:</b> Intel i7 для настольных систем 6-го поколения (6 ядер) <b>или</b> AMD Ryzen 5 1600 (6 ядер, 12 потоков).</td>
</tr><tr>
<td> Графический процессор</td><td> <b>Ноутбук:</b> графический процессор, эквивалентный NVIDIA GTX 965M, AMD RX 460M (2 ГБ) или более мощным процессорам с поддержкой DX12; <b>настольный компьютер:</b> графический процессор, эквивалентный NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 ГБ) или более мощным процессорам с поддержкой DX12</td><td><b>Настольный компьютер:</b> графический процессор, эквивалентный NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 ГБ) или более мощным процессорам с поддержкой DX12</td>
</tr><tr>
<td> Версия WDDM драйвера графического процессора</td><td colspan="2"> Драйвер WDDM 2.2</td>
</tr><tr>
<td> Тепловая мощность</td><td colspan="2"> 15 Вт или выше</td>
</tr><tr>
<td> Порты для графического отображения</td><td colspan="2"> 1 доступный порт графического отображения для гарнитуры (HDMI 1.4 или DisplayPort 1.2 для гарнитур с частотой 60 Гц, HDMI 2.0 или DisplayPort 1.2 для гарнитур с частотой 90 Гц)</td>
</tr><tr>
<td> Разрешение дисплея</td><td colspan="2"> Разрешение: SVGA (800 x 600) или большая глубина цвета: 32 бита цвета на пиксель</td>
</tr><tr>
<td> Память</td><td> 8 ГБ ОЗУ или более</td><td> 16 ГБ ОЗУ или более</td>
</tr><tr>
<td> Хранение</td><td colspan="2"> &gt;10 ГБ дополнительного пространства</td>
</tr><tr>
<td> USB-порты</td><td colspan="2"> 1 доступный USB-порт для гарнитуры (USB 3.0 Type-A)<b>Примечание. Сила тока USB должна составлять минимум 900 мА</b>.</td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (для подключения периферийных устройств)</td>
</tr>
</table>

Если у вас нет опыта разработки с использованием MRTK на нативных платформах, мы рекомендуем вам изучить наш обзор разработки для нативных платформ:

> [!div class="nextstepaction"]
> [Начало работы с нативными инструментами разработки](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы следуете изложенным нами этапам разработки для нативных платформ, вашей следующей задачей будет настройка среды разработки для HoloLens 2.

> [!div class="nextstepaction"]
> [Настройка для HoloLens 2](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

Вы можете в любой момент вернуться к [этапам разработки для нативных платформ](../native/directx-development-overview.md#1-getting-started).