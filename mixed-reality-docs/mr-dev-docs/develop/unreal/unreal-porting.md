---
title: Обновление проектов в Unreal
description: Общие сведения о шагах обновления версии и нерекомендуемых API в проектах Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, документация, руководства, функции, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, перенос, обновление
ms.openlocfilehash: 0ba10b8ee1067da4494f147d43f8834010e1250f
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609665"
---
# <a name="upgrading-projects-in-unreal"></a><span data-ttu-id="63090-104">Обновление проектов в Unreal</span><span class="sxs-lookup"><span data-stu-id="63090-104">Upgrading projects in Unreal</span></span>

<span data-ttu-id="63090-105">При обновлении до новой версии Unreal для нерекомендуемых функций отображаются предупреждения при компиляции схем или упаковке проекта.</span><span class="sxs-lookup"><span data-stu-id="63090-105">When updating to a new version of Unreal, deprecated functions show up as warnings when compiling blueprints or packaging the project.</span></span>  <span data-ttu-id="63090-106">Функции считаются нерекомендуемыми, если существует новая функция, которую следует использовать вместо старой.</span><span class="sxs-lookup"><span data-stu-id="63090-106">Functions are deprecated when a new function has been added that should be used instead.</span></span> 

## <a name="426-upgrades"></a><span data-ttu-id="63090-107">Обновления в версии 4.26</span><span class="sxs-lookup"><span data-stu-id="63090-107">4.26 upgrades</span></span>
 
<span data-ttu-id="63090-108">В версии 4.26 все платформы дополненной и виртуальной реальности подверглись рефакторингу — были добавлены общие интерфейсы, а код приложения при этом сохранил независимость от платформы. Поэтому может отобразиться больше предупреждений, чем обычно.</span><span class="sxs-lookup"><span data-stu-id="63090-108">In 4.26, all AR and VR platforms have been refactored to add common interfaces and keep application code platform agnostic, so you may see more warnings than usual.</span></span>  <span data-ttu-id="63090-109">Обновление до новых API рекомендуется, чтобы упростить возможность переноса на другие платформы.</span><span class="sxs-lookup"><span data-stu-id="63090-109">Updating to the new APIs is recommended so the project can be more easily ported to other platforms.</span></span>

<span data-ttu-id="63090-110">В предупреждающих сообщениях указывается, какая функция устарела и какую функцию следует использовать.</span><span class="sxs-lookup"><span data-stu-id="63090-110">Warning messages will show which function has been deprecated and indicate what function to use instead.</span></span>  <span data-ttu-id="63090-111">Все нерекомендуемые функции будут работать в этом выпуске, но в будущих выпусках они могут быть недоступны.</span><span class="sxs-lookup"><span data-stu-id="63090-111">All deprecated functions will continue to work for this release but may not work in future releases.</span></span>  <span data-ttu-id="63090-112">Нерекомендуемые функции также больше не будут выводиться при поиске функций для схемы.</span><span class="sxs-lookup"><span data-stu-id="63090-112">Deprecated functions will also no longer be listed when searching for functions in a blueprint.</span></span>

