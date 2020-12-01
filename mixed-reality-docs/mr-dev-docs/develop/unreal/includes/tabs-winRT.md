---
ms.openlocfilehash: fd44d63ad502b6807c6aa18ce6fc63493fc254dc
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354450"
---
# <a name="425"></a>[<span data-ttu-id="7887c-101">4.25</span><span class="sxs-lookup"><span data-stu-id="7887c-101">4.25</span></span>](#tab/425)

<span data-ttu-id="7887c-102">«Нереалия» не компилирует код WinRT в версии 4,25, поэтому задание создает отдельный двоичный файл, который может использоваться в нереальной системе сборки.</span><span class="sxs-lookup"><span data-stu-id="7887c-102">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="7887c-103">В этом учебнике рассматривается такой сценарий.</span><span class="sxs-lookup"><span data-stu-id="7887c-103">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="7887c-104">Задачи</span><span class="sxs-lookup"><span data-stu-id="7887c-104">Objectives</span></span>
- <span data-ttu-id="7887c-105">Создание универсальной библиотеки DLL Windows, которая открывает Филесаведиалогуе</span><span class="sxs-lookup"><span data-stu-id="7887c-105">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="7887c-106">Связывание библиотеки DLL с нереальным игровым проектом</span><span class="sxs-lookup"><span data-stu-id="7887c-106">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="7887c-107">Сохранение файла на HoloLens из нереального проекта с помощью новой библиотеки DLL</span><span class="sxs-lookup"><span data-stu-id="7887c-107">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="7887c-108">Начало работы</span><span class="sxs-lookup"><span data-stu-id="7887c-108">Getting started</span></span>
1. <span data-ttu-id="7887c-109">Убедитесь, что установлены все [необходимые средства](../tutorials/unreal-uxt-ch1.md) .</span><span class="sxs-lookup"><span data-stu-id="7887c-109">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="7887c-110">[Создайте новый проект с нереальным](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) именем и назовите его **консумевинрт**</span><span class="sxs-lookup"><span data-stu-id="7887c-110">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="7887c-111">Включение [необходимых подключаемых модулей](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) для разработки HoloLens</span><span class="sxs-lookup"><span data-stu-id="7887c-111">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="7887c-112">[Установка для развертывания](../tutorials/unreal-uxt-ch6.md) на устройстве или в эмуляторе</span><span class="sxs-lookup"><span data-stu-id="7887c-112">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="7887c-113">Создание библиотеки DLL WinRT</span><span class="sxs-lookup"><span data-stu-id="7887c-113">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="7887c-114">Откройте новый проект Visual Studio и создайте проект **DLL (универсальные приложения Windows)** в том же каталоге, в котором находится файл **упрожект** нереального игры.</span><span class="sxs-lookup"><span data-stu-id="7887c-114">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![Создание библиотеки DLL](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="7887c-116">Присвойте проекту имя **хололенсвинртдлл** и задайте расположение в качестве подкаталога **сторонних** для файла упрожект нереальной игры.</span><span class="sxs-lookup"><span data-stu-id="7887c-116">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="7887c-117">Выберите **разместить решение и проект в том же каталоге** , чтобы упростить поиск путей в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="7887c-117">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Настройка библиотеки DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="7887c-119">После компиляции нового проекта необходимо обратить особое внимание на пустые файлы cpp и Header с именами **хололенсвинртдлл. cpp** и **хололенсвинртдлл. h** соответственно.</span><span class="sxs-lookup"><span data-stu-id="7887c-119">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="7887c-120">Заголовок — это включаемый файл, использующий библиотеку DLL в нереальном режиме, в то время как в cpp содержится текст всех экспортируемых функций, а также код WinRT, который в противном случае не может быть скомпилирован.</span><span class="sxs-lookup"><span data-stu-id="7887c-120">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="7887c-121">Перед добавлением кода необходимо обновить свойства проекта, чтобы убедиться, что необходимый код WinRT можно скомпилировать:</span><span class="sxs-lookup"><span data-stu-id="7887c-121">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="7887c-122">Щелкните правой кнопкой мыши проект Хололенсвинртдлл и выберите пункт **Свойства** .</span><span class="sxs-lookup"><span data-stu-id="7887c-122">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="7887c-123">В раскрывающемся списке **Конфигурация** укажите **все конфигурации** и раскрывающийся список **платформа** для **всех платформ** .</span><span class="sxs-lookup"><span data-stu-id="7887c-123">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="7887c-124">В разделе **Свойства конфигурации> C/C++> все параметры**:</span><span class="sxs-lookup"><span data-stu-id="7887c-124">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="7887c-125">Добавьте параметр **await** в **Дополнительные параметры** , чтобы убедиться, что мы можем ожидать асинхронные задачи.</span><span class="sxs-lookup"><span data-stu-id="7887c-125">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="7887c-126">Изменение **стандарта языка C++** на **ISO C++ 17 Standard (/std: C++ 17)** для включения любого кода WinRT</span><span class="sxs-lookup"><span data-stu-id="7887c-126">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Обновление свойств проекта](../images/unreal-winrt-img-03.png)

