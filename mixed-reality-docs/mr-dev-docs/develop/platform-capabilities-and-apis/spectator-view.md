---
title: Spectator View
description: Визуализируйте голограммы с внешнего устройства для отображения или записи взаимодействий смешанной реальности на внешнем дисплее.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, камера, ARKit, HoloLens, смешанная реальность, MixedRealityToolkit, демонстрация, запись
ms.openlocfilehash: c344edea9b499bdff15d1d93e400b8be626a63b6
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530103"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="53ab3-104">Spectator View для HoloLens и HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="53ab3-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="53ab3-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="53ab3-106">Overview</span></span>

<span data-ttu-id="53ab3-107">Когда вы используете HoloLens, очень легко забыть, что человек без этого устройства не может наслаждаться его возможностями.</span><span class="sxs-lookup"><span data-stu-id="53ab3-107">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="53ab3-108">Представление наблюдателя позволяет другим видеть на двухмерном экране то, что видит пользователь HoloLens.</span><span class="sxs-lookup"><span data-stu-id="53ab3-108">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="53ab3-109">Это также быстрый и доступный способ для записи голограмм в HD-разрешении с помощью мобильных устройств и получения высококачественных записей голограмм с помощью видеокамер.</span><span class="sxs-lookup"><span data-stu-id="53ab3-109">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="53ab3-110">Основные ресурсы</span><span class="sxs-lookup"><span data-stu-id="53ab3-110">Key Resources</span></span>

