---
title: WinRT в Unreal
description: Общие сведения о подключаемом модуле пространственного звука для Unreal Engine.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, потоковая передача, удаленное взаимодействие, смешанная реальность, разработка, начало работы, функции, новый проект, эмулятор, документация, руководства, функции, голограммы, разработка игр
ms.openlocfilehash: d7c94ebb7fc6cc16916f1f577b8e54e374b9db1f
ms.sourcegitcommit: e1de7caa7bd46afe9766186802fa4254d33d1ca6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/20/2020
ms.locfileid: "92240761"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="977f2-104">WinRT в Unreal</span><span class="sxs-lookup"><span data-stu-id="977f2-104">WinRT in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="977f2-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="977f2-105">Overview</span></span>

<span data-ttu-id="977f2-106">В процессе разработки HoloLens может потребоваться написать функцию с помощью WinRT.</span><span class="sxs-lookup"><span data-stu-id="977f2-106">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="977f2-107">Например, для открытия диалогового окна файла в приложении HoloLens потребуется Филесавепиккер в файле заголовка WinRT/Windows. Storage.. h.</span><span class="sxs-lookup"><span data-stu-id="977f2-107">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span>  <span data-ttu-id="977f2-108">Поскольку нереальность не компилирует код WinRT в машинном коде, это задание создает отдельный двоичный файл, который может использоваться в нереальной системе сборки.</span><span class="sxs-lookup"><span data-stu-id="977f2-108">Since Unreal doesn't natively compile WinRT code, it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="977f2-109">В этом учебнике рассматривается такой сценарий.</span><span class="sxs-lookup"><span data-stu-id="977f2-109">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="977f2-110">Цели</span><span class="sxs-lookup"><span data-stu-id="977f2-110">Objectives</span></span>
- <span data-ttu-id="977f2-111">Создание универсальной библиотеки DLL Windows, которая открывает Филесаведиалогуе</span><span class="sxs-lookup"><span data-stu-id="977f2-111">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="977f2-112">Связывание библиотеки DLL с нереальным игровым проектом</span><span class="sxs-lookup"><span data-stu-id="977f2-112">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="977f2-113">Сохранение файла на HoloLens из нереального проекта с помощью новой библиотеки DLL</span><span class="sxs-lookup"><span data-stu-id="977f2-113">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="977f2-114">Начало работы</span><span class="sxs-lookup"><span data-stu-id="977f2-114">Getting started</span></span>
1. <span data-ttu-id="977f2-115">Убедитесь, что установлены все [необходимые средства](tutorials/unreal-uxt-ch1.md) .</span><span class="sxs-lookup"><span data-stu-id="977f2-115">Check that you have all [required tools](tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="977f2-116">[Создайте новый проект с нереальным](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) именем и назовите его **консумевинрт**</span><span class="sxs-lookup"><span data-stu-id="977f2-116">[Create a new Unreal project](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="977f2-117">Включение [необходимых подключаемых модулей](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) для разработки HoloLens</span><span class="sxs-lookup"><span data-stu-id="977f2-117">Enable the [required plugins](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="977f2-118">[Установка для развертывания](tutorials/unreal-uxt-ch6.md) на устройстве или в эмуляторе</span><span class="sxs-lookup"><span data-stu-id="977f2-118">[Setup for deployment](tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="977f2-119">Создание библиотеки DLL WinRT</span><span class="sxs-lookup"><span data-stu-id="977f2-119">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="977f2-120">Откройте новый проект Visual Studio и создайте проект **DLL (универсальные приложения Windows)** в том же каталоге, в котором находится файл **упрожект** нереального игры.</span><span class="sxs-lookup"><span data-stu-id="977f2-120">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![Создание библиотеки DLL](images/unreal-winrt-img-01.png)

2. <span data-ttu-id="977f2-122">Присвойте проекту имя **хололенсвинртдлл** и задайте расположение в качестве подкаталога **сторонних** для файла упрожект нереальной игры.</span><span class="sxs-lookup"><span data-stu-id="977f2-122">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="977f2-123">Выберите **разместить решение и проект в том же каталоге** , чтобы упростить поиск путей в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="977f2-123">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Настройка библиотеки DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="977f2-125">После компиляции нового проекта необходимо обратить особое внимание на пустые файлы cpp и Header с именами **хололенсвинртдлл. cpp** и **хололенсвинртдлл. h** соответственно.</span><span class="sxs-lookup"><span data-stu-id="977f2-125">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="977f2-126">Заголовок — это включаемый файл, использующий библиотеку DLL в нереальном режиме, в то время как в cpp содержится текст всех экспортируемых функций, а также код WinRT, который в противном случае не может быть скомпилирован.</span><span class="sxs-lookup"><span data-stu-id="977f2-126">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="977f2-127">Перед добавлением кода необходимо обновить свойства проекта, чтобы убедиться, что необходимый код WinRT можно скомпилировать:</span><span class="sxs-lookup"><span data-stu-id="977f2-127">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="977f2-128">Щелкните правой кнопкой мыши проект Хололенсвинртдлл и выберите пункт **Свойства** .</span><span class="sxs-lookup"><span data-stu-id="977f2-128">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="977f2-129">В раскрывающемся списке **Конфигурация** укажите **все конфигурации** и раскрывающийся список **платформа** для **всех платформ** .</span><span class="sxs-lookup"><span data-stu-id="977f2-129">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="977f2-130">В разделе **Свойства конфигурации> C/C++> все параметры**:</span><span class="sxs-lookup"><span data-stu-id="977f2-130">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="977f2-131">Добавьте параметр **await** в **Дополнительные параметры** , чтобы убедиться, что мы можем ожидать асинхронные задачи.</span><span class="sxs-lookup"><span data-stu-id="977f2-131">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="977f2-132">Изменение **стандарта языка C++** на **ISO C++ 17 Standard (/std: C++ 17)** для включения любого кода WinRT</span><span class="sxs-lookup"><span data-stu-id="977f2-132">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Обновление свойств проекта](images/unreal-winrt-img-03.png)

<span data-ttu-id="977f2-134">Проект готов к обновлению источника библиотеки DLL с помощью кода WinRT, который открывает диалоговое окно файла и сохраняет файл на диск HoloLens.</span><span class="sxs-lookup"><span data-stu-id="977f2-134">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="977f2-135">Добавление кода DLL</span><span class="sxs-lookup"><span data-stu-id="977f2-135">Adding the DLL code</span></span>
1. <span data-ttu-id="977f2-136">Откройте **хололенсвинртдлл. h** и добавьте экспортированную функцию DLL для использования в нереальном виде:</span><span class="sxs-lookup"><span data-stu-id="977f2-136">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="977f2-137">Откройте **хололенсвинртдлл. cpp** и добавьте все заголовки, которые будет использовать класс:</span><span class="sxs-lookup"><span data-stu-id="977f2-137">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> <span data-ttu-id="977f2-138">Весь код WinRT хранится в **хололенсвинртдлл. cpp** , поэтому нереально не пытается включить какой-либо код WinRT при ссылке на заголовок.</span><span class="sxs-lookup"><span data-stu-id="977f2-138">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="977f2-139">По-прежнему в **хололенсвинртдлл. cpp**добавьте тело функции для опенфиледиалогуе () и весь поддерживаемый код:</span><span class="sxs-lookup"><span data-stu-id="977f2-139">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="977f2-140">Добавьте класс Савегамеманажер в файл **хололенсвинртдлл. cpp** , чтобы обрабатывал диалоговое окно файла и сохранить файл:</span><span class="sxs-lookup"><span data-stu-id="977f2-140">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullptr);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. <span data-ttu-id="977f2-141">Постройте решение для **выпуска > ARM64** , чтобы создать библиотеку DLL в дочернем каталоге ARM64/Release/хололенсвинртдлл из решения DLL.</span><span class="sxs-lookup"><span data-stu-id="977f2-141">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="977f2-142">Добавление двоичного файла WinRT в нереалию</span><span class="sxs-lookup"><span data-stu-id="977f2-142">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="977f2-143">Для связывания и использования библиотеки DLL в нереальном случае требуется проект C++.</span><span class="sxs-lookup"><span data-stu-id="977f2-143">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="977f2-144">Если вы используете проект схемы, его можно легко преобразовать в проект C++, добавив класс C++:</span><span class="sxs-lookup"><span data-stu-id="977f2-144">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="977f2-145">В нереальном редакторе откройте **файл > новый класс C++...**</span><span class="sxs-lookup"><span data-stu-id="977f2-145">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="977f2-146">и создайте новый **субъект** с именем **винртактор** для запуска кода в библиотеке DLL:</span><span class="sxs-lookup"><span data-stu-id="977f2-146">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Создание нового субъекта](images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="977f2-148">Теперь решение создано в том же каталоге, что и файл упрожект, а также новый скрипт сборки с именем Source/Консумевинрт/Консумевинрт. Build. cs.</span><span class="sxs-lookup"><span data-stu-id="977f2-148">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="977f2-149">Откройте решение, найдите папку **Games/консумевинрт/Source/консумевинрт** и откройте **ConsumeWinRT.Build.CS**:</span><span class="sxs-lookup"><span data-stu-id="977f2-149">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Открытие файла ConsumeWinRT.build.cs](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="977f2-151">Связывание библиотеки DLL</span><span class="sxs-lookup"><span data-stu-id="977f2-151">Linking the DLL</span></span>
1. <span data-ttu-id="977f2-152">В **ConsumeWinRT.Build.CS**добавьте свойство, чтобы найти путь включения для библиотеки DLL (каталог, содержащий хололенсвинртдлл. h).</span><span class="sxs-lookup"><span data-stu-id="977f2-152">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="977f2-153">Библиотека DLL находится в дочернем каталоге с путем include, поэтому это свойство будет использоваться в качестве двоичного корневого каталога:</span><span class="sxs-lookup"><span data-stu-id="977f2-153">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

```cs
using System.IO;

public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirdParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. <span data-ttu-id="977f2-154">В конструкторе класса добавьте следующий код, чтобы обновить путь включаемых файлов, связать новую библиотеку lib и загрузить отложенную загрузку и скопировать DLL в расположение пакета Appx:</span><span class="sxs-lookup"><span data-stu-id="977f2-154">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. <span data-ttu-id="977f2-155">Откройте **винртактор. h** и добавьте два определения функций, одну из которых может использовать схема, и другую, которая использует код DLL:</span><span class="sxs-lookup"><span data-stu-id="977f2-155">Open **WinrtActor.h** and add two function definitions, one that a blueprint can use and another that uses the DLL code:</span></span> 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. <span data-ttu-id="977f2-156">Откройте **винртактор. cpp** и загрузите DLL-файл в бегинплай:</span><span class="sxs-lookup"><span data-stu-id="977f2-156">Open **WinrtActor.cpp** and load the DLL in BeginPlay:</span></span> 

```cpp
void AWinfrtActor::BeginPlay()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> <span data-ttu-id="977f2-157">Библиотека DLL должна быть загружена перед вызовом любой из ее функций.</span><span class="sxs-lookup"><span data-stu-id="977f2-157">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="977f2-158">Создание игры</span><span class="sxs-lookup"><span data-stu-id="977f2-158">Building the game</span></span>
1. <span data-ttu-id="977f2-159">Выполните сборку решения игры, чтобы запустить нереальный редактор, Открытый для игрового проекта:</span><span class="sxs-lookup"><span data-stu-id="977f2-159">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="977f2-160">На вкладке **Размещение субъектов** найдите новый **винртактор** и перетащите его в сцену.</span><span class="sxs-lookup"><span data-stu-id="977f2-160">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="977f2-161">Откройте проект уровня, чтобы выполнить вызываемую функцию схемы в **винртактор** .</span><span class="sxs-lookup"><span data-stu-id="977f2-161">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Размещение Винртактор в сцене](images/unreal-winrt-img-06.png)

2. <span data-ttu-id="977f2-163">В **мировом мире**найдите **виндртактор** , ранее вставленный в сцену, и перетащите его в проект уровня:</span><span class="sxs-lookup"><span data-stu-id="977f2-163">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Перетаскивание Винртактор в схему уровня](images/unreal-winrt-img-07.png)

