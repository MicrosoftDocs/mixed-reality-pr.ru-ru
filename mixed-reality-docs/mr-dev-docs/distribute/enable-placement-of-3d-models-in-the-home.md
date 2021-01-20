---
title: Размещение трехмерных моделей в доме
description: Узнайте, как разместить трехмерные модели с веб-сайта или приложения на домашней странице Windows Mixed Reality.
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, модель, место дома, место, мир, моделирование, Домашняя страница смешанная, Интернет, приложение, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 58da61add35546331ff8199fa20885f9869a9f43
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583807"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="85aef-104">Поддержка размещения трехмерных моделей в доме со смешанной реальностью</span><span class="sxs-lookup"><span data-stu-id="85aef-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="85aef-105">Эта функция была добавлена как часть [обновления Windows 10 от апреля 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018).</span><span class="sxs-lookup"><span data-stu-id="85aef-105">This feature was added as part of the [Windows 10 April 2018 Update](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018).</span></span> <span data-ttu-id="85aef-106">Более старые версии Windows несовместимы с этой функцией.</span><span class="sxs-lookup"><span data-stu-id="85aef-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="85aef-107">[Главная страница Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) — это отправная точка, в которой пользователи начинают работу перед запуском приложений.</span><span class="sxs-lookup"><span data-stu-id="85aef-107">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="85aef-108">В некоторых случаях двумерные приложения (например, приложения с голограммами) позволяют размещать трехмерные модели непосредственно в домашней среде "смешанной реальности" как украшения или для дальнейшей проверки в полном объеме.</span><span class="sxs-lookup"><span data-stu-id="85aef-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="85aef-109">*Протокол добавления модели* позволяет отправить трехмерную модель с веб-сайта или приложения непосредственно на домашнюю страницу Windows Mixed Reality, где они будут сохраняться как средства [запуска 3D-приложений](3d-app-launcher-design-guidance.md), 2D-приложения и голограммы.</span><span class="sxs-lookup"><span data-stu-id="85aef-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="85aef-110">Например, если вы разрабатываете приложение, которое охватывает каталог трехмерной мебели для создания пространства, используйте *Протокол добавления модели* , чтобы разрешить пользователям размещать эти модели трехмерной мебели из каталога.</span><span class="sxs-lookup"><span data-stu-id="85aef-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="85aef-111">После помещения в мир пользователи могут перемещать, изменять размер и удалять эти трехмерные модели так же, как и другие голограммы дома.</span><span class="sxs-lookup"><span data-stu-id="85aef-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="85aef-112">В этой статье приводятся общие сведения о реализации *протокола добавления модели* для предоставления пользователям возможности оформления своего мира трехмерными объектами из приложения или из Интернета.</span><span class="sxs-lookup"><span data-stu-id="85aef-112">This article provides an overview of implementing the *add model protocol* for enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="85aef-113">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="85aef-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="85aef-114"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="85aef-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="85aef-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="85aef-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="85aef-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="85aef-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="85aef-117">Добавление протокола модели</span><span class="sxs-lookup"><span data-stu-id="85aef-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="85aef-118">✔️</span><span class="sxs-lookup"><span data-stu-id="85aef-118">✔️</span></span></td>
        <td><span data-ttu-id="85aef-119">✔️</span><span class="sxs-lookup"><span data-stu-id="85aef-119">✔️</span></span></td>
    </tr>
</table>

## <a name="the-basics"></a><span data-ttu-id="85aef-120">Основные сведения</span><span class="sxs-lookup"><span data-stu-id="85aef-120">The basics</span></span>

<span data-ttu-id="85aef-121">Включить размещение трехмерных моделей в домашней среде Windows Mixed Reality можно двумя шагами:</span><span class="sxs-lookup"><span data-stu-id="85aef-121">There are two steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="85aef-122">[Убедитесь, что ваша трехмерная модель совместима с домашней системой Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="85aef-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="85aef-123">Реализуйте *Протокол добавления модели* в приложении или на веб-странице (в этой статье).</span><span class="sxs-lookup"><span data-stu-id="85aef-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="85aef-124">Реализация *протокола добавления модели*</span><span class="sxs-lookup"><span data-stu-id="85aef-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="85aef-125">После создания [совместимой трехмерной модели](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)можно реализовать *Протокол добавления модели* , активируя следующий URI с любой веб-страницы или приложения:</span><span class="sxs-lookup"><span data-stu-id="85aef-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="85aef-126">Если URI указывает на удаленный ресурс, он будет автоматически скачан и помещен в домашнюю страницу.</span><span class="sxs-lookup"><span data-stu-id="85aef-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="85aef-127">Локальные ресурсы будут скопированы в папку данных приложения для дома смешанной реальности перед размещением в домашней папке.</span><span class="sxs-lookup"><span data-stu-id="85aef-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="85aef-128">Мы рекомендуем разработать свой опыт для учета сценариев, в которых пользователь может работать под управлением более старой версии Windows, которая не поддерживает эту функцию, скрывая кнопку или отключая ее по возможности.</span><span class="sxs-lookup"><span data-stu-id="85aef-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="85aef-129">Вызов *протокола добавления модели* из приложения универсальная платформа Windows:</span><span class="sxs-lookup"><span data-stu-id="85aef-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="85aef-130">Вызов *протокола добавления модели* с веб-страницы:</span><span class="sxs-lookup"><span data-stu-id="85aef-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="85aef-131">Рекомендации для головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="85aef-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="85aef-132">Для головных гарнитур (VR) на портале Mixed Reality не должно выполняться до вызова *протокола добавления модели*.</span><span class="sxs-lookup"><span data-stu-id="85aef-132">For immersive (VR) headsets, the Mixed Reality Portal doesn't have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="85aef-133">В этом случае *Протокол добавления модели* запустит портал Mixed Reality и поместит объект непосредственно там, где будет смотреться гарнитура, когда вы поступите на главную страницу Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="85aef-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="85aef-134">При вызове *протокола добавления модели* с рабочего стола с уже запущенным порталом Mixed Reality убедитесь, что головной телефон находится в спящем режиме.</span><span class="sxs-lookup"><span data-stu-id="85aef-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="85aef-135">В противном случае размещение не будет выполняться.</span><span class="sxs-lookup"><span data-stu-id="85aef-135">If not, the placement won't succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="85aef-136">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="85aef-136">See also</span></span>

* [<span data-ttu-id="85aef-137">Создание трехмерных моделей для использования на домашней странице Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="85aef-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="85aef-138">Навигация по дому с технологией Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="85aef-138">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)