* [<span data-ttu-id="53ab3-111">**Spectator View на сайте GitHub**</span><span class="sxs-lookup"><span data-stu-id="53ab3-111">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="53ab3-112">**Документация по Spectator View**</span><span class="sxs-lookup"><span data-stu-id="53ab3-112">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="53ab3-113">**Примеры для Spectator View**</span><span class="sxs-lookup"><span data-stu-id="53ab3-113">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="53ab3-114">Варианты использования</span><span class="sxs-lookup"><span data-stu-id="53ab3-114">Use Cases</span></span>

* <span data-ttu-id="53ab3-115">Вы можете записать взаимодействие со смешанной реальностью с помощью устройства iPhone или Android.</span><span class="sxs-lookup"><span data-stu-id="53ab3-115">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="53ab3-116">Записывайте взаимодействия в HD-разрешении и применяйте к голограммам сглаживание и затенение — это экономичный и быстрый способ для записи видео с голограммами.</span><span class="sxs-lookup"><span data-stu-id="53ab3-116">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="53ab3-117">Передавайте видеопоток среды смешанной реальности в Apple TV непосредственно с устройства iPhone или iPad без каких-либо задержек!</span><span class="sxs-lookup"><span data-stu-id="53ab3-117">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="53ab3-118">Покажите возможности работы гостям: позвольте пользователям без HoloLens увидеть, как можно взаимодействовать с голограммами, непосредственно на телефоне или планшете.</span><span class="sxs-lookup"><span data-stu-id="53ab3-118">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="53ab3-119">Текущие возможности</span><span class="sxs-lookup"><span data-stu-id="53ab3-119">Current Features</span></span>

* <span data-ttu-id="53ab3-120">Пространственная синхронизация голограмм позволяет всем пользователям видеть голограммы на одном и том же месте.</span><span class="sxs-lookup"><span data-stu-id="53ab3-120">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="53ab3-121">Поддержка iOS (устройства с поддержкой ARKit) и Android (устройства с поддержкой ARCore).</span><span class="sxs-lookup"><span data-stu-id="53ab3-121">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="53ab3-122">Несколько гостей iOS.</span><span class="sxs-lookup"><span data-stu-id="53ab3-122">Multiple iOS guests.</span></span>
<span data-ttu-id="53ab3-123">Запись видео, голограмм, окружающего звука и звука голограмм.</span><span class="sxs-lookup"><span data-stu-id="53ab3-123">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="53ab3-124">Опубликуйте лист, чтобы сохранить видео, и отправьте его по электронной почте или с помощью других вспомогательных приложений.</span><span class="sxs-lookup"><span data-stu-id="53ab3-124">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="53ab3-125">![Маркер](images/SpecViewPhoneDemo.jpg)
![Маркер](images/hololensspectatorview-500px.jpg) ![Маркер](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="53ab3-125">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="53ab3-126">В следующей таблице описаны различные функции Spectator View и их возможности.</span><span class="sxs-lookup"><span data-stu-id="53ab3-126">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="53ab3-127">Выберите вариант, который лучше всего соответствует вашим требованиям к записи видео.</span><span class="sxs-lookup"><span data-stu-id="53ab3-127">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="53ab3-128">функциональное назначение;</span><span class="sxs-lookup"><span data-stu-id="53ab3-128">Functionality</span></span>                                | <span data-ttu-id="53ab3-129">Мобильные приложения</span><span class="sxs-lookup"><span data-stu-id="53ab3-129">Mobile</span></span>                  |                    <span data-ttu-id="53ab3-130">Видеокамера</span><span class="sxs-lookup"><span data-stu-id="53ab3-130">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="53ab3-131">Качество HD</span><span class="sxs-lookup"><span data-stu-id="53ab3-131">HD quality</span></span>                           |         <span data-ttu-id="53ab3-132">Full HD</span><span class="sxs-lookup"><span data-stu-id="53ab3-132">Full HD</span></span>         |        <span data-ttu-id="53ab3-133">Профессиональная съемка (определяется видеокамерой)</span><span class="sxs-lookup"><span data-stu-id="53ab3-133">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="53ab3-134">Простое перемещение камеры</span><span class="sxs-lookup"><span data-stu-id="53ab3-134">Easy camera movement</span></span>                 |            <span data-ttu-id="53ab3-135">✔</span><span class="sxs-lookup"><span data-stu-id="53ab3-135">✔</span></span>            |                      <span data-ttu-id="53ab3-136">✔</span><span class="sxs-lookup"><span data-stu-id="53ab3-136">✔</span></span>                      |
| <span data-ttu-id="53ab3-137">Вид от третьего лица</span><span class="sxs-lookup"><span data-stu-id="53ab3-137">Third-person view</span></span>                    |            <span data-ttu-id="53ab3-138">✔</span><span class="sxs-lookup"><span data-stu-id="53ab3-138">✔</span></span>            |                      <span data-ttu-id="53ab3-139">✔</span><span class="sxs-lookup"><span data-stu-id="53ab3-139">✔</span></span>                      |
| <span data-ttu-id="53ab3-140">Возможность потоковой передачи на экраны</span><span class="sxs-lookup"><span data-stu-id="53ab3-140">Can be streamed to screens</span></span>           |            <span data-ttu-id="53ab3-141">✔</span><span class="sxs-lookup"><span data-stu-id="53ab3-141">✔</span></span>            |                      <span data-ttu-id="53ab3-142">✔</span><span class="sxs-lookup"><span data-stu-id="53ab3-142">✔</span></span>                      |
| <span data-ttu-id="53ab3-143">Портативные</span><span class="sxs-lookup"><span data-stu-id="53ab3-143">Portable</span></span>                             |            <span data-ttu-id="53ab3-144">✔</span><span class="sxs-lookup"><span data-stu-id="53ab3-144">✔</span></span>            |                                             |
| <span data-ttu-id="53ab3-145">Беспроводная связь</span><span class="sxs-lookup"><span data-stu-id="53ab3-145">Wireless</span></span>                             |            <span data-ttu-id="53ab3-146">✔</span><span class="sxs-lookup"><span data-stu-id="53ab3-146">✔</span></span>            |                                             |
| <span data-ttu-id="53ab3-147">Дополнительное обязательное оборудование</span><span class="sxs-lookup"><span data-stu-id="53ab3-147">Additional required hardware</span></span>         |     <span data-ttu-id="53ab3-148">Телефон Android, iPhone</span><span class="sxs-lookup"><span data-stu-id="53ab3-148">Android phone, iPhone</span></span>    | <span data-ttu-id="53ab3-149">HoloLens, обвес, штатив, видеокамера, компьютер и Unity</span><span class="sxs-lookup"><span data-stu-id="53ab3-149">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="53ab3-150">Вложения в оборудование</span><span class="sxs-lookup"><span data-stu-id="53ab3-150">Hardware investment</span></span>                  |           <span data-ttu-id="53ab3-151">Низкий</span><span class="sxs-lookup"><span data-stu-id="53ab3-151">Low</span></span>            |                     <span data-ttu-id="53ab3-152">Высокий</span><span class="sxs-lookup"><span data-stu-id="53ab3-152">High</span></span>                    |
| <span data-ttu-id="53ab3-153">Поддержка разных платформ</span><span class="sxs-lookup"><span data-stu-id="53ab3-153">Cross-platform</span></span>                       |           <span data-ttu-id="53ab3-154">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="53ab3-154">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="53ab3-155">Синхронизированное содержимое</span><span class="sxs-lookup"><span data-stu-id="53ab3-155">Synchronized content</span></span>                 |            <span data-ttu-id="53ab3-156">✔</span><span class="sxs-lookup"><span data-stu-id="53ab3-156">✔</span></span>            |                      <span data-ttu-id="53ab3-157">✔</span><span class="sxs-lookup"><span data-stu-id="53ab3-157">✔</span></span>                      |
| <span data-ttu-id="53ab3-158">Длительность настройки во время выполнения</span><span class="sxs-lookup"><span data-stu-id="53ab3-158">Runtime setup duration</span></span>               |         <span data-ttu-id="53ab3-159">Сразу же</span><span class="sxs-lookup"><span data-stu-id="53ab3-159">Instant</span></span>          |                     <span data-ttu-id="53ab3-160">Медл.</span><span class="sxs-lookup"><span data-stu-id="53ab3-160">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="53ab3-161">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="53ab3-161">See also</span></span>

* [<span data-ttu-id="53ab3-162">Смешанный захват реальности</span><span class="sxs-lookup"><span data-stu-id="53ab3-162">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="53ab3-163">Съемка смешанной реальности для разработчиков</span><span class="sxs-lookup"><span data-stu-id="53ab3-163">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="53ab3-164">Общий доступ в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="53ab3-164">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
