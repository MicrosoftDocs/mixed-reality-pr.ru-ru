---
title: Заметки о выпуске подключаемого модуля OpenXR для смешанной реальности
description: Оставайтесь в курсе последних заметок о выпуске и обновлениях для подключаемого модуля OpenXR для смешанной реальности.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394632"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a><span data-ttu-id="007f6-104">Заметки о выпуске подключаемого модуля OpenXR для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="007f6-104">Mixed Reality OpenXR plugin release notes</span></span>

## <a name="100---current-release"></a><span data-ttu-id="007f6-105">Текущая версия — 1.0.0</span><span class="sxs-lookup"><span data-stu-id="007f6-105">1.0.0 - Current release</span></span>

* <span data-ttu-id="007f6-106">Исправлена ошибка, из-за которой XRAnchorSubsystem был всегда запущен при запуске приложения, независимо от наличия ARAnchorManager.</span><span class="sxs-lookup"><span data-stu-id="007f6-106">Fixed a bug where a the XRAnchorSubsystem was always started on app start regardless ARAnchorManager’s present.</span></span>
* <span data-ttu-id="007f6-107">Исправлена ошибка, из-за которой режим перепроецирования не работал должным образом.</span><span class="sxs-lookup"><span data-stu-id="007f6-107">Fixed a bug where the reprojection mode didn’t work properly.</span></span>

## <a name="100-preview2---2021-06-14"></a><span data-ttu-id="007f6-108">1.0.0-preview.2 — 2021-06-14</span><span class="sxs-lookup"><span data-stu-id="007f6-108">1.0.0-preview.2 - 2021-06-14</span></span>

* <span data-ttu-id="007f6-109">Зависит от подключаемого модуля 1.2.2 OpenXR Unity.</span><span class="sxs-lookup"><span data-stu-id="007f6-109">Depends on Unity’s 1.2.2 OpenXR plugin.</span></span>
* <span data-ttu-id="007f6-110">Изменены функции голографического удаленного взаимодействия Holographic Remoting для отдельных групп функций.</span><span class="sxs-lookup"><span data-stu-id="007f6-110">Changed Holographic Remoting features in to individual feature groups.</span></span>
* <span data-ttu-id="007f6-111">Исправлена ошибка, при которой из-за применения настроек проекта HoloLens 2 изменялась цветовая область проекта.</span><span class="sxs-lookup"><span data-stu-id="007f6-111">Fixed a bug where “Apply HoloLens 2 project settings” changes project color space.</span></span> <span data-ttu-id="007f6-112">Это исправление не требуется для подключаемого модуля Unity OpenXR версии 1.2.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="007f6-112">This is no longer needed after Unity OpenXR 1.2.0 plugin.</span></span>
* <span data-ttu-id="007f6-113">Исправлена ошибка, при которой входное устройство подключалось без отключения после приостановки и возобновления работы приложения.</span><span class="sxs-lookup"><span data-stu-id="007f6-113">Fixed a bug where a input device get connected without disconnect after application suspended and resumed.</span></span>
* <span data-ttu-id="007f6-114">Добавлена поддержка обнаружения подключаемого модуля и текущего состояния отслеживания через ARSession.</span><span class="sxs-lookup"><span data-stu-id="007f6-114">Added support for detecting plugin and current tracking states via ARSession.</span></span>
* <span data-ttu-id="007f6-115">Исправлена ошибка, из-за которой заготовка ARFoundation "AR Default Plane" не отображалась.</span><span class="sxs-lookup"><span data-stu-id="007f6-115">Fixed a bug where the “AR Default Plane” ARFoundation prefab wouldn’t be visible.</span></span>

## <a name="100-preview1---2021-06-02"></a><span data-ttu-id="007f6-116">1.0.0-preview.1 — 2021-06-02</span><span class="sxs-lookup"><span data-stu-id="007f6-116">1.0.0-preview.1 - 2021-06-02</span></span>

