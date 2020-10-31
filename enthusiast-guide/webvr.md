---
title: Использование Вебвр с Windows Mixed Reality
description: Описание Вебвр и способов его использования с Microsoft ребром на гарнитурах Windows Mixed Reality.
ms.topic: article
keywords: Windows Mixed Reality, Смешанная реальность, виртуальная реальность, VR, MR, Вебвр, ребро, Microsoft ребро, просмотр веб-страниц
ms.openlocfilehash: 8e8d7b5feefe5b1eccad0684808b40b63e9bbbca
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131858"
---
# <a name="using-webvr-with-windows-mixed-reality"></a><span data-ttu-id="830a9-104">Использование Вебвр с Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="830a9-104">Using WebVR with Windows Mixed Reality</span></span>

>[!IMPORTANT]
><span data-ttu-id="830a9-105">Большинство современных веб-браузеров имеют устаревшую поддержку Вебвр в пользу Вебкср, новый стандарт для создания впечатляющих веб-интерфейсов для головных телефонов VR.</span><span class="sxs-lookup"><span data-stu-id="830a9-105">Most modern web browsers have deprecated support of WebVR in favor of WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="830a9-106">Установите [Новый Microsoft ребр](using-microsoft-edge.md) для поддержки вебкср.</span><span class="sxs-lookup"><span data-stu-id="830a9-106">Please install [the new Microsoft Edge](using-microsoft-edge.md) for WebXR support.</span></span>

## <a name="what-is-webvr"></a><span data-ttu-id="830a9-107">Что такое WebVR</span><span class="sxs-lookup"><span data-stu-id="830a9-107">What is WebVR</span></span>

