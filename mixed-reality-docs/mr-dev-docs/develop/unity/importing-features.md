---
title: Импорт функций
description: Сведения о том, как импортировать и устанавливать функции из средства Mixed Reality Feature Tool для разработки для HoloLens и смешанной реальности.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230831"
---
# <a name="importing-features"></a><span data-ttu-id="6e623-104">Импорт функций</span><span class="sxs-lookup"><span data-stu-id="6e623-104">Importing features</span></span>

<span data-ttu-id="6e623-105">Когда скачивание функций завершится, вы сможете просмотреть их и импортировать в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="6e623-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="6e623-106">На этом шаге окно приложения должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="6e623-106">At this step, your application window should look like the following image:</span></span>

![Импорт функций](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="6e623-108">Список характеристик</span><span class="sxs-lookup"><span data-stu-id="6e623-108">Features list</span></span>

<span data-ttu-id="6e623-109">Список **Функции** включает коллекцию пакетов, выбранных на этапе обнаружения.</span><span class="sxs-lookup"><span data-stu-id="6e623-109">The **Features** list contains the collection of packages selected during discovery.</span></span> <span data-ttu-id="6e623-110">Перед импортом вы можете выбрать любую из функций или отменить выбор.</span><span class="sxs-lookup"><span data-stu-id="6e623-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="6e623-111">Сведения о пакете можно просмотреть с помощью ссылки **Сведения**, которая показана ниже.</span><span class="sxs-lookup"><span data-stu-id="6e623-111">Package details can be viewed using the **Details** link shown below</span></span>

![Список характеристик](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="6e623-113">Список необходимых зависимостей</span><span class="sxs-lookup"><span data-stu-id="6e623-113">Required dependencies list</span></span>

<span data-ttu-id="6e623-114">Список **Необходимые зависимости** включает пакеты, которые требуются для работы одной или нескольких выбранных функций.</span><span class="sxs-lookup"><span data-stu-id="6e623-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="6e623-115">Также в этом списке приведены зависимости зависимостей.</span><span class="sxs-lookup"><span data-stu-id="6e623-115">This list will also contain dependencies of dependencies.</span></span> <span data-ttu-id="6e623-116">Перед импортом вы можете выбрать любую из зависимостей или отменить выбор.</span><span class="sxs-lookup"><span data-stu-id="6e623-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="6e623-117">Сведения о пакете можно просмотреть с помощью ссылки **Сведения**, которая показана ниже.</span><span class="sxs-lookup"><span data-stu-id="6e623-117">Package details can be viewed using the **Details** link shown below</span></span>

![Список зависимостей](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="6e623-119">Если вы отмените выбор необходимых зависимостей, при загрузке проекта в Unity вы увидите одну или несколько ошибок зависимостей.</span><span class="sxs-lookup"><span data-stu-id="6e623-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="6e623-120">Соответствующие функции в проекте будут неработоспособны.</span><span class="sxs-lookup"><span data-stu-id="6e623-120">These features won't be usable in the project.</span></span>

## <a name="validating-selections"></a><span data-ttu-id="6e623-121">Проверка выбора</span><span class="sxs-lookup"><span data-stu-id="6e623-121">Validating selections</span></span>

<span data-ttu-id="6e623-122">Мы настоятельно рекомендуем проверить перед импортом выбранные функции.</span><span class="sxs-lookup"><span data-stu-id="6e623-122">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="6e623-123">На этом шаге будут выявлены все проблемы, которые могут помешать успешной разработке проекта.</span><span class="sxs-lookup"><span data-stu-id="6e623-123">This step will raise any issues that are likely to impede successful project development.</span></span>

![Проблемы при проверке](images/ValidationIssues.png)

<span data-ttu-id="6e623-125">Средство Mixed Reality Feature Tool предоставляет два метода автоматического устранения проблем, которые описаны в следующих разделах, а также возможность отменить процесс и устранить проблемы вручную.</span><span class="sxs-lookup"><span data-stu-id="6e623-125">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="6e623-126">Включение зависимостей</span><span class="sxs-lookup"><span data-stu-id="6e623-126">Enable dependencies</span></span>

<span data-ttu-id="6e623-127">Кнопка **Включить зависимости** автоматически выбирает недостающие зависимости, если они не выбраны.</span><span class="sxs-lookup"><span data-stu-id="6e623-127">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="6e623-128">Это действие применяется к тем зависимостям, которые были выбраны явным образом (то есть отображаются в списке **Функции**) или неявно добавлены как обязательные зависимости выбранных функций.</span><span class="sxs-lookup"><span data-stu-id="6e623-128">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="6e623-129">Отключение функций</span><span class="sxs-lookup"><span data-stu-id="6e623-129">Disable features</span></span>

<span data-ttu-id="6e623-130">Действие **Отключить функции** автоматически отменяет выбор всех функций, которые зависят от тех зависимостей, выбор которых был ранее отменен.</span><span class="sxs-lookup"><span data-stu-id="6e623-130">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="6e623-131">Оно применяется к неявно выбранным пакетам зависимостей и явно выбранным функциям.</span><span class="sxs-lookup"><span data-stu-id="6e623-131">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="6e623-132">Импорт</span><span class="sxs-lookup"><span data-stu-id="6e623-132">Importing</span></span>

<span data-ttu-id="6e623-133">Выберите **Импортировать**, чтобы добавить выбранные функции и предоставить [окончательное утверждение](reviewing-changes.md) перед обновлением целевого проекта.</span><span class="sxs-lookup"><span data-stu-id="6e623-133">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6e623-134">Если при импорте сохраняется ошибка проверки, отобразится предупреждающее сообщение.</span><span class="sxs-lookup"><span data-stu-id="6e623-134">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="6e623-135">Мы рекомендуем выбрать в нем вариант "Нет", затем щелкнуть **Проверить** и устранить все перечисленные здесь проблемы.</span><span class="sxs-lookup"><span data-stu-id="6e623-135">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![Продолжение проверки проблем](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="6e623-137">Переход к предыдущему шагу</span><span class="sxs-lookup"><span data-stu-id="6e623-137">Going back to the previous step</span></span>

<span data-ttu-id="6e623-138">Из раздела **Импорт функций** в средстве Mixed Reality Feature Tool можно вернуться назад к [обнаружению функций](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="6e623-138">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="6e623-139">Щелкните **Назад**, чтобы скачать другие пакеты функций.</span><span class="sxs-lookup"><span data-stu-id="6e623-139">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e623-140">См. также</span><span class="sxs-lookup"><span data-stu-id="6e623-140">See also</span></span>

- [<span data-ttu-id="6e623-141">Вас приветствует Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="6e623-141">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="6e623-142">Обнаружение и получение</span><span class="sxs-lookup"><span data-stu-id="6e623-142">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="6e623-143">Просмотр сведений о пакете функций</span><span class="sxs-lookup"><span data-stu-id="6e623-143">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="6e623-144">Просмотр и утверждение изменений в проекте</span><span class="sxs-lookup"><span data-stu-id="6e623-144">Reviewing and approving project modifications</span></span>](reviewing-changes.md)