* <span data-ttu-id="007f6-117">Поддерживает расширения MSFT для интерпретаций сцен OpenXR вместо расширений для предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="007f6-117">Supports OpenXR scene understanding MSFT extensions instead of preview extensions.</span></span>
* <span data-ttu-id="007f6-118">Обнаружение плоскости в HoloLens 2 больше не требует предварительных версий сред выполнения OpenXR смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="007f6-118">Plane detection on HoloLens 2 no longer requires preview versions of the Mixed Reality OpenXR runtimes.</span></span>

## <a name="095---2021-05-21"></a><span data-ttu-id="007f6-119">0.9.5 — 2021-05-21</span><span class="sxs-lookup"><span data-stu-id="007f6-119">0.9.5 - 2021-05-21</span></span>

* <span data-ttu-id="007f6-120">Зависит от подключаемого модуля 1.2.0 OpenXR Unity.</span><span class="sxs-lookup"><span data-stu-id="007f6-120">Depends on Unity’s 1.2.0 OpenXR Plugin</span></span>
* <span data-ttu-id="007f6-121">Адаптация к новому пользовательскому интерфейсу компонента (в подключаемом модуле OpenXR 1.2.0) для конфигурации.</span><span class="sxs-lookup"><span data-stu-id="007f6-121">Adapted to the new feature UI (in OpenXR Plugin 1.2.0) for configuration.</span></span>
* <span data-ttu-id="007f6-122">Исправлена ошибка, при которой поставщик обнаруживаемой камеры не регистрировался должным образом.</span><span class="sxs-lookup"><span data-stu-id="007f6-122">Fixed a bug where the locatable camera provider wasn’t properly unregistering.</span></span>
* <span data-ttu-id="007f6-123">Очищено несколько дополнительных использований [Preserve].</span><span class="sxs-lookup"><span data-stu-id="007f6-123">Cleaned up some extra usages of [Preserve].</span></span>
* <span data-ttu-id="007f6-124">В пользовательском интерфейсе системы ввода обновлено имя контроллера "HP Reverb G2 Controller (OpenXR)".</span><span class="sxs-lookup"><span data-stu-id="007f6-124">Update “HP Reverb G2 Controller (OpenXR)” name in the input system UI.</span></span>

## <a name="094---2021-05-20"></a><span data-ttu-id="007f6-125">0.9.4 — 2021-05-20</span><span class="sxs-lookup"><span data-stu-id="007f6-125">0.9.4 - 2021-05-20</span></span>

* <span data-ttu-id="007f6-126">Зависит от подключаемого модуля 1.2.0 OpenXR Unity.</span><span class="sxs-lookup"><span data-stu-id="007f6-126">Depends on Unity’s 1.2.0 OpenXR Plugin.</span></span>
* <span data-ttu-id="007f6-127">Добавлен новый API C# для получения модели glTF контроллера движения.</span><span class="sxs-lookup"><span data-stu-id="007f6-127">Added new C# API to get motion controller glTF model.</span></span>
* <span data-ttu-id="007f6-128">Добавлен новый API C# для получения включенных конфигураций представлений и задания параметров перепроецирования.</span><span class="sxs-lookup"><span data-stu-id="007f6-128">Added new C# API to get enabled view configurations and set reprojection settings.</span></span>
* <span data-ttu-id="007f6-129">Добавлен новый API C# для настройки дополнительных параметров для вычисления сеток с помощью XRMeshSubsystem.</span><span class="sxs-lookup"><span data-stu-id="007f6-129">Added new C# API to set additional settings for computing meshes with XRMeshSubsystem.</span></span>
* <span data-ttu-id="007f6-130">Добавлен новый API C# для подписки на события распознавания жестов и их настройки.</span><span class="sxs-lookup"><span data-stu-id="007f6-130">Added new C# API to configure and subscribe to gesture recognition events.</span></span>
* <span data-ttu-id="007f6-131">Добавлено диалоговое окно параметров Windows->XR->Editor Remoting.</span><span class="sxs-lookup"><span data-stu-id="007f6-131">Added Windows->XR->Editor Remoting settings dialog.</span></span>
* <span data-ttu-id="007f6-132">Добавлена поддержка ARM для приложений UWP HoloLens.</span><span class="sxs-lookup"><span data-stu-id="007f6-132">Added ARM support for HoloLens UWP applications.</span></span>

