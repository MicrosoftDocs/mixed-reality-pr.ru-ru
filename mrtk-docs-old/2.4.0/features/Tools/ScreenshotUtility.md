---
title: ScreenshotUtility
description: Документация по использованию средства для создания снимков экрана в MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, смешанная реальность, разработка, MRTK
ms.openlocfilehash: 6aafcf6602caae94cf69bc62faf02601de830bbd
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687894"
---
# <a name="screenshot-utility"></a>Служебная программа для создания снимков экрана

Если вы часто создаете снимки экрана в Unity для документации и рекламных материалов, этот процесс может быть очень трудоемким и не давать желаемых результатов. Решить эти проблемы поможет `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility).

Класс ScreenshotUtility позволяет создавать снимки экрана через пункты меню и общедоступные API в редакторе Unity. Снимки экрана можно создавать с разным разрешением и прозрачными цветами для последующего простого наложения изображений. Это средство не поддерживает создание снимков экрана из изолированной сборки.

## <a name="taking-screenshots"></a>Создание снимков экрана

Создавать снимки экрана очень легко: выберите в редакторе *Mixed Reality Toolkit->Utilities->Take Screenshot* (Mixed Reality Toolkit -> Средства -> Сделать снимок экрана) и выберите нужный вариант. Если вы создаете снимок экрана не во время игры, убедитесь, что вкладка с окном игры отображается. В противном случае снимок экрана не будет сохранен.

По умолчанию все снимки экрана сохраняются по [пути временного кэша](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), а путь к самому снимку экрана отобразится в консоли Unity.

![Пункт меню служебной программы для создания снимков экрана](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>Пример создания снимка экрана

Приведенный ниже снимок экрана был создан с использованием варианта *"4x Resolution (Transparent Background)"* (Четырехкратное разрешение (прозрачный фон)). При этом создается изображение с высоким разрешением и преобразованием пикселей с удаленным цветом в прозрачные пиксели. Это позволяет разработчикам продемонстрировать использование своего приложения в магазине или других на других медиаплощадках, наложив это изображение поверх других изображений.

![Пример захвата с помощью служебной программы для создания снимков экрана](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Example_Capture.png)
