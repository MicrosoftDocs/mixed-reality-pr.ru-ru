---
title: Авторизация изменений в проекте
description: Узнайте, как авторизовать изменения в проекте с помощью Mixed Reality Feature Tool при разработке решений для HoloLens и виртуальной реальности.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: db7ae079e19c7739f57f0b9e4a375a3e6f9a3cdd
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230788"
---
# <a name="authorizing-project-changes"></a><span data-ttu-id="2c94d-104">Авторизация изменений в проекте</span><span class="sxs-lookup"><span data-stu-id="2c94d-104">Authorizing project changes</span></span>

<span data-ttu-id="2c94d-105">Перед внесением изменений в проект Unity необходимо проверить и утвердить все изменения в файлах манифеста и проекта.</span><span class="sxs-lookup"><span data-stu-id="2c94d-105">Before modifying the Unity project, changes to the manifest and project files need to be reviewed and approved:</span></span>

![Запрос на авторизацию](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a><span data-ttu-id="2c94d-107">манифеста</span><span class="sxs-lookup"><span data-stu-id="2c94d-107">Manifest</span></span>

<span data-ttu-id="2c94d-108">Предложенные изменения манифеста можно просмотреть в столбце **Manifest** (Манифест) слева.</span><span class="sxs-lookup"><span data-stu-id="2c94d-108">The proposed manifest changes can be viewed in the **Manifest** column on the left.</span></span> <span data-ttu-id="2c94d-109">Его содержимое будет в точности записано в манифест проекта (**Packages/manifest.json**):</span><span class="sxs-lookup"><span data-stu-id="2c94d-109">The contents are exactly what will be written to the project manifest (**Packages/manifest.json**):</span></span>

![Предварительный просмотр манифеста](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a><span data-ttu-id="2c94d-111">Файлы, которые будут скопированы в проект</span><span class="sxs-lookup"><span data-stu-id="2c94d-111">Files to be copied into the project</span></span>

<span data-ttu-id="2c94d-112">В разделе **Files to be copied into the project** (Файлы, которые будут скопированы в проект) справа представлен список конкретных файлов пакетов функций, которые будут скопированы в проект Unity:</span><span class="sxs-lookup"><span data-stu-id="2c94d-112">The **Files to be copied into the project** section on the right lists the specific feature package files that will be copied into the Unity project:</span></span>

![Предварительный просмотр манифеста и файлов, которые будут скопированы](images/FilesToCopy.png)

## <a name="compare-manifests"></a><span data-ttu-id="2c94d-114">Сравнение манифестов</span><span class="sxs-lookup"><span data-stu-id="2c94d-114">Compare manifests</span></span>

<span data-ttu-id="2c94d-115">Вы можете сравнить версии всех предлагаемых изменений, выбрав **Compare** (Сравнить).</span><span class="sxs-lookup"><span data-stu-id="2c94d-115">You can see a detailed side-by-side comparison of all proposed changes by selecting **Compare**:</span></span>

![Сравнение манифестов](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a><span data-ttu-id="2c94d-117">Утверждение изменений</span><span class="sxs-lookup"><span data-stu-id="2c94d-117">Approving changes</span></span>

<span data-ttu-id="2c94d-118">Когда вы утвердите предложенные изменения, включенные в список файлы будут скопированы в проект Unity, а в манифест будут добавлены ссылки на эти файлы.</span><span class="sxs-lookup"><span data-stu-id="2c94d-118">When the proposed changes are approved, the listed files will be copied into the Unity project and the manifest will be updated with references to these files.</span></span>

> [!NOTE]
> <span data-ttu-id="2c94d-119">Файлы пакетов функций (\*.tgz) нужно добавить в систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="2c94d-119">The feature package (\*.tgz) files should be added to source control.</span></span> <span data-ttu-id="2c94d-120">Ссылки на них указываются в формате относительного пути, что позволяет группам разработчиков легко предоставлять общий доступ к изменениям функций и манифестов.</span><span class="sxs-lookup"><span data-stu-id="2c94d-120">They are referenced using a relative path to enable development teams to easily share features and manifest changes.</span></span>

 <span data-ttu-id="2c94d-121">В процессе изменений будет создана резервная копия текущего файла **manifest.json**.</span><span class="sxs-lookup"><span data-stu-id="2c94d-121">As part of the modifications, the current **manifest.json** file will be backed up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c94d-122">В списке резервных копий манифеста самая старая всегда имеет имя **manifest.json.backup**.</span><span class="sxs-lookup"><span data-stu-id="2c94d-122">When viewing the manifest backups, the oldest will be called **manifest.json.backup**.</span></span> <span data-ttu-id="2c94d-123">Более новые резервные копии дополняются числовыми значениями, начиная с нуля (0).</span><span class="sxs-lookup"><span data-stu-id="2c94d-123">Newer backups will be annotated with a numeric value, beginning with zero (0).</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="2c94d-124">Переход к предыдущему шагу</span><span class="sxs-lookup"><span data-stu-id="2c94d-124">Going back to the previous step</span></span>

<span data-ttu-id="2c94d-125">Если вам нужно изменить выбранные функции, выберите **Go Back** (Назад), чтобы вернуться к шагу [Import](importing-features.md) (Импорт).</span><span class="sxs-lookup"><span data-stu-id="2c94d-125">If you need to make changes to your feature selections, use **Go Back** to return to the [import](importing-features.md) step.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c94d-126">См. также</span><span class="sxs-lookup"><span data-stu-id="2c94d-126">See also</span></span>

- [<span data-ttu-id="2c94d-127">Вас приветствует Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="2c94d-127">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="2c94d-128">Импорт выбранных пакетов</span><span class="sxs-lookup"><span data-stu-id="2c94d-128">Importing selected packages</span></span>](importing-features.md)