<span data-ttu-id="7887c-128">Проект готов к обновлению источника библиотеки DLL с помощью кода WinRT, который открывает диалоговое окно файла и сохраняет файл на диск HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7887c-128">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="7887c-129">Добавление кода DLL</span><span class="sxs-lookup"><span data-stu-id="7887c-129">Adding the DLL code</span></span>
1. <span data-ttu-id="7887c-130">Откройте **хололенсвинртдлл. h** и добавьте экспортированную функцию DLL для использования в нереальном виде:</span><span class="sxs-lookup"><span data-stu-id="7887c-130">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="7887c-131">Откройте **хололенсвинртдлл. cpp** и добавьте все заголовки, которые будет использовать класс:</span><span class="sxs-lookup"><span data-stu-id="7887c-131">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="7887c-132">Весь код WinRT хранится в **хололенсвинртдлл. cpp** , поэтому нереально не пытается включить какой-либо код WinRT при ссылке на заголовок.</span><span class="sxs-lookup"><span data-stu-id="7887c-132">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="7887c-133">По-прежнему в **хололенсвинртдлл. cpp** добавьте тело функции для опенфиледиалогуе () и весь поддерживаемый код:</span><span class="sxs-lookup"><span data-stu-id="7887c-133">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="7887c-134">Добавьте класс Савегамеманажер в файл **хололенсвинртдлл. cpp** , чтобы обрабатывал диалоговое окно файла и сохранить файл:</span><span class="sxs-lookup"><span data-stu-id="7887c-134">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="7887c-135">Постройте решение для **выпуска > ARM64** , чтобы создать библиотеку DLL в дочернем каталоге ARM64/Release/хололенсвинртдлл из решения DLL.</span><span class="sxs-lookup"><span data-stu-id="7887c-135">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="7887c-136">Добавление двоичного файла WinRT в нереалию</span><span class="sxs-lookup"><span data-stu-id="7887c-136">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="7887c-137">Для связывания и использования библиотеки DLL в нереальном случае требуется проект C++.</span><span class="sxs-lookup"><span data-stu-id="7887c-137">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="7887c-138">Если вы используете проект схемы, его можно легко преобразовать в проект C++, добавив класс C++:</span><span class="sxs-lookup"><span data-stu-id="7887c-138">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="7887c-139">В нереальном редакторе откройте **файл > новый класс C++...**</span><span class="sxs-lookup"><span data-stu-id="7887c-139">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="7887c-140">и создайте новый **субъект** с именем **винртактор** для запуска кода в библиотеке DLL:</span><span class="sxs-lookup"><span data-stu-id="7887c-140">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Создание нового субъекта](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="7887c-142">Теперь решение создано в том же каталоге, что и файл упрожект, а также новый скрипт сборки с именем Source/Консумевинрт/Консумевинрт. Build. cs.</span><span class="sxs-lookup"><span data-stu-id="7887c-142">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="7887c-143">Откройте решение, найдите папку **Games/консумевинрт/Source/консумевинрт** и откройте **ConsumeWinRT.Build.CS**:</span><span class="sxs-lookup"><span data-stu-id="7887c-143">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Открытие файла ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="7887c-145">Связывание библиотеки DLL</span><span class="sxs-lookup"><span data-stu-id="7887c-145">Linking the DLL</span></span>
1. <span data-ttu-id="7887c-146">В **ConsumeWinRT.Build.CS** добавьте свойство, чтобы найти путь включения для библиотеки DLL (каталог, содержащий хололенсвинртдлл. h).</span><span class="sxs-lookup"><span data-stu-id="7887c-146">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="7887c-147">Библиотека DLL находится в дочернем каталоге с путем include, поэтому это свойство будет использоваться в качестве двоичного корневого каталога:</span><span class="sxs-lookup"><span data-stu-id="7887c-147">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="7887c-148">В конструкторе класса добавьте следующий код, чтобы обновить путь включаемых файлов, связать новую библиотеку lib и загрузить отложенную загрузку и скопировать DLL в расположение пакета Appx:</span><span class="sxs-lookup"><span data-stu-id="7887c-148">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="7887c-149">Откройте **винртактор. h** и добавьте одно определение функции, которое будет вызываться чертежом:</span><span class="sxs-lookup"><span data-stu-id="7887c-149">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="7887c-150">Откройте **винртактор. cpp** и обновите бегинплай, чтобы загрузить библиотеку DLL:</span><span class="sxs-lookup"><span data-stu-id="7887c-150">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

```cpp
void AWinrtActor::BeginPlay()
{
    Super::BeginPlay();

    // Gets path to DLL location
    const FString BinDir = FPaths::ProjectDir() / 
        "ThirdParty" / "HoloLensWinrtDLL" / 
        "arm64" / "Release" / "HoloLensWinrtDLL";

    // Loads DLL into application
    void * dllHandle = FPlatformProcess::GetDllHandle(
        *(BinDir / "HoloLensWinrtDLL.dll"));
}

void AWinrtActor::OpenFileDialogue()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> <span data-ttu-id="7887c-151">Библиотека DLL должна быть загружена перед вызовом любой из ее функций.</span><span class="sxs-lookup"><span data-stu-id="7887c-151">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="7887c-152">Создание игры</span><span class="sxs-lookup"><span data-stu-id="7887c-152">Building the game</span></span>
1. <span data-ttu-id="7887c-153">Выполните сборку решения игры, чтобы запустить нереальный редактор, Открытый для игрового проекта:</span><span class="sxs-lookup"><span data-stu-id="7887c-153">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="7887c-154">На вкладке **Размещение субъектов** найдите новый **винртактор** и перетащите его в сцену.</span><span class="sxs-lookup"><span data-stu-id="7887c-154">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="7887c-155">Откройте проект уровня, чтобы выполнить вызываемую функцию схемы в **винртактор** .</span><span class="sxs-lookup"><span data-stu-id="7887c-155">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Размещение Винртактор в сцене](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="7887c-157">В **мировом мире** найдите **виндртактор** , ранее вставленный в сцену, и перетащите его в проект уровня:</span><span class="sxs-lookup"><span data-stu-id="7887c-157">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Перетаскивание Винртактор в схему уровня](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="7887c-159">В схеме уровня перетащите выходной узел из Винртактор, найдите **диалоговое окно Открыть файл**, а затем направьте узел от любого пользовательского ввода.</span><span class="sxs-lookup"><span data-stu-id="7887c-159">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="7887c-160">В этом случае диалоговое окно открытия файла вызывается из события речи:</span><span class="sxs-lookup"><span data-stu-id="7887c-160">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Настройка узлов в проекте уровня](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="7887c-162">[Упакуйте эту игру для HoloLens](../tutorials/unreal-uxt-ch6.md), разверните ее и запустите.</span><span class="sxs-lookup"><span data-stu-id="7887c-162">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="7887c-163">Когда недействительные вызовы Опенфиледиалогуе, открывается диалоговое окно файла на странице HoloLens, в которой запрашивается имя файла. txt.</span><span class="sxs-lookup"><span data-stu-id="7887c-163">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="7887c-164">После сохранения файла перейдите на вкладку " **проводник** " на портале устройств, чтобы просмотреть содержимое "Hello WinRT".</span><span class="sxs-lookup"><span data-stu-id="7887c-164">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="7887c-165">Итоги</span><span class="sxs-lookup"><span data-stu-id="7887c-165">Summary</span></span> 

<span data-ttu-id="7887c-166">Мы рекомендуем использовать код из этого руководства в качестве отправной точки для использования кода WinRT в нереальном виде.</span><span class="sxs-lookup"><span data-stu-id="7887c-166">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="7887c-167">Он позволяет пользователям сохранять файлы на диск HoloLens, используя тот же диалог, что и Windows.</span><span class="sxs-lookup"><span data-stu-id="7887c-167">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="7887c-168">Выполните те же действия, чтобы экспортировать дополнительные функции из заголовка Хололенсвинртдлл и использовать их в нереальном виде.</span><span class="sxs-lookup"><span data-stu-id="7887c-168">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="7887c-169">Обратите внимание на код DLL, который ожидает любой асинхронный код WinRT в фоновом потоке агента передачи сообщений, что позволяет избежать взаимоблокировки нереального игрового потока.</span><span class="sxs-lookup"><span data-stu-id="7887c-169">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

# <a name="426"></a>[<span data-ttu-id="7887c-170">4,26</span><span class="sxs-lookup"><span data-stu-id="7887c-170">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="7887c-171">Стандартные API-интерфейсы WinRT</span><span class="sxs-lookup"><span data-stu-id="7887c-171">The standard WinRT APIs</span></span>

<span data-ttu-id="7887c-172">Наиболее распространенным и простым способом использования WinRT является вызов методов из WinSDK.</span><span class="sxs-lookup"><span data-stu-id="7887c-172">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="7887c-173">Для этого откройте файл YourModule.Build.cs и добавьте следующие строки:</span><span class="sxs-lookup"><span data-stu-id="7887c-173">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

```cpp
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // These parameters are mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string[] { "shlwapi.lib", "runtimeobject.lib" });
    PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir,        
                                        "Include", 
                                        Target.WindowsPlatform.WindowsSdkVersion, 
                                        "cppwinrt"));
}
```

<span data-ttu-id="7887c-174">Далее необходимо добавить следующие заголовки WinRT:</span><span class="sxs-lookup"><span data-stu-id="7887c-174">Next, you need to add the following WinRT headers:</span></span> 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
#include "Windows/AllowWindowsPlatformTypes.h"
#include "Windows/AllowWindowsPlatformAtomics.h"
#include "Windows/PreWindowsApi.h"

#include <unknwn.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Perception.Spatial.h>
#include <winrt/Windows.Foundation.Collections.h>

#include "Windows/PostWindowsApi.h"
#include "Windows/HideWindowsPlatformAtomics.h"
#include "Windows/HideWindowsPlatformTypes.h"
#endif
```

