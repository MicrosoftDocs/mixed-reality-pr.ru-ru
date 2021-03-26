---
title: Обнаружение и получение функций
description: Обнаружение и скачивание функций смешанной реальности.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: 859abd0c8e538392a7ba2a1adbb4387956c50028
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230723"
---
# <a name="discovering-and-acquiring-features"></a><span data-ttu-id="a65f2-104">Обнаружение и получение функций</span><span class="sxs-lookup"><span data-stu-id="a65f2-104">Discovering and acquiring features</span></span>

<span data-ttu-id="a65f2-105">В разделах этой статьи показано, как найти пакеты функций в инструменте Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="a65f2-105">The sections in this article outline how to find feature packages in the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="a65f2-106">Ознакомьтесь с приведенным ниже снимком экрана, если вам нужна информация по конкретному разделу:</span><span class="sxs-lookup"><span data-stu-id="a65f2-106">Refer to the screenshot below if you need a reference for a given section:</span></span>

![Обнаружение функций](images/FeatureToolDiscovery.png)

## <a name="available-features"></a><span data-ttu-id="a65f2-108">Доступные функции</span><span class="sxs-lookup"><span data-stu-id="a65f2-108">Available features</span></span>

### <a name="category"></a><span data-ttu-id="a65f2-109">Категория</span><span class="sxs-lookup"><span data-stu-id="a65f2-109">Category</span></span>

<span data-ttu-id="a65f2-110">Средство Mixed Reality Feature Tool отображает коллекцию категорий функций, чтобы вам было удобнее найти нужное.</span><span class="sxs-lookup"><span data-stu-id="a65f2-110">The Mixed Reality Feature Tool displays a collection of feature categories to make it easy to find what you want.</span></span> <span data-ttu-id="a65f2-111">Разверните любую из категорий, чтобы отобразить коллекцию доступных функций.</span><span class="sxs-lookup"><span data-stu-id="a65f2-111">Expand any of the categories to display its collection of available features.</span></span>

> [!NOTE]
> <span data-ttu-id="a65f2-112">Если вы не можете найти нужные функции, проверьте раздел **Другие возможности**.</span><span class="sxs-lookup"><span data-stu-id="a65f2-112">If you can't find the functionality you're looking for, check **Other features**.</span></span>

![Категория компонента](images/FeatureCategory.png)

<span data-ttu-id="a65f2-114">Заголовок категории на приведенном выше снимке экрана содержит следующие свойства, слева направо:</span><span class="sxs-lookup"><span data-stu-id="a65f2-114">The category header in the above screenshot contains the following properties, from left to right:</span></span>

- <span data-ttu-id="a65f2-115">кнопка свертывания и развертывания;</span><span class="sxs-lookup"><span data-stu-id="a65f2-115">Expand and collapse button</span></span>
- <span data-ttu-id="a65f2-116">название категории (например, Mixed Reality Toolkit);</span><span class="sxs-lookup"><span data-stu-id="a65f2-116">Category name (ex: Mixed Reality Toolkit)</span></span>
- <span data-ttu-id="a65f2-117">число выбранных функций;</span><span class="sxs-lookup"><span data-stu-id="a65f2-117">Count of selected features</span></span>
- <span data-ttu-id="a65f2-118">число доступных функций.</span><span class="sxs-lookup"><span data-stu-id="a65f2-118">Count of available features</span></span>

### <a name="feature"></a><span data-ttu-id="a65f2-119">Компонент</span><span class="sxs-lookup"><span data-stu-id="a65f2-119">Feature</span></span>

![Запись функции](images/FeatureEntry.png)

<span data-ttu-id="a65f2-121">Функции перечислены в соответствующей категории.</span><span class="sxs-lookup"><span data-stu-id="a65f2-121">Features are listed in their appropriate category.</span></span> <span data-ttu-id="a65f2-122">На приведенном выше снимке экрана представлены следующие записи функций, слева направо:</span><span class="sxs-lookup"><span data-stu-id="a65f2-122">From left to right in the above screenshot, feature entries contain:</span></span>

- <span data-ttu-id="a65f2-123">флажок выбора;</span><span class="sxs-lookup"><span data-stu-id="a65f2-123">Selection check box</span></span>
- <span data-ttu-id="a65f2-124">название функции (например, Mixed Reality Toolkit Foundation);</span><span class="sxs-lookup"><span data-stu-id="a65f2-124">Feature name (ex: Mixed Reality Toolkit Foundation)</span></span>
- <span data-ttu-id="a65f2-125">список доступных версий;</span><span class="sxs-lookup"><span data-stu-id="a65f2-125">List of available versions</span></span>
- <span data-ttu-id="a65f2-126">ссылка на [сведения о пакете функций](viewing-package-details.md).</span><span class="sxs-lookup"><span data-stu-id="a65f2-126">Link to the [feature package details](viewing-package-details.md)</span></span>

