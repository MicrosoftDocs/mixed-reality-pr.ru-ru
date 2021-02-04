---
title: Авторизация изменений в проекте
description: Узнайте, как авторизовать изменения в проекте с помощью Mixed Reality Feature Tool при разработке решений для HoloLens и виртуальной реальности.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: b9e4f53c9a1e5503cfa92a612879be1971422acc
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243973"
---
# <a name="authorizing-project-changes"></a><span data-ttu-id="43743-104">Авторизация изменений в проекте</span><span class="sxs-lookup"><span data-stu-id="43743-104">Authorizing project changes</span></span>

<span data-ttu-id="43743-105">Перед внесением изменений в проект Unity необходимо проверить и утвердить все изменения в файлах манифеста и проекта.</span><span class="sxs-lookup"><span data-stu-id="43743-105">Before modifying the Unity project, changes to the manifest and project files need to be reviewed and approved:</span></span>

![Запрос на авторизацию](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a><span data-ttu-id="43743-107">манифеста</span><span class="sxs-lookup"><span data-stu-id="43743-107">Manifest</span></span>

<span data-ttu-id="43743-108">Предложенные изменения манифеста можно просмотреть в столбце **Manifest** (Манифест) слева.</span><span class="sxs-lookup"><span data-stu-id="43743-108">The proposed manifest changes can be viewed in the **Manifest** column on the left.</span></span> <span data-ttu-id="43743-109">Его содержимое будет в точности записано в манифест проекта (**Packages/manifest.json**):</span><span class="sxs-lookup"><span data-stu-id="43743-109">The contents are exactly what will be written to the project manifest (**Packages/manifest.json**):</span></span>

![Предварительный просмотр манифеста](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a><span data-ttu-id="43743-111">Файлы, которые будут скопированы в проект</span><span class="sxs-lookup"><span data-stu-id="43743-111">Files to be copied into the project</span></span>

<span data-ttu-id="43743-112">В разделе **Files to be copied into the project** (Файлы, которые будут скопированы в проект) справа представлен список конкретных файлов пакетов функций, которые будут скопированы в проект Unity:</span><span class="sxs-lookup"><span data-stu-id="43743-112">The **Files to be copied into the project** section on the right lists the specific feature package files that will be copied into the Unity project:</span></span>

![Предварительный просмотр манифеста и файлов, которые будут скопированы](images/FilesToCopy.png)

## <a name="compare-manifests"></a><span data-ttu-id="43743-114">Сравнение манифестов</span><span class="sxs-lookup"><span data-stu-id="43743-114">Compare manifests</span></span>

<span data-ttu-id="43743-115">Вы можете сравнить версии всех предлагаемых изменений, выбрав **Compare** (Сравнить).</span><span class="sxs-lookup"><span data-stu-id="43743-115">You can see a detailed side-by-side comparison of all proposed changes by selecting **Compare**:</span></span>

![Сравнение манифестов](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a><span data-ttu-id="43743-117">Утверждение изменений</span><span class="sxs-lookup"><span data-stu-id="43743-117">Approving changes</span></span>

<span data-ttu-id="43743-118">Когда вы утвердите предложенные изменения, включенные в список файлы будут скопированы в проект Unity, а в манифест будут добавлены ссылки на эти файлы.</span><span class="sxs-lookup"><span data-stu-id="43743-118">When the proposed changes are approved, the listed files will be copied into the Unity project and the manifest will be updated with references to these files.</span></span>

> [!NOTE]
> <span data-ttu-id="43743-119">Файлы пакетов функций (\*.tgz) нужно добавить в систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="43743-119">The feature package (\*.tgz) files should be added to source control.</span></span> <span data-ttu-id="43743-120">Ссылки на них указываются в формате относительного пути, что позволяет группам разработчиков легко предоставлять общий доступ к изменениям функций и манифестов.</span><span class="sxs-lookup"><span data-stu-id="43743-120">They are referenced using a relative path to enable development teams to easily share features and manifest changes.</span></span>

 <span data-ttu-id="43743-121">В процессе изменений будет создана резервная копия текущего файла **manifest.json**.</span><span class="sxs-lookup"><span data-stu-id="43743-121">As part of the modifications, the current **manifest.json** file will be backed up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43743-122">В списке резервных копий манифеста самая старая всегда имеет имя **manifest.json.backup**.</span><span class="sxs-lookup"><span data-stu-id="43743-122">When viewing the manifest backups, the oldest will be called **manifest.json.backup**.</span></span> <span data-ttu-id="43743-123">Более новые резервные копии дополняются числовыми значениями, начиная с нуля (0).</span><span class="sxs-lookup"><span data-stu-id="43743-123">Newer backups will be annotated with a numeric value, beginning with zero (0).</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="43743-124">Переход к предыдущему шагу</span><span class="sxs-lookup"><span data-stu-id="43743-124">Going back to the previous step</span></span>

<span data-ttu-id="43743-125">Если вам нужно изменить выбранные функции, выберите **Go Back** (Назад), чтобы вернуться к шагу [Import](importing-features.md) (Импорт).</span><span class="sxs-lookup"><span data-stu-id="43743-125">If you need to make changes to your feature selections, use **Go Back** to return to the [import](importing-features.md) step.</span></span>

## <a name="see-also"></a><span data-ttu-id="43743-126">См. также</span><span class="sxs-lookup"><span data-stu-id="43743-126">See also</span></span>

- [<span data-ttu-id="43743-127">Вас приветствует Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="43743-127">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="43743-128">Импорт выбранных пакетов</span><span class="sxs-lookup"><span data-stu-id="43743-128">Importing selected packages</span></span>](importing-features.md)