<span data-ttu-id="7887c-175">Код WinRT можно скомпилировать только на платформах Win64 и HoloLens, поэтому инструкция if предотвращает включение библиотек WinRT на другие платформы.</span><span class="sxs-lookup"><span data-stu-id="7887c-175">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="7887c-176">ункнвн. h был добавлен для интерфейса IUnknown.</span><span class="sxs-lookup"><span data-stu-id="7887c-176">unknwn.h was added for having the IUnknown interface.</span></span> 

<span data-ttu-id="7887c-177">Перед написанием кода необходимо отключить общие предупреждения в заголовках WinRT с помощью:</span><span class="sxs-lookup"><span data-stu-id="7887c-177">Before writing any code, you need to disable common warnings in WinRT headers by using:</span></span>

```cpp
#pragma warning(disable : 5205 4265)
```

## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="7887c-178">WinRT из пакета NuGet</span><span class="sxs-lookup"><span data-stu-id="7887c-178">WinRT from a NuGet package</span></span>

<span data-ttu-id="7887c-179">Это немного усложняется, если необходимо добавить пакет NuGet с поддержкой WinRT.</span><span class="sxs-lookup"><span data-stu-id="7887c-179">It’s a little more complicated if you need to add a nuget package with WinRT support.</span></span> <span data-ttu-id="7887c-180">В этом случае Visual Studio может выполнять практически все задания, но нереалная система сборки не может.</span><span class="sxs-lookup"><span data-stu-id="7887c-180">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="7887c-181">К счастью, это не слишком сложная задача.</span><span class="sxs-lookup"><span data-stu-id="7887c-181">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="7887c-182">Ниже приведен пример того, как можно скачать пакет Microsoft. Микседреалити. QR.</span><span class="sxs-lookup"><span data-stu-id="7887c-182">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="7887c-183">Вы можете заменить его другим, просто убедитесь, что файл WinMD не утерян, и скопируйте правильную библиотеку DLL.</span><span class="sxs-lookup"><span data-stu-id="7887c-183">You can replace it with another, just make sure that you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="7887c-184">Windows SDK библиотеки DLL из предыдущего раздела обрабатываются операционной системой.</span><span class="sxs-lookup"><span data-stu-id="7887c-184">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="7887c-185">Библиотеки DLL NuGet должны управляться кодом в модуле.</span><span class="sxs-lookup"><span data-stu-id="7887c-185">Nuget’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="7887c-186">Необходимо добавить код, чтобы скачать их, скопировать в папку двоичных файлов и загрузить в память процесса при запуске модуля.</span><span class="sxs-lookup"><span data-stu-id="7887c-186">You should add code to download them, copy into binaries folder and load into the process memory at the module startup.</span></span>

