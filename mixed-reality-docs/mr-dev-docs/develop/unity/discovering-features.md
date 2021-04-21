---
title: Обнаружение и получение функций
description: Обнаружение и скачивание функций смешанной реальности.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: 9f12a1eba0c28b89000f1541ba62747a03e3564b
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2021
ms.locfileid: "107732012"
---
# <a name="discovering-and-acquiring-features"></a><span data-ttu-id="a5c58-104">Обнаружение и получение функций</span><span class="sxs-lookup"><span data-stu-id="a5c58-104">Discovering and acquiring features</span></span>

<span data-ttu-id="a5c58-105">В разделах этой статьи показано, как найти пакеты функций в инструменте Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="a5c58-105">The sections in this article outline how to find feature packages in the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="a5c58-106">Ознакомьтесь с приведенным ниже снимком экрана, если вам нужна информация по конкретному разделу:</span><span class="sxs-lookup"><span data-stu-id="a5c58-106">Refer to the screenshot below if you need a reference for a given section:</span></span>

![Обнаружение функций](images/FeatureToolDiscovery.png)

## <a name="available-features"></a><span data-ttu-id="a5c58-108">Доступные функции</span><span class="sxs-lookup"><span data-stu-id="a5c58-108">Available features</span></span>

### <a name="category"></a><span data-ttu-id="a5c58-109">Категория</span><span class="sxs-lookup"><span data-stu-id="a5c58-109">Category</span></span>

<span data-ttu-id="a5c58-110">Средство Mixed Reality Feature Tool отображает коллекцию категорий функций, чтобы вам было удобнее найти нужное.</span><span class="sxs-lookup"><span data-stu-id="a5c58-110">The Mixed Reality Feature Tool displays a collection of feature categories to make it easy to find what you want.</span></span> <span data-ttu-id="a5c58-111">Разверните любую из категорий, чтобы отобразить коллекцию доступных функций.</span><span class="sxs-lookup"><span data-stu-id="a5c58-111">Expand any of the categories to display its collection of available features.</span></span>

> [!NOTE]
> <span data-ttu-id="a5c58-112">Если вы не можете найти нужные функции, проверьте раздел **Другие возможности**.</span><span class="sxs-lookup"><span data-stu-id="a5c58-112">If you can't find the functionality you're looking for, check **Other features**.</span></span>

![Категория компонента](images/FeatureCategory.png)

<span data-ttu-id="a5c58-114">Заголовок категории на приведенном выше снимке экрана содержит следующие свойства, слева направо:</span><span class="sxs-lookup"><span data-stu-id="a5c58-114">The category header in the above screenshot contains the following properties, from left to right:</span></span>

- <span data-ttu-id="a5c58-115">кнопка свертывания и развертывания;</span><span class="sxs-lookup"><span data-stu-id="a5c58-115">Expand and collapse button</span></span>
- <span data-ttu-id="a5c58-116">название категории (например, Mixed Reality Toolkit);</span><span class="sxs-lookup"><span data-stu-id="a5c58-116">Category name (ex: Mixed Reality Toolkit)</span></span>
- <span data-ttu-id="a5c58-117">число выбранных функций;</span><span class="sxs-lookup"><span data-stu-id="a5c58-117">Count of selected features</span></span>
- <span data-ttu-id="a5c58-118">число доступных функций.</span><span class="sxs-lookup"><span data-stu-id="a5c58-118">Count of available features</span></span>
- <span data-ttu-id="a5c58-119">Кнопки выбора</span><span class="sxs-lookup"><span data-stu-id="a5c58-119">Section buttons</span></span>

> [!NOTE]
> <span data-ttu-id="a5c58-120">Кнопки выбора чувствительны к контексту.</span><span class="sxs-lookup"><span data-stu-id="a5c58-120">The selection buttons are context sensitive.</span></span> <span data-ttu-id="a5c58-121">Состояние выбора компонентов в категории влияет на отображение одной или нескольких кнопок `Select All` и `Select None`.</span><span class="sxs-lookup"><span data-stu-id="a5c58-121">Based on the state of feature selection within the category, one or more of the `Select All` and `Select None` buttons will be displayed.</span></span>

### <a name="feature"></a><span data-ttu-id="a5c58-122">Компонент</span><span class="sxs-lookup"><span data-stu-id="a5c58-122">Feature</span></span>

![Запись функции](images/FeatureEntry.png)

<span data-ttu-id="a5c58-124">Функции перечислены в соответствующей категории.</span><span class="sxs-lookup"><span data-stu-id="a5c58-124">Features are listed in their appropriate category.</span></span> <span data-ttu-id="a5c58-125">На приведенном выше снимке экрана представлены следующие записи функций, слева направо:</span><span class="sxs-lookup"><span data-stu-id="a5c58-125">From left to right in the above screenshot, feature entries contain:</span></span>

- <span data-ttu-id="a5c58-126">флажок выбора;</span><span class="sxs-lookup"><span data-stu-id="a5c58-126">Selection check box</span></span>
- <span data-ttu-id="a5c58-127">название функции (например, Mixed Reality Toolkit Foundation);</span><span class="sxs-lookup"><span data-stu-id="a5c58-127">Feature name (ex: Mixed Reality Toolkit Foundation)</span></span>
- <span data-ttu-id="a5c58-128">список доступных версий;</span><span class="sxs-lookup"><span data-stu-id="a5c58-128">List of available versions</span></span>
- <span data-ttu-id="a5c58-129">ссылка на [сведения о пакете функций](viewing-package-details.md).</span><span class="sxs-lookup"><span data-stu-id="a5c58-129">Link to the [feature package details](viewing-package-details.md)</span></span>

