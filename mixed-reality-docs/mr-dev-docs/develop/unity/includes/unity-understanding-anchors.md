---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719844"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + Опенкср](#tab/openxr)

Подключаемый модуль Mixed Reality Опенкср предоставляет базовые функции привязки с помощью реализации Арфаундатион **Аранчорманажер** Unity. Основные сведения о Аранчорс в Арфаундатион см. в руководстве по [арфаундатион для AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). 

# <a name="unity-20192020--windows-xr-plugin"></a>[Подключаемый модуль XR для Unity 2019/2020 + Windows](#tab/winxr)

Подключаемый модуль Mixed Reality Опенкср предоставляет базовые функции привязки с помощью реализации Арфаундатион **Аранчорманажер** Unity. Основные сведения о Аранчорс в Арфаундатион см. в руководстве по [арфаундатион для AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).

# <a name="legacy-wsa"></a>[Устаревший WSA](#tab/wsa)

## <a name="building-a-world-scale-experience"></a>Создание возможностей для мирового масштабирования

**Пространство имен:** *UnityEngine. XR. WSA*<br>
**Тип:** *ворлданчор*

Для полноценного **крупномасштабного взаимодействия** в HoloLens, который позволяет пользователям рыскающего более 5 метров, вам потребуются новые методы, кроме тех, которые используются для работы с масштабом комнаты. Одной из ключевых методик, которую вы будете использовать, является создание [пространственной привязки](../../../design/coordinate-systems.md#spatial-anchors) для блокировки кластера голограмм, точно на месте физического мира, независимо от того, на каком расстояние перемещен пользователь, а затем [снова находит эти голограммы в последующих сеансах](../../../design/coordinate-systems.md#spatial-anchor-persistence).

В Unity вы создаете пространственное привязку, добавив компонент Unity **ворлданчор** в GameObject.

### <a name="adding-a-world-anchor"></a>Добавление универсальной привязки

Чтобы добавить привязку по всему миру, вызовите `AddComponent<WorldAnchor>()` объект Game с преобразованием, которое необходимо привязать в реальном мире.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Вот и все! Этот объект игры теперь будет привязан к его текущему расположению в физическом мире. Вы можете увидеть, что его координаты Unity могут немного измениться с течением времени, чтобы обеспечить физическое выравнивание. Сведения о том, как закрепить это закрепленное расположение в следующем сеансе приложения, см. в статье [Загрузка универсальной привязки](#loading-a-worldanchor) .

### <a name="removing-a-world-anchor"></a>Удаление универсальной привязки

Если вы больше не хотите, чтобы GameObject заблокировались в физическом расположении и не планировали перемещать его, то можно просто вызвать Destroy в компоненте «Универсальная привязка».

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Если вы хотите переместить GameObject этот кадр, необходимо вызвать Дестройиммедиате.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Перемещение привязанного GameObject по всему миру

GameObject нельзя переместить, пока на нем есть универсальная привязка. Если вам нужно переместить GameObject этот кадр, сделайте следующее:

1. Дестройиммедиате компонент «мировая привязка»
2. Перемещение GameObject
3. Добавьте новый компонент универсальной привязки к GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Обработка изменений Локатабилити

Ворлданчор не может быть размещаемые в физическом мире на момент времени. В таком случае Unity не будет обновлять преобразование привязанного объекта. Это также можно изменить во время работы приложения. Сбой при обработке изменения в локатабилити приведет к тому, что объект не будет отображаться в правильном физическом расположении в мире.

Чтобы получать уведомления об изменениях локатабилити:

1. Подпишитесь на событие Онтраккингчанжед
2. Обработайте событие

Событие **онтраккингчанжед** будет вызываться при каждом изменении базовой пространственной привязки между состояниями размещаемые и not размещаемые.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Затем обработайте событие:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Иногда привязки размещаются немедленно. В этом случае для этого свойства объекта привязки будет задано значение true, если функция AddComponent <WorldAnchor> () возвращает. В результате событие Онтраккингчанжед не будет запущено. Чистый шаблон будет вызывать обработчик Онтраккингчанжед с начальным состоянием после присоединения привязки.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```