![Схема функции Create Named ARPin](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a><span data-ttu-id="63090-114">Нерекомендуемые функции из версии 4.25</span><span class="sxs-lookup"><span data-stu-id="63090-114">4.25 deprecations</span></span>

| <span data-ttu-id="63090-115">Нерекомендуемая функция</span><span class="sxs-lookup"><span data-stu-id="63090-115">Deprecated function</span></span> | <span data-ttu-id="63090-116">Новая функция</span><span class="sxs-lookup"><span data-stu-id="63090-116">New function</span></span> |
| --- | --- |
| <span data-ttu-id="63090-117">CreateNamedARPin</span><span class="sxs-lookup"><span data-stu-id="63090-117">CreateNamedARPin</span></span> | ![Схема функции Pin Component](images/unreal-porting-img-02.png) |
| <span data-ttu-id="63090-119">LoadWMRAnchorStoreARPins</span><span class="sxs-lookup"><span data-stu-id="63090-119">LoadWMRAnchorStoreARPins</span></span> | ![Схема функции Load ARPins from Local Store](images/unreal-porting-img-03.png) |
| <span data-ttu-id="63090-121">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span><span class="sxs-lookup"><span data-stu-id="63090-121">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span></span> | ![Схема функции Save ARPin to Local Store](images/unreal-porting-img-04.png) |
| <span data-ttu-id="63090-123">RemoveARPinFromWMRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="63090-123">RemoveARPinFromWMRAnchorStore</span></span> | ![Схема функции Remove ARPin from Local Store](images/unreal-porting-img-05.png) |
| <span data-ttu-id="63090-125">SetEnabledMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="63090-125">SetEnabledMixedRealityCamera</span></span> | ![Схема функции Set Enabled XRCamera](images/unreal-porting-img-06.png) |
| <span data-ttu-id="63090-127">ResizeMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="63090-127">ResizeMixedRealityCamera</span></span> | ![Схема функции Resize XRCamera](images/unreal-porting-img-07.png) |
| <span data-ttu-id="63090-129">StartCameraCapture</span><span class="sxs-lookup"><span data-stu-id="63090-129">StartCameraCapture</span></span> | ![Схема функции Toggle ARCapture для запуска захвата с камеры](images/unreal-porting-img-08.png) |
| <span data-ttu-id="63090-131">StopCameraCapture</span><span class="sxs-lookup"><span data-stu-id="63090-131">StopCameraCapture</span></span> | ![Схема функции Toggle ARCapture для остановки захвата с камеры](images/unreal-porting-img-09.png) |
| <span data-ttu-id="63090-133">StartQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="63090-133">StartQRCodeCapture</span></span> | ![Схема функции Toggle ARCapture для запуска захвата QR-кода](images/unreal-porting-img-10.png) |
| <span data-ttu-id="63090-135">StopQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="63090-135">StopQRCodeCapture</span></span> | ![Схема функции Toggle ARCapture для остановки захвата QR-кода](images/unreal-porting-img-11.png) |
| <span data-ttu-id="63090-137">Пространственное сопоставление ранее автоматически запускалось в версии 4.25, но в версии 4.26 его нужно включить.</span><span class="sxs-lookup"><span data-stu-id="63090-137">Spatial mapping previously automatically started in 4.25, but now needs to be toggled in 4.26.</span></span> | ![Схема функции Toggle ARCapture для включения пространственного сопоставления](images/unreal-porting-img-12.png) |
| <span data-ttu-id="63090-139">ShowKeyboard</span><span class="sxs-lookup"><span data-stu-id="63090-139">ShowKeyboard</span></span> | <span data-ttu-id="63090-140">Удалена в версии 4.26, так как клавиатура отображается автоматически при наведении фокуса на текстовое мини-приложение.</span><span class="sxs-lookup"><span data-stu-id="63090-140">Removed in 4.26 since the keyboard automatically shows when a text widget is focused on.</span></span> |
| <span data-ttu-id="63090-141">HideKeyboard</span><span class="sxs-lookup"><span data-stu-id="63090-141">HideKeyboard</span></span> | <span data-ttu-id="63090-142">Удалена в версии 4.26, так как клавиатура скрывается автоматически при смещении фокуса с текстового мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="63090-142">Removed in 4.26 since the keyboard will automatically hide when a text widget is unfocused.</span></span> |
| <span data-ttu-id="63090-143">SupportsHandTracking</span><span class="sxs-lookup"><span data-stu-id="63090-143">SupportsHandTracking</span></span> | ![Схема свойства Supports Hand Tracking](images/unreal-porting-img-13.png) |
| <span data-ttu-id="63090-145">IsDisplayOpaque</span><span class="sxs-lookup"><span data-stu-id="63090-145">IsDisplayOpaque</span></span> | ![Схема свойства IsDisplayOpaque](images/unreal-porting-img-14.png) |
| <span data-ttu-id="63090-147">GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus</span><span class="sxs-lookup"><span data-stu-id="63090-147">GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus</span></span> | ![Схема функции Get Motion Controller Data](images/unreal-porting-img-15.png) |
| <span data-ttu-id="63090-149">GetVersionString</span><span class="sxs-lookup"><span data-stu-id="63090-149">GetVersionString</span></span> | ![Схема функции Get Version String](images/unreal-porting-img-16.png) |
| <span data-ttu-id="63090-151">IsTrackingAvailable</span><span class="sxs-lookup"><span data-stu-id="63090-151">IsTrackingAvailable</span></span> | ![Схема свойства IsTrackingAvailable](images/unreal-porting-img-17.png) |
| <span data-ttu-id="63090-153">IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed</span><span class="sxs-lookup"><span data-stu-id="63090-153">IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed</span></span> | <span data-ttu-id="63090-154">Используйте систему входных действий в Unreal.</span><span class="sxs-lookup"><span data-stu-id="63090-154">Use Unreal’s input action system.</span></span> |
| <span data-ttu-id="63090-155">SetFocusPointForFrame</span><span class="sxs-lookup"><span data-stu-id="63090-155">SetFocusPointForFrame</span></span> | <span data-ttu-id="63090-156">Удалена в версии 4.26.</span><span class="sxs-lookup"><span data-stu-id="63090-156">Removed in 4.26.</span></span>  <span data-ttu-id="63090-157">Ранее использовалась для повторного проецирования при удаленном взаимодействии, которое теперь поддерживает повторное проецирование глубины.</span><span class="sxs-lookup"><span data-stu-id="63090-157">Previously used for reprojection when remoting, which now supports depth reprojection.</span></span> |