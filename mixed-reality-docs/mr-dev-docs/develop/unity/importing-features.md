---
title: Импорт функций
description: Сведения о том, как импортировать и устанавливать функции из средства Mixed Reality Feature Tool для разработки для HoloLens и смешанной реальности.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: a82eea93a07b662314f3a718eef0c1bd18a4ca4e
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243984"
---
# <a name="importing-features"></a><span data-ttu-id="1ec34-104">Импорт функций</span><span class="sxs-lookup"><span data-stu-id="1ec34-104">Importing features</span></span>

<span data-ttu-id="1ec34-105">Когда скачивание функций завершится, вы сможете просмотреть их и импортировать в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="1ec34-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="1ec34-106">На этом шаге окно приложения должно выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="1ec34-106">At this step, your application window should look like the following image:</span></span>

![Импорт функций](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="1ec34-108">Список характеристик</span><span class="sxs-lookup"><span data-stu-id="1ec34-108">Features list</span></span>

<span data-ttu-id="1ec34-109">Список **Функции** включает коллекцию пакетов, выбранных на этапе обнаружения.</span><span class="sxs-lookup"><span data-stu-id="1ec34-109">The **Features** list contains the collection of packages selected during discovery.</span></span> 
* <span data-ttu-id="1ec34-110">Перед импортом вы можете выбрать любую из функций или отменить выбор.</span><span class="sxs-lookup"><span data-stu-id="1ec34-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="1ec34-111">Сведения о пакете можно просмотреть с помощью ссылки **Сведения**, которая показана ниже.</span><span class="sxs-lookup"><span data-stu-id="1ec34-111">Package details can be viewed using the **Details** link shown below</span></span>

![Список характеристик](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="1ec34-113">Список необходимых зависимостей</span><span class="sxs-lookup"><span data-stu-id="1ec34-113">Required dependencies list</span></span>

<span data-ttu-id="1ec34-114">Список **Необходимые зависимости** включает пакеты, которые требуются для работы одной или нескольких выбранных функций.</span><span class="sxs-lookup"><span data-stu-id="1ec34-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="1ec34-115">Также в этом списке приведены зависимости зависимостей.</span><span class="sxs-lookup"><span data-stu-id="1ec34-115">This list will also contain dependencies of dependencies.</span></span>
* <span data-ttu-id="1ec34-116">Перед импортом вы можете выбрать любую из зависимостей или отменить выбор.</span><span class="sxs-lookup"><span data-stu-id="1ec34-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="1ec34-117">Сведения о пакете можно просмотреть с помощью ссылки **Сведения**, которая показана ниже.</span><span class="sxs-lookup"><span data-stu-id="1ec34-117">Package details can be viewed using the **Details** link shown below</span></span>

![Список зависимостей](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="1ec34-119">Если вы отмените выбор необходимых зависимостей, при загрузке проекта в Unity вы увидите одну или несколько ошибок зависимостей.</span><span class="sxs-lookup"><span data-stu-id="1ec34-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="1ec34-120">Соответствующие функции в проекте будут неработоспособны.</span><span class="sxs-lookup"><span data-stu-id="1ec34-120">These features won't be usable in the project.</span></span>

## <a name="specifying-the-unity-project-path"></a><span data-ttu-id="1ec34-121">Указание пути к проекту Unity</span><span class="sxs-lookup"><span data-stu-id="1ec34-121">Specifying the Unity project path</span></span>

<span data-ttu-id="1ec34-122">Чтобы функции можно было импортировать в проект, нужно зарегистрировать путь к ним в средстве Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="1ec34-122">Before features can be imported into the project, you need to register the path with the Mixed Reality Feature Tool.</span></span>

![Задание пути к проекту](images/ProjectPath.png)

## <a name="validating-selections"></a><span data-ttu-id="1ec34-124">Проверка выбора</span><span class="sxs-lookup"><span data-stu-id="1ec34-124">Validating selections</span></span>

<span data-ttu-id="1ec34-125">Мы настоятельно рекомендуем проверить перед импортом выбранные функции.</span><span class="sxs-lookup"><span data-stu-id="1ec34-125">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="1ec34-126">На этом шаге будут выявлены все проблемы, которые могут помешать успешной разработке проекта.</span><span class="sxs-lookup"><span data-stu-id="1ec34-126">This step will raise any issues that are likely to impede successful project development.</span></span>

![Проблемы при проверке](images/ValidationIssues.png)

<span data-ttu-id="1ec34-128">Средство Mixed Reality Feature Tool предоставляет два метода автоматического устранения проблем, которые описаны в следующих разделах, а также возможность отменить процесс и устранить проблемы вручную.</span><span class="sxs-lookup"><span data-stu-id="1ec34-128">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ec34-129">Средство Mixed Reality Feature Tool не может автоматически устранять проблемы, связанные с отсутствием требуемых версий Unity.</span><span class="sxs-lookup"><span data-stu-id="1ec34-129">The Mixed Reality Feature Tool cannot automatically resolve issues related to required versions of Unity.</span></span> <span data-ttu-id="1ec34-130">Такие проблемы необходимо обработать вручную, обновив используемую проектом версию Unity или отключив функции, для которых требуется более новая версия.</span><span class="sxs-lookup"><span data-stu-id="1ec34-130">These issues must be handled manually by upgrading the version of Unity used by the project or disabling the feature(s) requiring a newer version.</span></span>
>
> <span data-ttu-id="1ec34-131">В будущих выпусках средство Mixed Reality Feature Tool предоставит улучшенную возможность фильтрации функций на основе версии Unity, используемой проектом.</span><span class="sxs-lookup"><span data-stu-id="1ec34-131">A future release of the Mixed Reality Feature Tool will provide better filtering of features based upon the version of Unity being used by the project.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="1ec34-132">Включение зависимостей</span><span class="sxs-lookup"><span data-stu-id="1ec34-132">Enable dependencies</span></span>

<span data-ttu-id="1ec34-133">Кнопка **Включить зависимости** автоматически выбирает недостающие зависимости, если они не выбраны.</span><span class="sxs-lookup"><span data-stu-id="1ec34-133">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="1ec34-134">Это действие применяется к тем зависимостям, которые были выбраны явным образом (то есть отображаются в списке **Функции**) или неявно добавлены как обязательные зависимости выбранных функций.</span><span class="sxs-lookup"><span data-stu-id="1ec34-134">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="1ec34-135">Отключение функций</span><span class="sxs-lookup"><span data-stu-id="1ec34-135">Disable features</span></span>

<span data-ttu-id="1ec34-136">Действие **Отключить функции** автоматически отменяет выбор всех функций, которые зависят от тех зависимостей, выбор которых был ранее отменен.</span><span class="sxs-lookup"><span data-stu-id="1ec34-136">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="1ec34-137">Оно применяется к неявно выбранным пакетам зависимостей и явно выбранным функциям.</span><span class="sxs-lookup"><span data-stu-id="1ec34-137">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="1ec34-138">Импорт</span><span class="sxs-lookup"><span data-stu-id="1ec34-138">Importing</span></span>

<span data-ttu-id="1ec34-139">Выберите **Импортировать**, чтобы добавить выбранные функции и предоставить [окончательное утверждение](reviewing-changes.md) перед обновлением целевого проекта.</span><span class="sxs-lookup"><span data-stu-id="1ec34-139">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ec34-140">Если при импорте сохраняется ошибка проверки, отобразится предупреждающее сообщение.</span><span class="sxs-lookup"><span data-stu-id="1ec34-140">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="1ec34-141">Мы рекомендуем выбрать в нем вариант "Нет", затем щелкнуть **Проверить** и устранить все перечисленные здесь проблемы.</span><span class="sxs-lookup"><span data-stu-id="1ec34-141">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![Продолжение проверки проблем](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="1ec34-143">Переход к предыдущему шагу</span><span class="sxs-lookup"><span data-stu-id="1ec34-143">Going back to the previous step</span></span>

<span data-ttu-id="1ec34-144">Из раздела **Импорт функций** в средстве Mixed Reality Feature Tool можно вернуться назад к [обнаружению функций](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="1ec34-144">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="1ec34-145">Щелкните **Назад**, чтобы скачать другие пакеты функций.</span><span class="sxs-lookup"><span data-stu-id="1ec34-145">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ec34-146">См. также</span><span class="sxs-lookup"><span data-stu-id="1ec34-146">See also</span></span>

- [<span data-ttu-id="1ec34-147">Вас приветствует Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="1ec34-147">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="1ec34-148">Обнаружение и получение</span><span class="sxs-lookup"><span data-stu-id="1ec34-148">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="1ec34-149">Просмотр сведений о пакете функций</span><span class="sxs-lookup"><span data-stu-id="1ec34-149">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="1ec34-150">Просмотр и утверждение изменений в проекте</span><span class="sxs-lookup"><span data-stu-id="1ec34-150">Reviewing and approving project modifications</span></span>](reviewing-changes.md)