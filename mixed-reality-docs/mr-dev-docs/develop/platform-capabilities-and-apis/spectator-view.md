---
title: Spectator View
description: Визуализируйте голограммы с внешнего устройства для отображения или записи взаимодействий смешанной реальности на внешнем дисплее.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, камера, ARKit, HoloLens, смешанная реальность, MixedRealityToolkit, демонстрация, запись
ms.openlocfilehash: 1f61d2094ec2762ab22576d2eac85ed6bf81d5c7
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008614"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="e51fb-104">Spectator View для HoloLens и HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e51fb-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

<span data-ttu-id="e51fb-106">Когда вы используете HoloLens, очень легко забыть, что человек без этого устройства не может наслаждаться его возможностями.</span><span class="sxs-lookup"><span data-stu-id="e51fb-106">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="e51fb-107">Представление наблюдателя позволяет другим видеть на двухмерном экране то, что видит пользователь HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e51fb-107">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="e51fb-108">Это также быстрый и доступный способ для записи голограмм в HD-разрешении с помощью мобильных устройств и получения высококачественных записей голограмм с помощью видеокамер.</span><span class="sxs-lookup"><span data-stu-id="e51fb-108">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="e51fb-109">Основные ресурсы</span><span class="sxs-lookup"><span data-stu-id="e51fb-109">Key Resources</span></span>

