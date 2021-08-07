---
title: Размещение трехмерных моделей в доме
description: узнайте, как разместить трехмерные модели с веб-сайта или приложения на Windows Mixed Reality домашней странице.
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, модель, место дома, место, мир, моделирование, Домашняя страница смешанная, Интернет, приложение, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 29761cb2a8725221a3be90187488cb13bf6643e4ff334a1edca73e633e7b1d4c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186800"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Поддержка размещения трехмерных моделей в доме со смешанной реальностью

> [!NOTE]
> эта функция была добавлена как часть [Windows 10 обновления за апрель 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018). более старые версии Windows несовместимы с этой функцией.

[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) является отправной точкой, где пользователи начинают работу перед запуском приложений. в некоторых сценариях двумерные приложения (например, Голограммыное приложение) позволяют размещать трехмерные модели непосредственно в домашней среде "смешанной реальности" как украшения или для дальнейшей проверки в полном объеме. *протокол добавления модели* позволяет отправить трехмерную модель с веб-сайта или приложения непосредственно в Windows Mixed Reality home, где они будут сохраняться как средства [запуска 3d-приложений](3d-app-launcher-design-guidance.md), 2d-приложения и голограммы. 

Например, если вы разрабатываете приложение, которое охватывает каталог трехмерной мебели для создания пространства, используйте *Протокол добавления модели* , чтобы разрешить пользователям размещать эти модели трехмерной мебели из каталога. После помещения в мир пользователи могут перемещать, изменять размер и удалять эти трехмерные модели так же, как и другие голограммы дома. В этой статье приводятся общие сведения о реализации *протокола добавления модели* для предоставления пользователям возможности оформления своего мира трехмерными объектами из приложения или из Интернета.

## <a name="device-support"></a>Поддержка устройств

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Компонент</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></td>
    </tr>
     <tr>
        <td>Добавление протокола модели</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="the-basics"></a>Основные сведения

включить размещение трехмерных моделей в Windows Mixed Reality home можно двумя шагами:
1. [убедитесь, что ваша трехмерная модель совместима с Windows Mixed Reality домашней](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Реализуйте *Протокол добавления модели* в приложении или на веб-странице (в этой статье).

## <a name="implementing-the-add-model-protocol"></a>Реализация *протокола добавления модели*

После создания [совместимой трехмерной модели](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)можно реализовать *Протокол добавления модели* , активируя следующий URI с любой веб-страницы или приложения:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Если URI указывает на удаленный ресурс, он будет автоматически скачан и помещен в домашнюю страницу. Локальные ресурсы будут скопированы в папку данных приложения для дома смешанной реальности перед размещением в домашней папке. мы рекомендуем разработать свой опыт для учета сценариев, в которых пользователь может запустить более раннюю версию Windows, которая не поддерживает эту функцию, скрывая кнопку или отключая ее по возможности. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>вызов *протокола добавления модели* из приложения универсальная платформа Windows:

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Вызов *протокола добавления модели* с веб-страницы:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Рекомендации для головных телефонов (VR)

* Для головных гарнитур (VR) на портале Mixed Reality не должно выполняться до вызова *протокола добавления модели*. В этом случае *Протокол добавления модели* запустит портал Mixed Reality и поместит объект непосредственно там, где будет смотреться гарнитура, когда вы поступите на главную страницу Mixed Reality. 
* При вызове *протокола добавления модели* с рабочего стола с уже запущенным порталом Mixed Reality убедитесь, что головной телефон находится в спящем режиме. В противном случае размещение не будет выполняться. 

## <a name="see-also"></a>См. также

* [создание трехмерных моделей для использования в Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Навигация по дому с технологией Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)