## <a name="093---2021-04-29"></a><span data-ttu-id="007f6-133">0.9.3 — 2021-04-29</span><span class="sxs-lookup"><span data-stu-id="007f6-133">0.9.3 - 2021-04-29</span></span>

* <span data-ttu-id="007f6-134">Исправлена ошибка, при которой подключение для голографического удаленного взаимодействия было ненадежным.</span><span class="sxs-lookup"><span data-stu-id="007f6-134">Fixed a bug where Holographic remoting connection is not reliable</span></span>
* <span data-ttu-id="007f6-135">Исправлена ошибка, из-за которой производительность отрисовки VR являлась неоптимальной после обновления до подключаемого модуля 1.1.1 OpenXR Unity.</span><span class="sxs-lookup"><span data-stu-id="007f6-135">Fixed a bug where the VR rendering performance is sub-optimum after upgrade to Unity’s 1.1.1 OpenXR plugin.</span></span>

## <a name="092---2021-04-21"></a><span data-ttu-id="007f6-136">0.9.2 — 2021-04-21</span><span class="sxs-lookup"><span data-stu-id="007f6-136">0.9.2 - 2021-04-21</span></span>

* <span data-ttu-id="007f6-137">Обнаружение плоскости на HoloLens 2 в подключаемом модуле версии 0.9.1 будет работать с версией 105 среды выполнения смешанной реальности OpenXR (предварительная версия).</span><span class="sxs-lookup"><span data-stu-id="007f6-137">Plane detection on HoloLens 2 in plugin version 0.9.1 will work with version 105 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="007f6-138">Обнаружение плоскости на HoloLens 2 в подключаемом модуле версии 0.9.2 будет работать с версией 106 среды выполнения смешанной реальности OpenXR (предварительная версия).</span><span class="sxs-lookup"><span data-stu-id="007f6-138">Plane detection on HoloLens 2 in plugin version 0.9.2 will work with version 106 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="007f6-139">Удалены некоторые неиспользуемые обратные вызовы из InputProvider, чтобы предотвратить возвращение успешных вызовов, таких как XRInputSubsystem.\* GetTrackingOriginMode (которые не управляются нашей входной системой).</span><span class="sxs-lookup"><span data-stu-id="007f6-139">Removed some unused callbacks from InputProvider to prevent calls like XRInputSubsystem.\* GetTrackingOriginMode (which aren’t managed by our input system) from returning success with misleading values.</span></span>
* <span data-ttu-id="007f6-140">Устаревшая версия XRAnchorStore выделена в свой собственный файл, чтобы предотвратить предупреждение консоли Unity.</span><span class="sxs-lookup"><span data-stu-id="007f6-140">Split out deprecated version of XRAnchorStore into its own file to prevent Unity console warning.</span></span>

## <a name="091---2021-04-20"></a><span data-ttu-id="007f6-141">0.9.1 — 2021-04-20</span><span class="sxs-lookup"><span data-stu-id="007f6-141">0.9.1 - 2021-04-20</span></span>

* <span data-ttu-id="007f6-142">Зависит от подключаемого модуля 1.1.1 OpenXR Unity.</span><span class="sxs-lookup"><span data-stu-id="007f6-142">Depends on Unity’s 1.1.1 OpenXR Plugin.</span></span>
* <span data-ttu-id="007f6-143">Добавлена поддержка приложения Holographic Remoting для платформы UWP.</span><span class="sxs-lookup"><span data-stu-id="007f6-143">Added support for Holographic Remoting application for UWP platform.</span></span>
* <span data-ttu-id="007f6-144">Исправление UnityException, где XRAnchorStore пытался получить экземпляр параметров за пределами основного потока.</span><span class="sxs-lookup"><span data-stu-id="007f6-144">Fix UnityException where XRAnchorStore was trying to get a settings instance outside the main thread.</span></span>

