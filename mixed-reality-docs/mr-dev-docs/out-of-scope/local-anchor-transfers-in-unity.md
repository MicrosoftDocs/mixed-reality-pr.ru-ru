---
title: Передача локальных привязок в Unity
description: узнайте, как передавать привязки между несколькими HoloLens устройствами в приложении Unity mixed reality.
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Совместное использование, привязка, Ворлданчор, MR совместное использование 250, Ворлданчортрансфербатч, Спатиалперцептион, перемещение, перенос локальной привязки, экспорт привязки, импорт привязки
ms.openlocfilehash: eaf25edbae39aab628277aa29f975f3d4d9d7374c796fd1b7b159053d4a46b95
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189131"
---
# <a name="local-anchor-transfers-in-unity"></a>Передача локальных привязок в Unity

в ситуациях, когда нельзя использовать <a href="/azure/spatial-anchors" target="_blank">пространственные привязки Azure</a>, передача локальных точек подключения позволяет одному HoloLens устройству экспортировать привязку, импортируемую вторым HoloLens устройством.

>[!NOTE]
>Передача локальных привязок обеспечивает менее устойчивое отзыв, чем <a href="/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>, а устройства iOS и Android не поддерживаются этим подходом.

### <a name="setting-the-spatialperception-capability"></a>Настройка возможности Спатиалперцептион

Чтобы приложение могла передавать пространственные привязки, необходимо включить возможность *спатиалперцептион* .

Как включить функцию *спатиалперцептион* :
1. в редакторе Unity откройте область **"Параметры проигрывателя"** (измените > Project Параметры > Player).
2. щелкните вкладку **"хранилище Windows"** .
3. разверните узел **"публикация Параметры"** и проверьте возможность **"спатиалперцептион** " в списке **"возможности"** .

>[!NOTE]
>если проект Unity уже экспортирован в Visual Studio решение, необходимо либо экспортировать в новую папку, либо вручную [установить эту возможность в AppxManifest в Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Перенос привязки

**Пространство имен:** *UnityEngine. XR. WSA. Sharing*<br>
**Тип**: *ворлданчортрансфербатч*

Чтобы передать [ворлданчор](../develop/unity/coordinate-systems-in-unity.md), необходимо установить привязку для передачи. пользователь одного HoloLens сканирует свою среду и либо вручную, либо программно выбирает точку в пространстве, чтобы быть привязкой для общего интерфейса. Данные, представляющие эту точку, можно затем сериализовать и передать на другие устройства, которые совместно используются в интерфейсе. Затем каждое устройство десериализует данные привязки и пытается нахождение точки в пространстве. Чтобы перемещение привязки работало, каждое устройство должно быть проверено в достаточном объеме среды, чтобы можно было идентифицировать точку, представленную привязкой.

### <a name="setup"></a>Установка

Пример кода на этой странице содержит несколько полей, которые необходимо инициализировать:
1. *GameObject рутгамеобжект* — это *GameObject* в Unity, на котором есть компонент *ворлданчор* . Один пользователь в общем интерфейсе поместит этот *GameObject* и экспортирует данные другим пользователям.
2. *Ворлданчор гамерутанчор* — это *UnityEngine. XR. WSA. ворлданчор* , который находится на *рутгамеобжект*.
3. *Byte [] импортеддата* является массивом байтов для сериализованной привязки, получаемой каждым клиентом по сети.

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a>Экспорт

Чтобы выполнить экспорт, нам нужно просто *ворлданчор* и знать, что именно мы его называю, что имеет смысл для принимающего приложения. Один клиент в общем интерфейсе выполняет следующие действия по экспорту общей привязки:
1. Создание *ворлданчортрансфербатч*
2. Добавление *ворлданчорс* для перемещения
3. Начать экспорт
4. Обрабатывает событие *онекспортдатааваилабле* , так как данные становятся доступными
5. Обрабатывает событие *онекспорткомплете*

Мы создадим *ворлданчортрансфербатч* , чтобы инкапсулировать, что мы будем передавать, а затем экспортировать в байты:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

По мере того как данные становятся доступными, отправьте их клиенту или буферу в виде сегментов данных и отправьте их по своему усмотрению:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

После завершения экспорта, если мы передавали данные и произошел сбой сериализации, сообщите клиенту об отмене данных. Если сериализация выполнена успешно, сообщите клиенту, что все данные были переданы и импорт может начаться:

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a>Импорт

После получения всех байтов от отправителя можно импортировать данные обратно в *ворлданчортрансфербатч* и заблокировать объект корневой игры в том же физическом расположении. Примечание. в некоторых случаях импорт будет временно невозможен и необходимо повторить попытку:

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

После того как *GameObject* блокируется через вызов *lockobject* , он будет иметь *ворлданчор* , который сохранит его в той же физической позиции в мире, но может находиться в другом месте в пространстве координат Unity, чем другие пользователи.