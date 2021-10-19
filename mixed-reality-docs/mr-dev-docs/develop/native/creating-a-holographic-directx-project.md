---
title: Создание голографического проекта в DirectX
description: узнайте, как создать новое приложение holographic DirectX на основе шаблона приложения Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, holographic приложение, новое приложение, приложение UWP, шаблонное приложение, голограммы, новый проект, пошаговое руководство, загрузка, пример кода, гарнитура смешанной реальности, гарнитура Windows Mixed reality, гарнитура виртуальной реальности
ms.openlocfilehash: f8ab131f563771599173ed141195bc4f19497df1
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130154970"
---
# <a name="creating-a-holographic-directx-project"></a>Создание голографического проекта в DirectX

> [!NOTE]
> Эта статья связана с устаревшими собственными API-интерфейсами WinRT.  Для новых проектов собственных приложений рекомендуется использовать **[API опенкср](openxr-getting-started.md)**.

приложение с более holographic, которое создается для HoloLens, будет иметь <a href="/windows/uwp/get-started/universal-application-platform-guide" target="_blank">универсальная платформа Windows (UWP)</a>.  если нацеливание на настольные Windows Mixed Reality гарнитуры, можно создать приложение UWP или приложение Win32.

Шаблон приложения с DirectX 11 holographic, который похож на шаблон приложения UWP DirectX 11. Шаблон включает цикл программы, класс **DeviceResources** для управления устройством и контекстом Direct3D, а также упрощенный класс модуля подготовки содержимого. Он также имеет <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, как и любое другое приложение UWP.

Однако приложение Mixed Reality имеет некоторые дополнительные возможности, отсутствующие в типичном приложении UWP для платформы Direct3D. шаблон приложения Windows Mixed Reality может:
* Обрабатывайте ресурсы устройства Direct3D, связанные с Holographic.
* Извлечение задних буферов камеры из системы. В случае с Direct3D12 создавайте ресурсы для буферов и Управляйте временем существования ресурсов.
* Обрабатывает входные данные [взгляда](../../design/gaze-and-commit.md) и распознает [жест](../../design/gaze-and-commit.md#composite-gestures).
* Переход к полноэкранному режиму отображения.

## <a name="how-do-i-get-started"></a>С чего начать?

сначала [установите средства](../install-the-tools.md), следуя инструкциям в статье загрузка Visual Studio 2019 и шаблонов Windows Mixed Reality приложений. шаблоны приложений смешанной реальности доступны в Visual Studio marketplace в виде [веб-загрузки](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)или устанавливаются в виде расширения с помощью пользовательского интерфейса Visual Studio.

теперь вы готовы к созданию приложения DirectX 11 Windows Mixed Reality! Обратите внимание, что для удаления образца содержимого закомментируйте директиву препроцессора **DRAW_SAMPLE_CONTENT** в *PCH. h*.

## <a name="creating-a-uwp-project"></a>Создание проекта UWP

После установки средств] (. /install-the-tools.md) вы можете создать проект с помощью DirectX UWP.

