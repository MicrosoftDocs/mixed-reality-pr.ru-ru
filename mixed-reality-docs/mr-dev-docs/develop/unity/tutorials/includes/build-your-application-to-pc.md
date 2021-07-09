---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392658"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-switching-build-platform"></a>1. Переключение платформы сборки

В меню Unity щелкните File (Файл) > Build Settings... (Параметры сборки...), чтобы открыть окно параметров сборки:

В окне параметров сборки выберите платформу **PC, Mac & Linux Standalone** и нажмите кнопку **Switch Platform** (Переключить платформу), чтобы изменить платформу сборки.

![Переключение платформы сборки](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

Когда Unity переключит платформу, щелкните значок крестика, чтобы закрыть окно параметров сборки.

### <a name="2-set-the-project-settings"></a>2. Настройка параметров проекта

В меню Unity выберите пункт **Edit** (Изменить)  >  **Project Settings** (Параметры проекта)  >  **XR Plug-in Management** (Управление подключаемыми модулями XR), убедитесь, что вы на вкладке Windows Standalone, и установите флажок **OpenXR** и **Windows Mixed Reality feature set** (Набор функций Windows Mixed Reality).

![Включение OpenXR и набора функций Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

В окне Project Settings (Параметры проекта) выберите **OpenXR**, убедитесь, что вы на вкладке Windows Standalone, и измените значение параметра **Depth submission mode** (Режим глубины при отправке) с None на **Depth 16 Bit** (16-битная глубина).

На вкладке профилей взаимодействия добавьте **Eye Gaze Interaction Profile** (Профиль взаимодействия взгляда) и **Microsoft Hand Interaction Profile** (Профиль взаимодействия рук Microsoft), щелкнув значок "+".

![Добавление профиля взаимодействия с помощью взгляда и профиля взаимодействия с помощью рук (Майкрософт)](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

В разделе **Open XR feature groups** (Открыть группы функций XR)  >  **All features** (Все функции) установите флажок **Holographic App Remoting** (Голографическое удаленное взаимодействие через приложение).

![Включение голографического удаленного взаимодействия через приложение](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

Далее установите флажок **Windows Mixed Reality** и в разделе группы Windows Mixed Reality установите флажок **Holographic App Remoting** (Голографическое удаленное взаимодействие с приложением).

![Включение голографического удаленного взаимодействия с приложением Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a>3. Сборка проекта Unity

В меню Unity щелкните File (Файл) > Build Settings... (Параметры сборки...), чтобы открыть окно параметров сборки:

В окне Build Settings (Параметры сборки) нажмите кнопку ***Add Open Scenes** _ (Добавить открытые сцены), чтобы добавить текущую сцену в список Scenes (Сцены). В списке Build (Сборка) нажмите кнопку _ *Build**:

![Окно параметров сборки Unity с добавленной сценой](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

Выберите подходящее расположение для хранения сборки, например Documents\MixedRealityLearning. Создайте папку и присвойте ей подходящее имя, например PCHolographicRemoting. Затем нажмите кнопку ***Select Folder*** (Выбрать папку), чтобы начать процесс сборки:

![Окно параметров сборки Unity с окном выбора папки](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

Подождите, пока Unity завершит сборку.

![Unity выполняет сборку](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

Дважды щелкните исполняемый файл, чтобы открыть на компьютере приложение голографического удаленного взаимодействия Holographic Remoting.

> [!NOTE]
> Из-за некоторых известных проблем в приложении Holographic Remoting для ПК, созданного как UWP, мы создаем приложение для ПК как Windows Standalone для OpenXR.


# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)

### <a name="1-set-the-player-settings"></a>1. Настройка параметров проигрывателя.

В разделе **XR Settings** (Параметры XR) установите флажок **WSA Holographic Remoting Supported** (Поддержка голографического удаленного взаимодействия WSA) и включите функцию голографического удаленного взаимодействия.

![Окно параметров смешанной реальности Unity с включенной поддержкой удаленного голографического взаимодействия WSA](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Создание проекта Unity.

В меню Unity щелкните File (Файл) > Build Settings... (Параметры сборки...), чтобы открыть окно параметров сборки:

В окне Build Settings (Параметры сборки) нажмите кнопку ***Add Open Scenes** _ (Добавить открытые сцены), чтобы добавить текущую сцену в список Scenes (Сцены). В списке Build (Сборка) нажмите кнопку _ *_Build_** (Сборка), чтобы открыть окно Build Universal Windows Platform (Создание приложений универсальной платформы Windows):

![Окно параметров сборки Unity с добавленной сценой](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

В окне Build Universal Windows Platform (Создание приложений универсальной платформы Windows) выберите подходящее расположение для хранения своей сборки, например Documents\MixedRealityLearning. Создайте папку и присвойте ей подходящее имя, например PCHolographicRemoting. Затем нажмите кнопку ***Select Folder*** (Выбрать папку), чтобы начать процесс сборки:

![Окно параметров сборки Unity с окном выбора папки](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Подождите, пока Unity завершит сборку.

![Unity выполняет сборку](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Сборка и развертывание приложения

По завершении процесса сборки Unity запросит проводник Windows открыть расположение с сохраненной сборкой. Перейдите к папке и дважды щелкните файл SLN, чтобы открыть его в Visual Studio:

![Проводник Windows с выбранным созданным решением Visual Studio](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано в документации по установке средств.

Настройте Visual Studio для компьютера, выбрав конфигурацию "Выпуск" архитектуру x64 и целевой объект "Локальный компьютер":

![Среда Visual Studio, настроенная для локального компьютера](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Нажмите кнопку ***Локальный компьютер***. Запустится сборка и развертывание приложения на вашем компьютере. Приложение будет установлено на ваш компьютер по умолчанию.