> [!NOTE]
> <span data-ttu-id="a5c58-130">Если компонент предоставляется в рамках программы раннего доступа (также называется закрытой предварительной версией), отображается значок ![раннего доступа](images/EarlyAccess.png).</span><span class="sxs-lookup"><span data-stu-id="a5c58-130">If a feature is provided by an Early Access (also called private preview) program, an indicator icon ![early access](images/EarlyAccess.png) will be displayed.</span></span>

## <a name="refresh-the-feature-catalog"></a><span data-ttu-id="a5c58-131">Обновление каталога функций</span><span class="sxs-lookup"><span data-stu-id="a5c58-131">Refresh the feature catalog</span></span>

<span data-ttu-id="a5c58-132">Чтобы проверить наличие новых функций и обновлений, нажмите кнопку "Обновить".</span><span class="sxs-lookup"><span data-stu-id="a5c58-132">To check for new and updated features, click the refresh</span></span> ![кнопка "Обновить"](images/RefreshButton.png) <span data-ttu-id="a5c58-134">.</span><span class="sxs-lookup"><span data-stu-id="a5c58-134">button.</span></span> <span data-ttu-id="a5c58-135">Это действие устанавливает подключение к сайту каталога и получает последние сведения.</span><span class="sxs-lookup"><span data-stu-id="a5c58-135">This will connect to the catalog site and retrieve the latest information.</span></span> <span data-ttu-id="a5c58-136">После считывания каталога отобразятся дата и время последнего обновления.</span><span class="sxs-lookup"><span data-stu-id="a5c58-136">Once the catalog has been read, the date and time of the last update will be displayed.</span></span>

## <a name="select-features"></a><span data-ttu-id="a5c58-137">Выбор функций</span><span class="sxs-lookup"><span data-stu-id="a5c58-137">Select features</span></span>

<span data-ttu-id="a5c58-138">Чтобы выбрать функции, разверните нужную категорию, выберите версию и установите соответствующий флажок:</span><span class="sxs-lookup"><span data-stu-id="a5c58-138">Features are selected by expanding a category, selecting a version, and clicking the check box:</span></span>

![Выбранные компоненты](images/SelectedFeatures.png)

<span data-ttu-id="a5c58-140">Для выбора всех пакетов в категории доступна кнопка `Select All`.</span><span class="sxs-lookup"><span data-stu-id="a5c58-140">To select every package within a category, a `Select All` button is provided.</span></span> <span data-ttu-id="a5c58-141">`Select None` отменяет выбор всех пакетов.</span><span class="sxs-lookup"><span data-stu-id="a5c58-141">`Select None` will deselect all selected packages.</span></span> 

<span data-ttu-id="a5c58-142">Каждая категория, в которой выбраны одна или несколько функций, отобразят количество выбранных элементов.</span><span class="sxs-lookup"><span data-stu-id="a5c58-142">Each category with one or more selected features will update to display the count.</span></span>

## <a name="acquiring-features"></a><span data-ttu-id="a5c58-143">Получение функций</span><span class="sxs-lookup"><span data-stu-id="a5c58-143">Acquiring features</span></span>

<span data-ttu-id="a5c58-144">Выбрав нужные функции, щелкните **Получить функции**, чтобы начать скачивание файлов для выбранного пакета компонентов.</span><span class="sxs-lookup"><span data-stu-id="a5c58-144">Once you've chosen your features, select **Get features** to start downloading the selected feature package files.</span></span>

> [!NOTE]
> <span data-ttu-id="a5c58-145">По умолчанию файлы полученных ранее пакетов функций не скачиваются повторно.</span><span class="sxs-lookup"><span data-stu-id="a5c58-145">By default, previously acquired feature package files won't be re-downloaded.</span></span> <span data-ttu-id="a5c58-146">Чтобы изменить это поведение, воспользуйтесь [настройкой средства функций](configuring-feature-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a5c58-146">To change this behavior please see [configuring the feature tool](configuring-feature-tool.md).</span></span>

<span data-ttu-id="a5c58-147">Когда скачивание завершится, средство Mixed Reality Feature Tool перейдет к шагу [импорта функций](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="a5c58-147">Once downloading is complete, the Mixed Reality Feature Tool will move to the [importing features](importing-features.md) step.</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="a5c58-148">Переход к предыдущему шагу</span><span class="sxs-lookup"><span data-stu-id="a5c58-148">Going back to the previous step</span></span>

<span data-ttu-id="a5c58-149">Из раздела **Обнаружение функций** в средстве Mixed Reality Feature Tool можно вернуться к выбору проекта.</span><span class="sxs-lookup"><span data-stu-id="a5c58-149">From **Discover features**, the Mixed Reality Feature Tool allows for navigating back to project selection.</span></span> <span data-ttu-id="a5c58-150">Щелкните **Назад**, чтобы повторить этот процесс с начала.</span><span class="sxs-lookup"><span data-stu-id="a5c58-150">Select **Go back** to start again.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5c58-151">См. также</span><span class="sxs-lookup"><span data-stu-id="a5c58-151">See also</span></span>

- [<span data-ttu-id="a5c58-152">Вас приветствует Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="a5c58-152">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="a5c58-153">Настройка средства функций</span><span class="sxs-lookup"><span data-stu-id="a5c58-153">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="a5c58-154">Просмотр сведений о пакете функций</span><span class="sxs-lookup"><span data-stu-id="a5c58-154">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="a5c58-155">Импорт выбранных пакетов</span><span class="sxs-lookup"><span data-stu-id="a5c58-155">Importing selected packages</span></span>](importing-features.md)
