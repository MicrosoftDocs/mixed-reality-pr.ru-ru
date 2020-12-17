---
title: Профилирование с помощью неreal Insights
description: Узнайте, как использовать неreal Insights в HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Нереал, Нереальный механизм 4, UE4, HoloLens, HoloLens 2, разработка, профилирования, нереалная информация, документация, руководства, функции, голограммы, Разработка игр, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 20e620f147f2cf5ee05073467c8ce7335340d59d
ms.sourcegitcommit: 53bde413a174712cb9d3794d02d96363a2d599cd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97486375"
---
# <a name="profiling-with-unreal-insights"></a>Профилирование с помощью неreal Insights 

[Нереалная аналитика](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) — это система профилирования, собирающая, анализирующая и визуализирующая данные из нереального механизма. Система профилирования помогает найти узкие места оптимизации и области, в которых производительность приложений может увеличиться. Как правило, вы включаете функцию "неreal Insights" прямо из редактора, но для HoloLens 2 потребуется использовать командную строку.  

## <a name="setup"></a>Настройка

Нереал. позволяет создать и настроить "настраиваемый профиль" в средстве запуска HoloLens с параметрами командной строки, которые включают неreal Insights.

1.  Найдите IP-адрес компьютера с помощью команды **ipconfig** в командной строке. IP-адрес — это адрес IPv4, указанный в ipconfig. Помните об этом при настройке параметров командной строки.

> [!IMPORTANT]
> Если вы находитесь за VPN, вам может потребоваться предоставить IP-адрес, предоставленный через VPN.

![Снимок экрана: результаты командной строки для команды ipconfig](images/unreal-insights-img-01.png)

2.  Перейдите в начало панели нереала и откройте **Device Manager** под кнопкой **запуска** :

![Снимок экрана параметров запуска с выделенным диспетчером устройств](images/unreal-insights-img-02.png)

3.  В Device Manager выберите **Добавить устройство, которое** не было добавлено в список.

![Снимок экрана: Открытие диспетчера устройств в нереальном ядре](images/unreal-insights-img-03.png)

4. Щелкните **выбрать платформу** и выберите **HoloLens**:

![Снимок экрана: Добавление раскрывающегося списка непоставленных устройств с выделенным HoloLens](images/unreal-insights-img-04.png)

5.  Если вы используете Иповерусб, введите 127.0.0.1:10080 в качестве идентификатора устройства. Введите имя пользователя и пароль HoloLens в соответствующие поля и заполните **Отображаемое название** по своему усмотрению.

> [!IMPORTANT]
> Идентификатор устройства — это IP-адрес HoloLens, а не компьютер с нереальными сведениями, найденными на шаге 1.

![Снимок экрана сведений об устройстве HoloLens в диспетчере устройств](images/unreal-insights-img-05.png)

6.  Выберите **Добавить** , и HoloLens должен появиться в списке устройств диспетчера устройств:

![Снимок экрана: HoloLens добавлен в список устройств](images/unreal-insights-img-06.png)

## <a name="launch"></a>Launch

1. Откройте **средство запуска проектов** на панели UE4 под кнопкой **запустить** :

![Снимок экрана параметров запуска с выделенным средством запуска проекта](images/unreal-insights-img-07.png)

2. Нажмите **+** кнопку, чтобы создать настраиваемый профиль в разделе **пользовательские профили запуска**. После создания этот профиль можно изменить позже:

![Снимок экрана средства запуска проекта с выделенными пользовательскими профилями запуска](images/unreal-insights-img-08.png)

3. Нажмите кнопку **изменить профиль** в настраиваемом профиле запуска HoloLens и настройте:
    * Выберите в **книге** **Кука** , чтобы включить копирование на устройство
    * Возможно, вы захотите выполнить **архивацию** в разделе " **Архив** ", чтобы сохранить созданный. appxbundle вместо удаления, чтобы сэкономить место на диске. Укажите расположение для appxbundle и переключитесь на сборку разработки, если хотите

![Снимок экрана с параметрами Кука в конфигурации профиля с Кука, выделенной книгой и HoloLens](images/unreal-insights-img-09.png)

4. Укажите, **как вы хотите развернуть сборку?** для **копирования на устройство** , чтобы активировать раздел **запуска** пользовательского интерфейса:

![Снимок экрана средства запуска проектов с параметрами развертывания с выделенным копированием в устройство](images/unreal-insights-img-10.png)

5. Задайте **Дополнительные параметры командной строки** в разделе **Launch** . Параметры записываются в файл ue4commandline.txt, упаковываются в пакет и используются при запуске. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * Попробуйте для начинающих: **-трацехост = IP_OF_YOUR_PC-Trace = журнал, закладка, кадр, ЦП, GPU, лоадтиме, файл, NET**
    * Полный список доступных параметров запуска можно найти в [справочной документации о нереальных аналитиках](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).

> [!NOTE]
> "IP_OF_YOUR_PC" — это IP-адрес, найденный на шаге 1. Это IP-адрес компьютера, на котором выполняются нереальные аналитические сведения, а не IP-адрес HoloLens.

> [!IMPORTANT]
> Трассировка может значительно быстро получиться. Включайте только те каналы, которые необходимы для обеспечения низкого размера трассировки.

![Снимок экрана параметров конфигурации запуска](images/unreal-insights-img-11.png)

6. Запустите нереалную аналитику перед запуском приложения, иначе нереальное понимание не сможет выполнить правильную инициализацию приложения:
    * Исполняемый файл неreal Insights хранится в папке обработчика двоичных файлов, как правило, следующим образом: "C:\Program Филес\епик Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe".

![Снимок экрана исполняемого файла неreal Insights](images/unreal-insights-img-12.png)

6.  Нажмите кнопку **назад** , чтобы вернуться в корневую папку диалогового окна **запуска проекта** .
7.  В редакторе щелкните **запустить** в настраиваемом профиле запуска.

![Снимок экрана с пользовательскими профилями запуска](images/unreal-insights-img-13.png)

8.  Следите за тем, чтобы проект был упакован, установлен на устройстве и запущен.

## <a name="profiling"></a>Профилирование

Вернувшись в нереалную аналитику, выберите **активное** подключение к устройству для запуска профилирования.

Пользовательский профиль является общим для проектов. Здесь вы можете использовать созданный вами пользовательский профиль вместо того, чтобы делать это каждый раз. Подключение к устройству необходимо создать заново при каждом запуске нереального действия с шагами 3 – 6 в [разделе Настройка](#setup).

## <a name="see-also"></a>См. также раздел
* [Документация по нереальным аналитикам](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)
