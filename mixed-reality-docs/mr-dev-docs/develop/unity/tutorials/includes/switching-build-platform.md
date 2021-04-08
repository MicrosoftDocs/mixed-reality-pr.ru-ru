---
ms.openlocfilehash: 78605b17e93429ad974e1ca21e7859035f38d615
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088720"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Подключаемый модуль Unity 2019/2020 + Windows XR](#tab/winxr)

В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:

![Выбор параметров сборки Unity в меню](../images/mr-learning-base/base-02-section2-step1-1.png)

В окне параметров сборки щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу):

![Окно параметров сборки в Unity с выбранной платформой UWP](../images/mr-learning-base/base-02-section2-step1-2.png)

Подождите, пока Unity переключит платформу:

![Unity выполняет переключение платформы](../images/mr-learning-base/base-02-section2-step1-3.png)

Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки:

![Окно сборки Unity с выделенным значком закрытия](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:

![Выбор параметров сборки Unity в меню](../images/mr-learning-base/base-02-section2-step1-1.png)

В окне параметров сборки щелкните элемент **Universal Windows Platform** (Универсальная платформа Windows). Затем сделайте следующее:
1.  Задайте для параметра **Target device** (Целевое устройство) значение **HoloLens**.
2.  Задайте для параметра **Architecture** (Архитектура) значение **ARM 64**.
3.  Задайте для параметра **Build Type** (Тип сборки) значение **D3D**.
4.  Задайте для параметра **Minimum Platform Version** (Минимальная версия платформы) значение **10.2.18362**.
5.  Задайте для параметра **UWP SDK** (Пакет SDK для UWP) значение **Latest installed** (Последняя установленная версия).
6.  Задайте для параметра **Build configuration** (Конфигурация сборки) значение **Release** (Выпуск), так как есть известные проблемы с производительностью при отладке.
7.  Нажмите кнопку Switch Platform (Сменить платформу).


![Окно параметров сборки Unity с заданным параметром Universal Windows Platform (Универсальная платформа Windows)](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки.

# <a name="legacy-wsa"></a>[Устаревшая версия WSA](#tab/wsa)

В меню Unity щелкните **File** > **Build Settings...** (Файл > Параметры сборки...), чтобы открыть окно параметров сборки:

![Выбор параметров сборки Unity в меню](../images/mr-learning-base/base-02-section2-step1-1.png)

В окне параметров сборки щелкните **Universal Windows Platform** (Универсальная платформа Windows) и нажмите кнопку **Switch Platform** (Переключить платформу):

![Окно параметров сборки в Unity с выбранной платформой UWP](../images/mr-learning-base/base-02-section2-step1-2.png)

Подождите, пока Unity переключит платформу:

![Unity выполняет переключение платформы](../images/mr-learning-base/base-02-section2-step1-3.png)

Когда Unity переключит платформу, щелкните красный значок **x**, чтобы закрыть окно параметров сборки:

![Окно сборки Unity с выделенным значком закрытия](../images/mr-learning-base/base-02-section2-step1-4.png)