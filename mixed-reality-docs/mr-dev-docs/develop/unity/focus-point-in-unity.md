---
title: Точка фокусировки в Unity
description: Узнайте, как вручную настроить стабильность в Unity, установив точку фокусировки для захватывающих головных телефонов HoloLens и Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, точка фокусировки, плоскость фокусировки, стабилизации плоскость, стабилизации точка, репроект, ЛСР, буфер глубины, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 2ceb5f2b58cbd1571b2d9f4de79acfe45779bfea
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226403"
---
# <a name="focus-point-in-unity"></a>Точка фокусировки в Unity

**Пространство имен:** *UnityEngine. XR. WSA*<br>
**Тип**: *холографиксеттингс*

Используйте [точку фокусировки](../platform-capabilities-and-apis/hologram-stability.md#reprojection) , чтобы предоставить HoloLens указание о том, как лучше стабилизировать отображаемые в данный момент голограммы.

Если вы хотите задать точку фокусировки в Unity, необходимо задать каждый кадр с помощью *холографиксеттингс. сетфокуспоинтфорфраме ()*. Если точка фокусировки не задана для рамки, используется плоскость стабилизации по умолчанию.

> [!NOTE]
> По умолчанию в новых проектах Unity установлен параметр "включить совместное использование буфера глубины".  С помощью этого параметра приложение Unity, работающее на высококлассной гарнитуре или на HoloLens под управлением Windows 10 2018 апреля Update (RS4) или более поздней версии, будет отправлять в Windows буфер глубины, чтобы автоматически оптимизировать стабильность, без приложения, указывающего на точку фокусировки:
> * На увлекательной гарнитуре настольной системы это позволит репроектировать на основе глубины на уровне точек.
> * В HoloLens с обновлением Windows 10 от апреля 2018 или более поздней версии будет проанализирован буфер глубины, чтобы автоматически выбрать оптимальную плоскость стабилизации.
>
> Любой из этих подходов должен обеспечить еще более высокое качество изображения без явной работы приложения, чтобы выбрать точку фокусировки для каждого кадра.  Обратите внимание, что если вы предложит точку фокусировки вручную, это переопределит автоматическое поведение, описанное выше, и обычно снизит стабильность.  Как правило, при выполнении приложения на HoloLens, который еще не обновлялся до обновления Windows 10 апреля 2018, следует указывать только точку фокусировки вручную.

### <a name="example"></a>Пример

Существует множество способов задать точку фокусировки, как предлагается перегрузки, доступные в статической функции *сетфокуспоинтфорфраме* . Ниже приведен простой пример для установки плоскости фокусировки на предоставленный объект для каждого кадра:

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

> [!NOTE]
> Приведенный выше простой код может снизить стабильность, если объект, которым он нацелен, заканчивается за пользователем. Обычно рекомендуется задать параметр **[включить совместное использование буфера глубины](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** вместо того, чтобы вручную указать точку фокусировки.

## <a name="next-development-checkpoint"></a>Следующий этап разработки

Если вы подготовились к расположению разработки Unity, мы собрались изучить возможности и API платформы смешанной реальности. Вы можете перейти к следующей статье:

> [!div class="nextstepaction"]
> [потеря слежения](tracking-loss-in-unity.md);

Или сразу перейдите к развертыванию приложения на устройстве или эмуляторе:

> [!div class="nextstepaction"]
> [Развертывание в HoloLens или в виде впечатляющих головных телефонов Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)

Вы можете в любой момент вернуться к [этапам разработки для Unity](unity-development-overview.md#3-advanced-features).

### <a name="see-also"></a>См. также раздел

* [Плоскость стабилизации](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