* [<span data-ttu-id="e51fb-110">**Spectator View на сайте GitHub**</span><span class="sxs-lookup"><span data-stu-id="e51fb-110">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="e51fb-111">**Документация по Spectator View**</span><span class="sxs-lookup"><span data-stu-id="e51fb-111">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="e51fb-112">**Примеры для Spectator View**</span><span class="sxs-lookup"><span data-stu-id="e51fb-112">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="e51fb-113">Варианты использования</span><span class="sxs-lookup"><span data-stu-id="e51fb-113">Use Cases</span></span>

* <span data-ttu-id="e51fb-114">Вы можете записать взаимодействие со смешанной реальностью с помощью устройства iPhone или Android.</span><span class="sxs-lookup"><span data-stu-id="e51fb-114">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="e51fb-115">Записывайте взаимодействия в HD-разрешении и применяйте к голограммам сглаживание и затенение — это экономичный и быстрый способ для записи видео с голограммами.</span><span class="sxs-lookup"><span data-stu-id="e51fb-115">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="e51fb-116">Передавайте видеопоток среды смешанной реальности в Apple TV непосредственно с устройства iPhone или iPad без каких-либо задержек!</span><span class="sxs-lookup"><span data-stu-id="e51fb-116">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="e51fb-117">Покажите возможности работы гостям: позвольте пользователям без HoloLens увидеть, как можно взаимодействовать с голограммами, непосредственно на телефоне или планшете.</span><span class="sxs-lookup"><span data-stu-id="e51fb-117">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="e51fb-118">Текущие возможности</span><span class="sxs-lookup"><span data-stu-id="e51fb-118">Current Features</span></span>

* <span data-ttu-id="e51fb-119">Пространственная синхронизация голограмм позволяет всем пользователям видеть голограммы на одном и том же месте.</span><span class="sxs-lookup"><span data-stu-id="e51fb-119">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="e51fb-120">Поддержка iOS (устройства с поддержкой ARKit) и Android (устройства с поддержкой ARCore).</span><span class="sxs-lookup"><span data-stu-id="e51fb-120">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="e51fb-121">Несколько гостей iOS.</span><span class="sxs-lookup"><span data-stu-id="e51fb-121">Multiple iOS guests.</span></span>
<span data-ttu-id="e51fb-122">Запись видео, голограмм, окружающего звука и звука голограмм.</span><span class="sxs-lookup"><span data-stu-id="e51fb-122">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="e51fb-123">Опубликуйте лист, чтобы сохранить видео, и отправьте его по электронной почте или с помощью других вспомогательных приложений.</span><span class="sxs-lookup"><span data-stu-id="e51fb-123">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="e51fb-124">![Маркер](images/SpecViewPhoneDemo.jpg)
![Маркер](images/hololensspectatorview-500px.jpg) ![Маркер](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="e51fb-124">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="e51fb-125">В следующей таблице описаны различные функции Spectator View и их возможности.</span><span class="sxs-lookup"><span data-stu-id="e51fb-125">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="e51fb-126">Выберите вариант, который лучше всего соответствует вашим требованиям к записи видео.</span><span class="sxs-lookup"><span data-stu-id="e51fb-126">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="e51fb-127">функциональное назначение;</span><span class="sxs-lookup"><span data-stu-id="e51fb-127">Functionality</span></span>                                | <span data-ttu-id="e51fb-128">Мобильные приложения</span><span class="sxs-lookup"><span data-stu-id="e51fb-128">Mobile</span></span>                  |                    <span data-ttu-id="e51fb-129">Видеокамера</span><span class="sxs-lookup"><span data-stu-id="e51fb-129">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="e51fb-130">Качество HD</span><span class="sxs-lookup"><span data-stu-id="e51fb-130">HD quality</span></span>                           |         <span data-ttu-id="e51fb-131">Full HD</span><span class="sxs-lookup"><span data-stu-id="e51fb-131">Full HD</span></span>         |        <span data-ttu-id="e51fb-132">Профессиональная съемка (определяется видеокамерой)</span><span class="sxs-lookup"><span data-stu-id="e51fb-132">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="e51fb-133">Простое перемещение камеры</span><span class="sxs-lookup"><span data-stu-id="e51fb-133">Easy camera movement</span></span>                 |            <span data-ttu-id="e51fb-134">✔</span><span class="sxs-lookup"><span data-stu-id="e51fb-134">✔</span></span>            |                      <span data-ttu-id="e51fb-135">✔</span><span class="sxs-lookup"><span data-stu-id="e51fb-135">✔</span></span>                      |
| <span data-ttu-id="e51fb-136">Вид от третьего лица</span><span class="sxs-lookup"><span data-stu-id="e51fb-136">Third-person view</span></span>                    |            <span data-ttu-id="e51fb-137">✔</span><span class="sxs-lookup"><span data-stu-id="e51fb-137">✔</span></span>            |                      <span data-ttu-id="e51fb-138">✔</span><span class="sxs-lookup"><span data-stu-id="e51fb-138">✔</span></span>                      |
| <span data-ttu-id="e51fb-139">Возможность потоковой передачи на экраны</span><span class="sxs-lookup"><span data-stu-id="e51fb-139">Can be streamed to screens</span></span>           |            <span data-ttu-id="e51fb-140">✔</span><span class="sxs-lookup"><span data-stu-id="e51fb-140">✔</span></span>            |                      <span data-ttu-id="e51fb-141">✔</span><span class="sxs-lookup"><span data-stu-id="e51fb-141">✔</span></span>                      |
| <span data-ttu-id="e51fb-142">Портативные</span><span class="sxs-lookup"><span data-stu-id="e51fb-142">Portable</span></span>                             |            <span data-ttu-id="e51fb-143">✔</span><span class="sxs-lookup"><span data-stu-id="e51fb-143">✔</span></span>            |                                             |
| <span data-ttu-id="e51fb-144">Беспроводная связь</span><span class="sxs-lookup"><span data-stu-id="e51fb-144">Wireless</span></span>                             |            <span data-ttu-id="e51fb-145">✔</span><span class="sxs-lookup"><span data-stu-id="e51fb-145">✔</span></span>            |                                             |
| <span data-ttu-id="e51fb-146">Дополнительное обязательное оборудование</span><span class="sxs-lookup"><span data-stu-id="e51fb-146">Additional required hardware</span></span>         |     <span data-ttu-id="e51fb-147">Телефон Android, iPhone</span><span class="sxs-lookup"><span data-stu-id="e51fb-147">Android phone, iPhone</span></span>    | <span data-ttu-id="e51fb-148">HoloLens, обвес, штатив, видеокамера, компьютер и Unity</span><span class="sxs-lookup"><span data-stu-id="e51fb-148">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="e51fb-149">Вложения в оборудование</span><span class="sxs-lookup"><span data-stu-id="e51fb-149">Hardware investment</span></span>                  |           <span data-ttu-id="e51fb-150">Низкий</span><span class="sxs-lookup"><span data-stu-id="e51fb-150">Low</span></span>            |                     <span data-ttu-id="e51fb-151">Высокий</span><span class="sxs-lookup"><span data-stu-id="e51fb-151">High</span></span>                    |
| <span data-ttu-id="e51fb-152">Поддержка разных платформ</span><span class="sxs-lookup"><span data-stu-id="e51fb-152">Cross-platform</span></span>                       |           <span data-ttu-id="e51fb-153">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="e51fb-153">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="e51fb-154">Синхронизированное содержимое</span><span class="sxs-lookup"><span data-stu-id="e51fb-154">Synchronized content</span></span>                 |            <span data-ttu-id="e51fb-155">✔</span><span class="sxs-lookup"><span data-stu-id="e51fb-155">✔</span></span>            |                      <span data-ttu-id="e51fb-156">✔</span><span class="sxs-lookup"><span data-stu-id="e51fb-156">✔</span></span>                      |
| <span data-ttu-id="e51fb-157">Длительность настройки во время выполнения</span><span class="sxs-lookup"><span data-stu-id="e51fb-157">Runtime setup duration</span></span>               |         <span data-ttu-id="e51fb-158">Сразу же</span><span class="sxs-lookup"><span data-stu-id="e51fb-158">Instant</span></span>          |                     <span data-ttu-id="e51fb-159">Медл.</span><span class="sxs-lookup"><span data-stu-id="e51fb-159">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="e51fb-160">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e51fb-160">See also</span></span>

* [<span data-ttu-id="e51fb-161">Смешанный захват реальности</span><span class="sxs-lookup"><span data-stu-id="e51fb-161">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="e51fb-162">Съемка смешанной реальности для разработчиков</span><span class="sxs-lookup"><span data-stu-id="e51fb-162">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="e51fb-163">Общий доступ в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="e51fb-163">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
