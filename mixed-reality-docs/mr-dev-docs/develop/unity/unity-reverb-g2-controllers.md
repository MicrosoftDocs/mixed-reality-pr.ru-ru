---
title: HP reverbы G2 Controllers в Unity
description: Инструкции по использованию контроллеров HP REVERB G2 в Стеамвр и Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, переглагол, переглаголы G2, HP reverbы G2, Mixed Reality, разработка, контроллеры движения, ввод данных, функции, новый проект, эмулятор, документация, руководства, функции, голограммы, Разработка игр
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638391"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="9b0a2-104">HP reverbы G2 Controllers в Unity</span><span class="sxs-lookup"><span data-stu-id="9b0a2-104">HP Reverb G2 Controllers in Unity</span></span>

## <a name="getting-started"></a><span data-ttu-id="9b0a2-105">Начало работы</span><span class="sxs-lookup"><span data-stu-id="9b0a2-105">Getting started</span></span>

<span data-ttu-id="9b0a2-106">Если вы разрабатываете для Стеамвр или используете входной API Windows Mixed Reality (XR), дополнительная настройка не требуется для использования контроллера HP reverbа G2. Головк. Входные данные).</span><span class="sxs-lookup"><span data-stu-id="9b0a2-106">There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input).</span></span> <span data-ttu-id="9b0a2-107">Однако кнопки A, B, X, Y и триггера сжатие в настоящее время недоступны через диспетчер ввода, если не используется Стеамвр.</span><span class="sxs-lookup"><span data-stu-id="9b0a2-107">However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR.</span></span> <span data-ttu-id="9b0a2-108">Поддержка дополнительных входных данных G2 будет доступна в ближайшем будущем, поэтому обязательно выполните проверку.</span><span class="sxs-lookup"><span data-stu-id="9b0a2-108">Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!</span></span>

## <a name="porting-existing-applications"></a><span data-ttu-id="9b0a2-109">Перенос существующих приложений</span><span class="sxs-lookup"><span data-stu-id="9b0a2-109">Porting existing applications</span></span>

<span data-ttu-id="9b0a2-110">Если у вас уже есть приложение, разрабатываемое для впечатляющих головных телефонов Windows Mixed Reality, ознакомьтесь с нашим [руководством по переносу](../porting-apps/porting-guides.md) и [параметрами проекта](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) , чтобы получить общие рекомендации.</span><span class="sxs-lookup"><span data-stu-id="9b0a2-110">If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.</span></span>

## <a name="mapping-input"></a><span data-ttu-id="9b0a2-111">Вход сопоставления</span><span class="sxs-lookup"><span data-stu-id="9b0a2-111">Mapping input</span></span>

<span data-ttu-id="9b0a2-112">Когда вы будете готовы приступить к подключению входных данных для новых контроллеров, начните работу с раздела " [Сопоставление входных данных](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) " в пошаговом руководством по переносу.</span><span class="sxs-lookup"><span data-stu-id="9b0a2-112">When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide.</span></span> <span data-ttu-id="9b0a2-113">Инструкции по настройке входных данных в Unity подробно описаны в разделе [жесты и контроллеры движения](gestures-and-motion-controllers-in-unity.md), а также полная [Таблица сопоставления кнопок и осей](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) для справки.</span><span class="sxs-lookup"><span data-stu-id="9b0a2-113">Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b0a2-114">См. также статью</span><span class="sxs-lookup"><span data-stu-id="9b0a2-114">See also</span></span>
* [<span data-ttu-id="9b0a2-115">Обновление для SteamVR</span><span class="sxs-lookup"><span data-stu-id="9b0a2-115">Updating for SteamVR</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)