---
title: Обновление проектов в Unreal
description: Общие сведения о шагах обновления версии и нерекомендуемых API в проектах Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, разработка, документация, руководства, функции, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, перенос, обновление
ms.openlocfilehash: 5460ab55c887c44029e956545cf6a549f55716f7
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010625"
---
# <a name="upgrading-projects-in-unreal"></a>Обновление проектов в Unreal

При обновлении до новой версии Unreal для нерекомендуемых функций отображаются предупреждения при компиляции схем или упаковке проекта.  Функции считаются нерекомендуемыми, если существует новая функция, которую следует использовать вместо старой. 

## <a name="426-upgrades"></a>Обновления в версии 4.26
 
В версии 4.26 все платформы дополненной и виртуальной реальности подверглись рефакторингу — были добавлены общие интерфейсы, а код приложения при этом сохранил независимость от платформы. Поэтому может отобразиться больше предупреждений, чем обычно.  Обновление до новых API рекомендуется, чтобы упростить возможность переноса на другие платформы.

В предупреждающих сообщениях указывается, какая функция устарела и какую функцию следует использовать.  Все нерекомендуемые функции будут работать в этом выпуске, но в будущих выпусках они могут быть недоступны.  Нерекомендуемые функции также больше не будут выводиться при поиске функций для схемы.

![Схема функции Create Named ARPin](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a>Нерекомендуемые функции из версии 4.25

| Нерекомендуемая функция | Новая функция |
| --- | --- |
| CreateNamedARPin | ![Схема функции Pin Component](images/unreal-porting-img-02.png) |
| LoadWMRAnchorStoreARPins | ![Схема функции Load ARPins from Local Store](images/unreal-porting-img-03.png) |
| LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins | ![Схема функции Save ARPin to Local Store](images/unreal-porting-img-04.png) |
| RemoveARPinFromWMRAnchorStore | ![Схема функции Remove ARPin from Local Store](images/unreal-porting-img-05.png) |
| SetEnabledMixedRealityCamera | ![Схема функции Set Enabled XRCamera](images/unreal-porting-img-06.png) |
| ResizeMixedRealityCamera | ![Схема функции Resize XRCamera](images/unreal-porting-img-07.png) |
| StartCameraCapture | ![Схема функции Toggle ARCapture для запуска захвата с камеры](images/unreal-porting-img-08.png) |
| StopCameraCapture | ![Схема функции Toggle ARCapture для остановки захвата с камеры](images/unreal-porting-img-09.png) |
| StartQRCodeCapture | ![Схема функции Toggle ARCapture для запуска захвата QR-кода](images/unreal-porting-img-10.png) |
| StopQRCodeCapture | ![Схема функции Toggle ARCapture для остановки захвата QR-кода](images/unreal-porting-img-11.png) |
| Пространственное сопоставление ранее автоматически запускалось в версии 4.25, но в версии 4.26 его нужно включить. | ![Схема функции Toggle ARCapture для включения пространственного сопоставления](images/unreal-porting-img-12.png) |
| ShowKeyboard | Удалена в версии 4.26, так как клавиатура отображается автоматически при наведении фокуса на текстовое мини-приложение. |
| HideKeyboard | Удалена в версии 4.26, так как клавиатура скрывается автоматически при смещении фокуса с текстового мини-приложения. |
| SupportsHandTracking | ![Схема свойства Supports Hand Tracking](images/unreal-porting-img-13.png) |
| IsDisplayOpaque | ![Схема свойства IsDisplayOpaque](images/unreal-porting-img-14.png) |
| GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus | ![Схема функции Get Motion Controller Data](images/unreal-porting-img-15.png) |
| GetVersionString | ![Схема функции Get Version String](images/unreal-porting-img-16.png) |
| IsTrackingAvailable | ![Схема свойства IsTrackingAvailable](images/unreal-porting-img-17.png) |
| IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed | Используйте систему входных действий в Unreal. |
| SetFocusPointForFrame | Удалена в версии 4.26.  Ранее использовалась для повторного проецирования при удаленном взаимодействии, которое теперь поддерживает повторное проецирование глубины. |

## <a name="426-changes"></a>Изменения в версии 4.26

Существенным изменением является то, что параметр **Start in VR** (Запустить в виртуальной реальности) на вкладке **Edit > Project Settings > Project > Description > Settings** (Правка > Параметры проекта > Проект > Описание > Настройки) обязателен для запуска подключаемого модуля Windows Mixed Reality. Без него вы не сможете видеть голограммы на устройстве.