<span data-ttu-id="830a9-108">[Вебвр](https://webvr.info) — это открытая спецификация, которая делает возможным запуск в БРАУЗЕРЕ среды VR.</span><span class="sxs-lookup"><span data-stu-id="830a9-108">[WebVR](https://webvr.info) is an open specification that makes it possible to experience VR in your browser.</span></span> <span data-ttu-id="830a9-109">Если веб-сайт реализует поддержку Вебвр и предоставляет трехмерное содержимое, он может отображать иммерсивное содержимое на гарнитуре с согласия пользователя.</span><span class="sxs-lookup"><span data-stu-id="830a9-109">If a website implements WebVR support and provides 3D content, it can display immersive content in the headset, with user consent.</span></span>

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a><span data-ttu-id="830a9-110">В чем разница между Вебвр и просмотром веб-страниц в режиме VR</span><span class="sxs-lookup"><span data-stu-id="830a9-110">What is the difference between WebVR and browsing the web in VR</span></span>

<span data-ttu-id="830a9-111">Вебвр — это технология, позволяющая автору веб-сайта добавлять функции VR на страницу.</span><span class="sxs-lookup"><span data-stu-id="830a9-111">WebVR is a technology that allows a website author to add VR functionality to a page.</span></span> <span data-ttu-id="830a9-112">API Вебвр используется страницей для отображения трехмерного содержимого (например, видео в 360 градусов, 3D-модели или трехмерной игры) до полной гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="830a9-112">The WebVR API is used by a page to display 3D content (such as 360 degree video, or a 3D model, or a 3D game) to the entirety of your headset.</span></span> <span data-ttu-id="830a9-113">**Пример:** Просмотр видео 360 в [CNN.com/VR](http://cnn.com/vr).</span><span class="sxs-lookup"><span data-stu-id="830a9-113">**Example:** Viewing a 360 Video on [cnn.com/vr](http://cnn.com/vr).</span></span> <span data-ttu-id="830a9-114">Если страница поддерживает Вебвр, она добавляет кнопку или другой элемент пользовательского интерфейса, который можно щелкнуть для входа в VR.</span><span class="sxs-lookup"><span data-stu-id="830a9-114">If a page supports WebVR, it will add a button or other UI element that you can click to enter VR.</span></span>

<span data-ttu-id="830a9-115">Просмотр веб-страниц в VR означает использование браузера Microsoft ребра, когда вы людьми гарнитуру, как 2D-приложение в Клиффхаусе.</span><span class="sxs-lookup"><span data-stu-id="830a9-115">Browsing the web in VR means using the Edge browser while you are wearing your headset, as a 2D app slate within the Cliffhouse.</span></span>

## <a name="do-all-websites-support-webvr"></a><span data-ttu-id="830a9-116">Все веб-сайты поддерживают Вебвр</span><span class="sxs-lookup"><span data-stu-id="830a9-116">Do all websites support WebVR</span></span>

<span data-ttu-id="830a9-117">Нет.</span><span class="sxs-lookup"><span data-stu-id="830a9-117">No.</span></span> <span data-ttu-id="830a9-118">Авторы веб-сайтов должны использовать Вебвр. Кроме того, они могут создавать сайты, оптимизированные для конкретных браузеров, головных телефонов и контроллеров.</span><span class="sxs-lookup"><span data-stu-id="830a9-118">Website authors must opt-in to use WebVR and furthermore they may create sites that are optimized for specific browsers, headsets, and controllers.</span></span> <span data-ttu-id="830a9-119">Например, некоторое содержимое Вебвр оптимизировано только для устройств с мобильными устройствами VR.</span><span class="sxs-lookup"><span data-stu-id="830a9-119">For example, some WebVR content is optimized for mobile VR devices only.</span></span> <span data-ttu-id="830a9-120">Кроме того, помните, что веб-сайты должны явно создавать и предоставлять содержимое Вебвр.</span><span class="sxs-lookup"><span data-stu-id="830a9-120">Also, keep in mind that web sites need to explicitly create and provide WebVR content.</span></span> <span data-ttu-id="830a9-121">Количество сайтов с содержимым, совместимым с Вебвр, постоянно увеличивается каждый день.</span><span class="sxs-lookup"><span data-stu-id="830a9-121">The number of sites that have some WebVR compatible content is growing every day.</span></span>

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a><span data-ttu-id="830a9-122">Можно ли использовать Naopak/Окулус и т. д. для просмотра содержимого Вебвр в Microsoft ребро</span><span class="sxs-lookup"><span data-stu-id="830a9-122">Can I use my Vive/Oculus etc to view WebVR content in Microsoft Edge</span></span>

<span data-ttu-id="830a9-123">Нет.</span><span class="sxs-lookup"><span data-stu-id="830a9-123">No.</span></span> <span data-ttu-id="830a9-124">Для использования Вебвр в пограничных условиях необходимо использовать гарнитуру Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="830a9-124">You must use a Windows Mixed Reality headset to use WebVR in Edge.</span></span> <span data-ttu-id="830a9-125">Однако вы можете получить доступ к содержимому Вебвр в другом браузере. см. полный список совместимых устройств и браузеров по адресу: [вебвр. Rocks](http://webvr.rocks/).</span><span class="sxs-lookup"><span data-stu-id="830a9-125">However, you may be able to access WebVR content in another browser; see the complete list of compatible devices and browsers at: [WebVR.rocks](http://webvr.rocks/).</span></span>

## <a name="where-can-i-find-the-webvr-developer-documentation"></a><span data-ttu-id="830a9-126">Где найти документацию для разработчиков Вебвр</span><span class="sxs-lookup"><span data-stu-id="830a9-126">Where can I find the WebVR developer documentation</span></span>

<span data-ttu-id="830a9-127">Документация для разработчиков находится здесь: [Документация для разработчиков вебвр](https://docs.microsoft.com/microsoft-edge/webvr/).</span><span class="sxs-lookup"><span data-stu-id="830a9-127">The developer documentation is located here: [WebVR Developer Documentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span></span>

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a><span data-ttu-id="830a9-128">Я нашел веб-сайт с Вебвр, который не работает в Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="830a9-128">I've found a website with WebVR that doesn't work in Windows Mixed Reality.</span></span> <span data-ttu-id="830a9-129">Чем я занимаюсь</span><span class="sxs-lookup"><span data-stu-id="830a9-129">What do I do</span></span>

<span data-ttu-id="830a9-130">Вы можете сообщить о неработающих веб-узлах непосредственно команде браузера Microsoft ребра в средстве [записи проблем](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)или с помощью Twitter, используя [#EdgeBug хэш-тег](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span><span class="sxs-lookup"><span data-stu-id="830a9-130">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

<span data-ttu-id="830a9-131">Кроме того, можно регистрировать ошибки с помощью приложения центра обратной связи Windows в категории:</span><span class="sxs-lookup"><span data-stu-id="830a9-131">You can also log bugs using the Windows Feedback Hub app under category:</span></span>

<span data-ttu-id="830a9-132">Microsoft ребро — проблемы с веб-сайтом ></span><span class="sxs-lookup"><span data-stu-id="830a9-132">Microsoft Edge -> Website Issues</span></span>

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a><span data-ttu-id="830a9-133">Что такое хорошая страница для проверки, если работает Вебвр</span><span class="sxs-lookup"><span data-stu-id="830a9-133">What is a good page to test if WebVR is working</span></span>

<span data-ttu-id="830a9-134">См. [примеры webvr.info](http://webvr.info/samples/XX-vr-controllers.html).</span><span class="sxs-lookup"><span data-stu-id="830a9-134">See [webvr.info samples](http://webvr.info/samples/XX-vr-controllers.html).</span></span>

## <a name="how-do-i-set-up-webvr"></a><span data-ttu-id="830a9-135">Разделы справки Настройка Вебвр</span><span class="sxs-lookup"><span data-stu-id="830a9-135">How do I set up WebVR</span></span>

<span data-ttu-id="830a9-136">Для работы с Вебвр содержимым на гарнитуре Windows Mixed Reality (с помощью оборудования или симуляции) необходимо:</span><span class="sxs-lookup"><span data-stu-id="830a9-136">To experience WebVR content on a Windows Mixed Reality headset (using hardware or simulation) you must:</span></span>

1. <span data-ttu-id="830a9-137">Убедитесь, что гарнитура подключена.</span><span class="sxs-lookup"><span data-stu-id="830a9-137">Ensure your headset is connected.</span></span>
2. <span data-ttu-id="830a9-138">Запустите Microsoft ребро на рабочем столе или в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="830a9-138">Launch Microsoft Edge, either on the desktop or within Mixed Reality.</span></span>
3. <span data-ttu-id="830a9-139">Перейдите на страницу с включенной Вебвр.</span><span class="sxs-lookup"><span data-stu-id="830a9-139">Navigate to a WebVR enabled page.</span></span>
4. <span data-ttu-id="830a9-140">Нажмите кнопку Ввод VR на странице (расположение и визуальное представление этой кнопки может различаться для каждого веб-сайта).</span><span class="sxs-lookup"><span data-stu-id="830a9-140">Click the Enter VR button within the page (the location and visual representation of this button may vary per website).</span></span> <span data-ttu-id="830a9-141">Он может выглядеть примерно так: </span><span class="sxs-lookup"><span data-stu-id="830a9-141">It may look similar to:</span></span>\
   ![Образ VR Гогглес](images/75px-enter-vr.png)
5. <span data-ttu-id="830a9-143">При первом входе в систему в определенном домене браузер запросит согласие на использование иммерсивного представления, а затем нажмите кнопку Да:</span><span class="sxs-lookup"><span data-stu-id="830a9-143">The first time you try to enter VR on a specific domain, the browser will ask for consent to use immersive view, click yes:</span></span> ![Пользовательский интерфейс согласия, отображаемый при первой попытке входа в VR в определенном домене](images/1053px-Webvr-consent-ui.png)
6. <span data-ttu-id="830a9-145">Гарнитура должна начинать отображать содержимое Вебвр.</span><span class="sxs-lookup"><span data-stu-id="830a9-145">Your headset should begin displaying the WebVR content.</span></span>

## <a name="see-also"></a><span data-ttu-id="830a9-146">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="830a9-146">See also</span></span>

* [<span data-ttu-id="830a9-147">Устранение неполадок > Вебвр</span><span class="sxs-lookup"><span data-stu-id="830a9-147">Troubleshooting > WebVR</span></span>](webvr-questions.md)
* [<span data-ttu-id="830a9-148">Как перейти к первому Вебврному интерфейсу</span><span class="sxs-lookup"><span data-stu-id="830a9-148">How to get into your first WebVR experience</span></span>](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [<span data-ttu-id="830a9-149">Использование игр и приложений в Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="830a9-149">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="830a9-150">Домашняя страница смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="830a9-150">Your Mixed Reality Home</span></span>](your-mixed-reality-home.md)
* [<span data-ttu-id="830a9-151">Система отслеживания</span><span class="sxs-lookup"><span data-stu-id="830a9-151">Tracking System</span></span>](tracking-system.md)
* [<span data-ttu-id="830a9-152">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="830a9-152">Motion Controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="830a9-153">SteamVR</span><span class="sxs-lookup"><span data-stu-id="830a9-153">SteamVR</span></span>](using-steamvr-with-windows-mixed-reality.md)
* [<span data-ttu-id="830a9-154">Отзывы о профиле</span><span class="sxs-lookup"><span data-stu-id="830a9-154">Filing feedback</span></span>](filing-feedback.md)