## <a name="090---2021-03-29"></a><span data-ttu-id="007f6-145">0.9.0 — 2021-03-29</span><span class="sxs-lookup"><span data-stu-id="007f6-145">0.9.0 - 2021-03-29</span></span>

* <span data-ttu-id="007f6-146">Добавлена поддержка пространственного сопоставления через XRMeshSubsystem и ARMeshManager.</span><span class="sxs-lookup"><span data-stu-id="007f6-146">Added support for spatial mapping via XRMeshSubsystem and ARMeshManager.</span></span>
* <span data-ttu-id="007f6-147">Добавлен новый API C# для получения дескрипторов OpenXR для поддержки других пакетов Unity, использующих расширения OpenXR.</span><span class="sxs-lookup"><span data-stu-id="007f6-147">Added new C# API to get OpenXR handles to support other Unity packages consumes OpenXR extensions.</span></span>
* <span data-ttu-id="007f6-148">Добавлен новый API C# для взаимодействия с API Windows.Perception для поддержки других пакетов Unity, использующих API-интерфейсы WinRT.</span><span class="sxs-lookup"><span data-stu-id="007f6-148">Added new C# API to interop with Windows.Perception APIs to support other Unity packages consuming Perception WinRT APIs.</span></span>
* <span data-ttu-id="007f6-149">Удалены профили взаимодействия из требуемых функций в наборе функций Windows Mixed Reality, чтобы разработчики могли выбрать контроллеры движений, которые тестировались.</span><span class="sxs-lookup"><span data-stu-id="007f6-149">Removed interaction profiles from required features in Windows Mixed Reality feature set, so developers can choose the motion controllers they tested with.</span></span>
* <span data-ttu-id="007f6-150">Добавлена проверка функции редактора голографического удаленного взаимодействия для помощи пользователям в настройке.</span><span class="sxs-lookup"><span data-stu-id="007f6-150">Added Holographic editor remoting feature validator to help users to setup editor remoting properly.</span></span>
* <span data-ttu-id="007f6-151">Исправлена ошибка, из-за которой работа редактора Unity аварийно завершалась при выходе из строя режима голографического удаленного взаимодействия после сбоя подключения.</span><span class="sxs-lookup"><span data-stu-id="007f6-151">Fixed a bug where Unity editor crashes when exiting Holographic editor remoting mode after connection failure.</span></span>
* <span data-ttu-id="007f6-152">Исправлена ошибка, при которой неумноженные альфа-текстуры приводили к неоптимальной производительности на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="007f6-152">Fixed a bug where unpremultipled alpha textures leads to sub-optimum performance on HoloLens 2.</span></span>
* <span data-ttu-id="007f6-153">Исправлена ошибка, при которой отслеживание было обнаружено неправильно, если источник сцены был на уровне пола.</span><span class="sxs-lookup"><span data-stu-id="007f6-153">Fixed a bug where hand tracking was not located correctly when the scene origin was at floor level.</span></span>
* <span data-ttu-id="007f6-154">Исправлена ошибка, из-за которой отслеживание сетки исчезало после завершения и загрузки новой сцены.</span><span class="sxs-lookup"><span data-stu-id="007f6-154">Fixed a bug where hand mesh tracking disappear after leaving and loading a new scene.</span></span>
* <span data-ttu-id="007f6-155">Исправлена ошибка, при которой поставщик обнаруживаемой камеры не очищался должным образом.</span><span class="sxs-lookup"><span data-stu-id="007f6-155">Fixed a bug where locatable camera provider didn’t properly clean up.</span></span>
* <span data-ttu-id="007f6-156">Изменено пространство имен API XRAnchorStore на Microsoft.MixedReality.OpenXR.</span><span class="sxs-lookup"><span data-stu-id="007f6-156">Revised the namespace of XRAnchorStore API into Microsoft.MixedReality.OpenXR.</span></span>