чтобы создать новый проект в Visual Studio 2019, выполните следующие действия.
1. Запустите **Visual Studio**.
2. в разделе **Начало работы** справа выберите **создать новый проект**.
3. в раскрывающихся меню диалогового окна **создание нового проекта** выберите **C++**, **Windows Mixed Reality** и **UWP**.
4. выберите **приложение holographic DirectX 11 (универсальное Windows) (C++/WinRT)**.
   ![снимок экрана шаблона проекта приложения UWP с/WinRTом DirectX 11 с + + в Visual Studio 2019](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *шаблон проекта приложения UWP для DirectX 11/WinRT с + + в Visual Studio 2019*
   >[!IMPORTANT]
   >Убедитесь, что имя шаблона проекта содержит "(C++/WinRT)".  Если нет, то у вас установлена старая версия шаблонов проектов Holographic.  чтобы получить последние шаблоны проектов, [установите их](../install-the-tools.md) в качестве расширения Visual Studio 2019.
5. Нажмите кнопку **Далее**.
5. заполните поля **Project имя** и **расположение** , а затем выберите или нажмите кнопку **создать**. Создается проект holographic приложения.
6. для целей разработки, предназначенных только для HoloLens 2, убедитесь, что для **целевой версии** и **минимальной версии** задано значение **Windows 10, версия 1903**.  если вы также настраиваете гарнитуры HoloLens (1-й номер) или настольные Windows Mixed Reality, можно задать для параметра **минимальная версия** значение **Windows 10, версия 1809**. Это потребует некоторых <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">адаптивных проверок версии</a> в коде при использовании новых функций HoloLens 2.
   ![снимок экрана: установка Windows 10, версия 1903 в качестве целевой и минимальной версий](images/new-uwp-project.png)<br>
   *настройка **Windows 10, версии 1903** в качестве целевой и минимальной версий*
   >[!IMPORTANT]
   >если вы не видите **Windows 10 версии 1903** , значит, не установлена последняя версия пакета SDK для Windows 10.  чтобы отобразить этот параметр, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">установите версию 10.0.18362.0 или более позднюю версию пакета SDK Windows 10</a>.

чтобы создать новый проект в Visual Studio 2017, выполните следующие действия.
1. Запустите **Visual Studio**.
2. в меню **файл** наведите указатель мыши на пункт **создать** и выберите **Project** в контекстном меню. Появится диалоговое окно **Создать проект**.
3. Разверните узел **установлено** слева и разверните узел язык **Visual C++** .
4. перейдите в **Windows универсальный > holographic** и выберите **приложение holographic DirectX 11 (универсальное Windows) (C++/WinRT)**.
   ![снимок экрана шаблона проекта приложения UWP с/WinRTом DirectX 11 с + + в Visual Studio 2017](images/holographic-directx-app-cpp-new-project.png)<br>
   *шаблон проекта приложения UWP для DirectX 11/WinRT с + + в Visual Studio 2017*
   >[!IMPORTANT]
   >Убедитесь, что имя шаблона проекта содержит "(C++/WinRT)".  Если нет, то у вас установлена старая версия шаблонов проектов Holographic.  чтобы получить последние шаблоны проектов, [установите их](../install-the-tools.md) в качестве расширения Visual Studio 2017.
5. Заполните текстовые поля **имя** и **Расположение** , а затем выберите или нажмите **кнопку ОК**. Создается проект holographic приложения.
6. для целей разработки, предназначенных только для HoloLens 2, убедитесь, что для **целевой версии** и **минимальной версии** задано значение **Windows 10, версия 1903**.  если вы также настраиваете гарнитуры HoloLens (1-й номер) или настольные Windows Mixed Reality, можно задать для параметра **минимальная версия** значение **Windows 10, версия 1809**. Это потребует некоторых <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">адаптивных проверок версии</a> в коде при использовании новых функций HoloLens 2.
   ![снимок экрана: установка Windows 10, версия 1903 в качестве целевой и минимальной версий](images/new-uwp-project.png)<br>
   *настройка **Windows 10, версии 1903** в качестве целевой и минимальной версий*
   >[!IMPORTANT]
   >если вы не видите **Windows 10 версии 1903** , значит, не установлена последняя версия пакета SDK для Windows 10.  чтобы отобразить этот параметр, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">установите версию 10.0.18362.0 или более позднюю версию пакета SDK Windows 10</a>.

шаблон создает проект с помощью <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">c++/WinRT</a>, проекции языка c++ 17 api среда выполнения Windows, который поддерживает любой стандартно совместимый с c++ 17 компилятор.  В проекте показано, как создать куб, заблокированный в мире, который помещается на 2 метрах от пользователя. Пользователь может [прикоснуться воздушного](../../design/gaze-and-commit.md#composite-gestures) меню или нажать кнопку на контроллере, чтобы поместить куб в другую позицию, указанную с помощью [взгляда](../../design/gaze-and-commit.md)пользователя. Вы можете изменить этот проект, чтобы создать любое приложение смешанной реальности.

Вы также можете создать новый проект с помощью шаблона проекта **Visual C#** holographic, который основан на шарпдкс.  если проект с более holographic по C# не был запущен из шаблона Windows holographic, необходимо скопировать файл ms. фкскомпиле. targets из Windows Mixed Reality проекта шаблона C# и импортировать его в csproj-файл, чтобы скомпилировать файлы HLSL, добавленные в проект. шаблон Direct3D 12 также предоставляется в расширении Windows Mixed Realityных шаблонов приложений для Visual Studio.

ознакомьтесь [с использованием Visual Studio для развертывания и отладки](../advanced-concepts/using-visual-studio.md) для получения сведений о том, как создать и развернуть пример на HoloLens, пк с подключенным иммерсивное устройство или эмулятором.

В остальных инструкциях ниже предполагается, что вы используете C++ для создания приложения.

### <a name="uwp-app-entry-point"></a>Точка входа приложения UWP

Приложение holographic с UWP запускается в функции **wWinMain** в аппвиев. cpp. Функция **wWinMain** создает <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> приложения и запускает <a href="/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> с ним.

Из **аппвиев. cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

с этого момента класс аппвиев обрабатывает взаимодействие с Windows базовыми событиями ввода, событиями CoreWindow и обменом сообщениями и т. д. Он также создаст Холографикспаце, используемый приложением.

## <a name="creating-a-win32-project"></a>Создание проекта Win32

Самый простой способ приступить к созданию проекта Win32 holographic — адаптировать <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">пример *басичолограм* Win32</a>.

в этом примере Win32 используется <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">c++/WinRT</a>, проекция языка c++ 17 для среда выполнения Windows api-интерфейсов, поддерживающих любой стандарт, совместимый с c++ 17 компилятор.  В проекте показано, как создать куб, заблокированный в мире, который помещается на 2 метрах от пользователя. Пользователь может нажать кнопку на контроллере, чтобы поместить куб в другую позицию, указанную с помощью [взгляда](../../design/gaze-and-commit.md)пользователя. Вы можете изменить этот проект, чтобы создать любое приложение смешанной реальности.

### <a name="win32-app-entry-point"></a>Точка входа приложения Win32

Приложение с holographic Win32 запускается в функции **wWinMain** в аппмаин. cpp. Функция **wWinMain** создает HWND приложения и запускает его цикл обработки сообщений.

Из **аппмаин. cpp**:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

С этого момента класс Аппмаин обрабатывает взаимодействие с основными сообщениями окон и т. д. Он также создаст Холографикспаце, используемый приложением.

## <a name="render-holographic-content"></a>Прорисовка с holographic содержимым

Папка **содержимого** проекта содержит классы для отрисовки голограмм в [holographic пространстве](getting-a-holographicspace.md). Голограмма по умолчанию в шаблоне является вращающимся кубом, который располагается на расстоянии 2 метров от пользователя. Рисование этого Куба реализовано в **спиннингкуберендерер. cpp**, который имеет следующие ключевые методы:

|  Метод  |  Описание | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Загружает шейдеры и создает сетку Куба. | 
|  `PositionHologram` |  Помещает голограмму в расположение, указанное предоставленным <a href="/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">спатиалпоинтерпосе</a>. | 
|  `Update` |  Поворачивает куб и задает матрицу модели. | 
|  `Render` |  Визуализирует кадр с помощью шейдеров вершин и пикселей. | 

Вложенная папка **шейдеров** содержит четыре реализации шейдера по умолчанию:

|  Шейдер  |  Объяснение | 
|----------|----------|
|  `GeometryShader.hlsl` |  Сквозной объект, который оставляет геометрию неизменной. | 
|  `PixelShader.hlsl` |  Проходит через данные цвета. Данные цвета интерполируются и назначаются пикселу на шаге растрирования. | 
|  `VertexShader.hlsl` |  Простой шейдер для обработки вершин на GPU. | 
|  `VPRTVertexShader.hlsl` |  простой шейдер для обработки вершин на GPU, оптимизированный для Windows Mixed Realityного отображения стерео. | 

`VertexShaderShared.hlsl` содержит общий код, совместно используемый `VertexShader.hlsl` и `VPRTVertexShader.hlsl` .

Примечание. шаблон приложения Direct3D 12 также включает `ViewInstancingVertexShader.hlsl` . Этот вариант использует дополнительные функции D3D12 для более эффективного отображения стерео изображений.

Шейдеры компилируются при сборке проекта и загружаются в метод **спиннингкуберендерер:: креатедевицедепендентресаурцес** .

## <a name="interact-with-your-holograms"></a>Взаимодействие с голограммами

Входные данные пользователя обрабатываются в классе **спатиалинпусандлер** , который получает экземпляр <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">спатиалинтерактионманажер</a> и подписывается на событие <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">саурцепрессед</a> . Это позволяет обнаруживать жесты касания и другие пространственные события ввода.

## <a name="update-holographic-content"></a>Обновление holographic

Приложение смешанной реальности обновляется в цикле игры, который по умолчанию реализован в методе **Update** в `AppMain.cpp` . Метод **Update** обновляет объекты сцены, например вращающийся куб, и возвращает объект <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> , который используется для получения актуальных матриц представления и проекции, а также для представления цепочки буферов обмена.

Метод **Render** в `AppMain.cpp` принимает <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> и визуализирует текущий кадр на каждой из holographic камер в соответствии с текущим приложением и состоянием пространственного позиционирования.

## <a name="notes"></a>Примечания

шаблон приложения Windows Mixed Reality теперь поддерживает компиляцию с включенным флагом защиты устранением рисков spectre (/Qspectre). перед компиляцией конфигурации с включенным устранением устранением рисков spectre убедитесь, что установлена версия Microsoft Visual C++ (MSVC) библиотеки времени выполнения устранением рисков spectre. чтобы установить библиотеки C++ с устранением рисков spectre-смягчением, запустите Visual Studio Installer и выберите **изменить**. Перейдите к **отдельным компонентам** и выполните поиск по запросу "устранением рисков Spectre". выберите поля, соответствующие целевым платформам и MSVC версии, для которых необходимо скомпилировать код, снижающий опасность для, и нажмите кнопку **изменить** , чтобы начать установку.

## <a name="see-also"></a>См. также раздел
* [Получение HolographicSpace](getting-a-holographicspace.md)
* <a href="/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Отрисовка в DirectX](rendering-in-directx.md)
* [Развертывание и отладка с помощью Visual Studio](../advanced-concepts/using-visual-studio.md)
* [Использование эмулятора HoloLens](../advanced-concepts/using-the-hololens-emulator.md)
* [Использование XAML с голографическими приложениями DirectX](using-xaml-with-holographic-directx-apps.md)