## <a name="refresh-the-feature-catalog"></a><span data-ttu-id="a65f2-127">Обновление каталога функций</span><span class="sxs-lookup"><span data-stu-id="a65f2-127">Refresh the feature catalog</span></span>

<span data-ttu-id="a65f2-128">Чтобы проверить наличие новых функций и обновлений, нажмите кнопку "Обновить".</span><span class="sxs-lookup"><span data-stu-id="a65f2-128">To check for new and updated features, click the refresh</span></span> ![кнопка "Обновить"](images/RefreshButton.png) <span data-ttu-id="a65f2-130">.</span><span class="sxs-lookup"><span data-stu-id="a65f2-130">button.</span></span> <span data-ttu-id="a65f2-131">Это действие устанавливает подключение к сайту каталога и получает последние сведения.</span><span class="sxs-lookup"><span data-stu-id="a65f2-131">This will connect to the catalog site and retrieve the latest information.</span></span> <span data-ttu-id="a65f2-132">После считывания каталога отобразятся дата и время последнего обновления.</span><span class="sxs-lookup"><span data-stu-id="a65f2-132">Once the catalog has been read, the date and time of the last update will be displayed.</span></span>

## <a name="select-features"></a><span data-ttu-id="a65f2-133">Выбор функций</span><span class="sxs-lookup"><span data-stu-id="a65f2-133">Select features</span></span>

<span data-ttu-id="a65f2-134">Чтобы выбрать функции, разверните нужную категорию, выберите версию и установите соответствующий флажок:</span><span class="sxs-lookup"><span data-stu-id="a65f2-134">Features are selected by expanding a category, selecting a version, and clicking the check box:</span></span>

![Выбранные компоненты](images/SelectedFeatures.png)

<span data-ttu-id="a65f2-136">Каждая категория, в которой выбраны одна или несколько функций, отобразят количество выбранных элементов.</span><span class="sxs-lookup"><span data-stu-id="a65f2-136">Each category with one or more selected features will update to display the count.</span></span>

## <a name="acquiring-features"></a><span data-ttu-id="a65f2-137">Получение функций</span><span class="sxs-lookup"><span data-stu-id="a65f2-137">Acquiring features</span></span>

<span data-ttu-id="a65f2-138">Выбрав нужные функции, щелкните **Получить функции**, чтобы начать скачивание файлов для выбранного пакета компонентов.</span><span class="sxs-lookup"><span data-stu-id="a65f2-138">Once you've chosen your features, select **Get features** to start downloading the selected feature package files.</span></span>

> [!NOTE]
> <span data-ttu-id="a65f2-139">По умолчанию файлы полученных ранее пакетов функций не скачиваются повторно.</span><span class="sxs-lookup"><span data-stu-id="a65f2-139">By default, previously acquired feature package files won't be re-downloaded.</span></span> <span data-ttu-id="a65f2-140">Чтобы изменить это поведение, воспользуйтесь [настройкой средства функций](configuring-feature-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a65f2-140">To change this behavior please see [configuring the feature tool](configuring-feature-tool.md).</span></span>

<span data-ttu-id="a65f2-141">Когда скачивание завершится, средство Mixed Reality Feature Tool перейдет к шагу [импорта функций](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="a65f2-141">Once downloading is complete, the Mixed Reality Feature Tool will move to the [importing features](importing-features.md) step.</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="a65f2-142">Переход к предыдущему шагу</span><span class="sxs-lookup"><span data-stu-id="a65f2-142">Going back to the previous step</span></span>

<span data-ttu-id="a65f2-143">Из раздела **Обнаружение функций** в средстве Mixed Reality Feature Tool можно вернуться к выбору проекта.</span><span class="sxs-lookup"><span data-stu-id="a65f2-143">From **Discover features**, the Mixed Reality Feature Tool allows for navigating back to project selection.</span></span> <span data-ttu-id="a65f2-144">Щелкните **Назад**, чтобы повторить этот процесс с начала.</span><span class="sxs-lookup"><span data-stu-id="a65f2-144">Select **Go back** to start again.</span></span>

## <a name="see-also"></a><span data-ttu-id="a65f2-145">См. также</span><span class="sxs-lookup"><span data-stu-id="a65f2-145">See also</span></span>

- [<span data-ttu-id="a65f2-146">Вас приветствует Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="a65f2-146">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="a65f2-147">Настройка средства функций</span><span class="sxs-lookup"><span data-stu-id="a65f2-147">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="a65f2-148">Просмотр сведений о пакете функций</span><span class="sxs-lookup"><span data-stu-id="a65f2-148">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="a65f2-149">Импорт выбранных пакетов</span><span class="sxs-lookup"><span data-stu-id="a65f2-149">Importing selected packages</span></span>](importing-features.md)
