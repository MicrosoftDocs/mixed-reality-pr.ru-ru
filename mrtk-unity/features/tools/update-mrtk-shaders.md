---
title: Средство обновления шейдеров
description: Документация по обновлению стандартных шейдеров МРТК
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 1f943d8ac7050b8607ae3a85af0a377a7460eb3b
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647099"
---
# <a name="updating-shaders"></a><span data-ttu-id="6be3a-104">Обновление шейдеров</span><span class="sxs-lookup"><span data-stu-id="6be3a-104">Updating Shaders</span></span>

<span data-ttu-id="6be3a-105">Начиная с версии 2.6.0, шейдеры МРТК имеют версию с помощью МРТК. Файл шейдеров. Sentinel.</span><span class="sxs-lookup"><span data-stu-id="6be3a-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="6be3a-106">При обновлении до новой версии МРТК может появиться следующее сообщение.</span><span class="sxs-lookup"><span data-stu-id="6be3a-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![Запрос на обновление шейдеров](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="6be3a-108">Если выбрать **Да** , мртк будет перезаписывать содержимое   >  **мрткных**  >  **шейдеров** с последней версией.</span><span class="sxs-lookup"><span data-stu-id="6be3a-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="6be3a-109">Если выбрать значение **нет** , текущие файлы будут сохранены.</span><span class="sxs-lookup"><span data-stu-id="6be3a-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="6be3a-110">**Игнорировать** создаст файл ( `IgnoreUpdateCheck.sentinel` ) в   >  **мртке**"активы"  >  , что приведет к подавлению проверок последующего обновления шейдера.</span><span class="sxs-lookup"><span data-stu-id="6be3a-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6be3a-111">При перезаписи файлов шейдера все пользовательские изменения будут потеряны.</span><span class="sxs-lookup"><span data-stu-id="6be3a-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="6be3a-112">Перед обновлением обязательно создайте резервную копию всех измененных файлов шейдера.</span><span class="sxs-lookup"><span data-stu-id="6be3a-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="6be3a-113">Если в проекте настроено использование универсального конвейера отрисовки (URP), прежнего (лврп), то необходимо повторно запустить служебные программы с пакетом управления для **смешанной реальности** >  >  >
>  **Обновление мртк Стандартный шейдер для упрощенного конвейера отрисовки**.</span><span class="sxs-lookup"><span data-stu-id="6be3a-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality** > **Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="6be3a-114">Кроме того, в любое время можно проверить наличие обновлений шейдеров с помощью   >    >  **служебных программ** набора средств смешанной реальности  >  **для обновления шейдеров** в строке меню редактора Unity.</span><span class="sxs-lookup"><span data-stu-id="6be3a-114">At is also possible to check for shader updates at any time using **Mixed Reality** > **Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![Проверка наличия обновлений шейдеров](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="6be3a-116">Проверка того, что **обновления шейдеров** отменяют `IgnoreUpdateCheck.sentinel` файл, и обеспечивает обновление шейдера по запросу.</span><span class="sxs-lookup"><span data-stu-id="6be3a-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="6be3a-117">Проверка наличия обновлений шейдера не требуется при импорте файлов МРТК. пакет unitypackage.</span><span class="sxs-lookup"><span data-stu-id="6be3a-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