<span data-ttu-id="7887c-187">На первом шаге следует добавить packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) в корневую папку модуля.</span><span class="sxs-lookup"><span data-stu-id="7887c-187">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="7887c-188">Необходимо добавить все пакеты, которые необходимо скачать, включая все их зависимости.</span><span class="sxs-lookup"><span data-stu-id="7887c-188">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="7887c-189">Здесь я добавил Microsoft. Микседреалити. QR как основную полезную нагрузку, а два других — как зависимости.</span><span class="sxs-lookup"><span data-stu-id="7887c-189">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="7887c-190">Формат этого файла такой же, как в Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="7887c-190">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="7887c-191">Теперь вы можете скачать NuGet, необходимые пакеты или обратиться к [документации](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)по NuGet.</span><span class="sxs-lookup"><span data-stu-id="7887c-191">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="7887c-192">Откройте YourModule.Build.cs и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="7887c-192">Open YourModule.Build.cs and add the following code:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    string MyModuleName = GetType().Name;

    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.Add("shlwapi.lib");
    PublicSystemLibraries.Add("runtimeobject.lib");

    // prepare everything for nuget
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

            PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if(!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
                                myWebClient.DownloadFile(@"https://dist.nuget.org/win-x86-commandline/latest/nuget.exe", NugetExe);
        }
    }

    // run nuget to update the packages
    {
        var StartInfo = new System.Diagnostics.ProcessStartInfo(NugetExe, string.Format("install \"{0}\" -OutputDirectory \"{1}\"", Path.Combine(ModuleDirectory, "packages.config"), NugetFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get nuget packages.  See log for details.");
        }
    }
            
    // get list of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] {'\r', '\n' });

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if(!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // search all downloaded packages for winmd files
        string[] WinMDFiles = Directory.GetFiles(NugetFolder, "*.winmd", SearchOption.AllDirectories);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach(var winmd in WinMDFiles)
        {
            WinMDFilesStringbuilder.Append(" -input \"");
            WinMDFilesStringbuilder.Append(winmd);
            WinMDFilesStringbuilder.Append("\"");
        }

        // generate winrt headers and add them into include paths
        var StartInfo = new System.Diagnostics.ProcessStartInfo(CppWinRTExe, string.Format("{0} -input \"{1}\" -output \"{2}\"", WinMDFilesStringbuilder, Target.WindowsPlatform.WindowsSdkVersion, CppWinRTFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get generate WinRT headers.  See log for details.");
        }

        PrivateIncludePaths.Add(CppWinRTFolder);

    }
    else
    {
        // fall to default WinSDK headers
                        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
            }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        SafeCopy(Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd"), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));
    }

    if(Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
        if (!string.IsNullOrEmpty(VCRTForwardersPackage))
        {
            string VCRTForwardersName = VCRTForwardersPackage.Replace(" ", ".");
            foreach (var Dll in Directory.EnumerateFiles(Path.Combine(NugetFolder, VCRTForwardersName, "runtimes/win10-x64/native/release"), "*_app.dll"))
            {
                string newDll = Path.Combine(BinariesFolder, Path.GetFileName(Dll));
                SafeCopy(Dll, newDll);
                RuntimeDependencies.Add(newDll);
            }
        }
    }
```

<span data-ttu-id="7887c-193">Необходимо определить метод Сафекопи следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7887c-193">You'll need to define the SafeCopy method as follows:</span></span>

```cpp
private void SafeCopy(string source, string destination)
{
    if(!File.Exists(source))
    {
        Log.TraceError("Class {0} can't find {1} file for copying", this.GetType().Name, source);
        return;
    }

    try
    {
        File.Copy(source, destination, true);
    }
    catch(IOException ex)
    {
        Log.TraceWarning("Failed to copy {0} to {1} with exception: {2}", source, destination, ex.Message);
        if (!File.Exists(destination))
        {
            Log.TraceError("Destination file {0} does not exist", destination);
            return;
        }

        Log.TraceWarning("Destination file {0} already existed and is probably in use.  The old file will be used for the runtime dependency.  This may happen when packaging a Win64 exe from the editor.", destination);
    }
}
```

<span data-ttu-id="7887c-194">Библиотеки DLL NuGet должны загружаться в память процесса Win32 вручную.</span><span class="sxs-lookup"><span data-stu-id="7887c-194">Nuget DLLs needs to load into your Win32 process memory manually.</span></span> <span data-ttu-id="7887c-195">Необходимо добавить ручную загрузку в метод запуска модуля:</span><span class="sxs-lookup"><span data-stu-id="7887c-195">You should add manual loading into the startup method of your module:</span></span>

```cpp
void StartupModule() override
{
#if PLATFORM_WINDOWS
    const FString LibrariesDir = FPaths::ProjectPluginsDir() / "MyModule" / THIRDPARTY_BINARY_SUBFOLDER;
    FPlatformProcess::PushDllDirectory(*LibrariesDir);

    const FString DllName = "Microsoft.MixedReality.QR.dll";
    if (!FPlatformProcess::GetDllHandle(*DllName))
    {
        UE_LOG(LogHMD, Warning, TEXT("Dll \'%s\' can't be loaded from \'%s\'"), *DllName, *LibrariesDir);
    }

    FPlatformProcess::PopDllDirectory(*LibrariesDir);
#endif
}
```

<span data-ttu-id="7887c-196">Наконец, можно включить заголовки WinRT в код, как описано в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="7887c-196">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>