3. <span data-ttu-id="977f2-165">В схеме уровня перетащите выходной узел из Винртактор, найдите **диалоговое окно Открыть файл**, а затем направьте узел от любого пользовательского ввода.</span><span class="sxs-lookup"><span data-stu-id="977f2-165">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="977f2-166">В этом случае диалоговое окно открытия файла вызывается из события речи:</span><span class="sxs-lookup"><span data-stu-id="977f2-166">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Настройка узлов в проекте уровня](images/unreal-winrt-img-08.png)

4. <span data-ttu-id="977f2-168">[Упакуйте эту игру для HoloLens](tutorials/unreal-uxt-ch6.md), разверните ее и запустите.</span><span class="sxs-lookup"><span data-stu-id="977f2-168">[Package this game for HoloLens](tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="977f2-169">Когда недействительные вызовы Опенфиледиалогуе, открывается диалоговое окно файла на странице HoloLens, в которой запрашивается имя файла. txt.</span><span class="sxs-lookup"><span data-stu-id="977f2-169">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="977f2-170">После сохранения файла перейдите на вкладку " **проводник** " на портале устройств, чтобы просмотреть содержимое "Hello WinRT".</span><span class="sxs-lookup"><span data-stu-id="977f2-170">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="977f2-171">Сводка</span><span class="sxs-lookup"><span data-stu-id="977f2-171">Summary</span></span> 

<span data-ttu-id="977f2-172">Мы рекомендуем использовать код из этого руководства в качестве отправной точки для использования кода WinRT в нереальном виде.</span><span class="sxs-lookup"><span data-stu-id="977f2-172">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="977f2-173">Он позволяет пользователям сохранять файлы на диск HoloLens, используя тот же диалог, что и Windows.</span><span class="sxs-lookup"><span data-stu-id="977f2-173">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="977f2-174">Выполните те же действия, чтобы экспортировать дополнительные функции из заголовка Хололенсвинртдлл и использовать их в нереальном виде.</span><span class="sxs-lookup"><span data-stu-id="977f2-174">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="977f2-175">Обратите внимание на код DLL, который ожидает любой асинхронный код WinRT в фоновом потоке агента передачи сообщений, что позволяет избежать взаимоблокировки нереального игрового потока.</span><span class="sxs-lookup"><span data-stu-id="977f2-175">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

## <a name="next-development-checkpoint"></a><span data-ttu-id="977f2-176">Следующий этап разработки</span><span class="sxs-lookup"><span data-stu-id="977f2-176">Next Development Checkpoint</span></span>

<span data-ttu-id="977f2-177">Если вы следуете изложенным нами этапам разработки для Unreal, вы как раз прошли половину в изучении возможностей и API платформы смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="977f2-177">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="977f2-178">Здесь можно перейти к любому [разделу](unreal-development-overview.md#3-platform-capabilities-and-apis) или перейти непосредственно к развертыванию приложения на устройстве или в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="977f2-178">From here, you can proceed to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="977f2-179">Развертывание на устройстве</span><span class="sxs-lookup"><span data-stu-id="977f2-179">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="977f2-180">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="977f2-180">See also</span></span>
* [<span data-ttu-id="977f2-181">API-интерфейсы/WinRT C++</span><span class="sxs-lookup"><span data-stu-id="977f2-181">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="977f2-182">Класс Филесавепиккер</span><span class="sxs-lookup"><span data-stu-id="977f2-182">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="977f2-183">Нереал. сторонние библиотеки</span><span class="sxs-lookup"><span data-stu-id="977f2-183">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
