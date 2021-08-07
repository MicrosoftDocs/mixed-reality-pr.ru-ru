---
title: Использование Вебкср с Windows Mixed Reality
description: изучите основы использования и разработки для приложений вебкср, работающих на Windows Mixed Reality впечатляющих гарнитурах.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: вебкср, винмр, вебар, вебвр, виндовсмикседреалити, HoloLens, windows mixed reality, веб-vr, web xr, web mr, web ar, 360, 360 video, 360 видео, 360 photo, 360 фотографии, 360 content, иммерсивное веб-, иммерсивевеб, IW
ms.openlocfilehash: e670135cb00db26082b73f8465390a686de6a3e946bbffa561f9df90085970f8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216270"
---
# <a name="webxr-overview"></a>Обзор Вебкср

## <a name="javascript-development"></a>Разработка на JavaScript

JavaScript — один из самых популярных языков программирования в мире! Это просто, упрощенное и широко используемое в Интернете. Используйте возможности JavaScript и веб-навыков для создания более привлекательных возможностей смешанной реальности.

## <a name="mixed-reality-applications-on-the-web"></a>Приложения смешанной реальности в Интернете

Функции смешанной реальности доступны в Интернете с помощью [вебкср](webxr-overview.md). Содержимое Virtual Reality (VR) и Расширенная реальность (AR) можно просматривать в совместимом браузере с поддержкой Вебкср без установки дополнительного программного обеспечения или подключаемых модулей. Вы можете использовать тот же браузер с физическим устройством, например HoloLens 2.

[**API устройства вебкср**](https://www.w3.org/TR/webxr/) предназначен для доступа к устройствам **Virtual Reality (VR)** и **дополненным (AR)** , включая **датчики** и **подключенные к головным выдисплеям** в **Интернете**. API устройства вебкср в настоящее время доступен на Microsoft Edge и Chrome версии 79 и более поздних версий по умолчанию поддерживает вебкср. Последнюю версию поддержки браузера для Вебкср можно узнать по адресу [caniuse.com](https://caniuse.com/#search=webxr).

> [!NOTE]
> **Вебвр** является устаревшим и недоступен в текущих браузерах, поэтому его не следует использовать для новых разработок. Все существующие реализации **вебвр** необходимо перенести вперед в **вебкср**.

### <a name="viewing-webxr"></a>Просмотр Вебкср

вы можете просматривать вебкср експеринцес на [Windows Mixed Reality, а также новые Microsoft Edge](../../whats-new/new-microsoft-edge.md) и [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).
Чтобы проверить, поддерживает ли ваш браузер Вебкср, перейдите к [примерам вебкср](https://immersive-web.github.io/webxr-samples/) в браузере.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>Что можно использовать для разработки впечатляющих веб-приложений?

В следующем списке показаны платформы и API-интерфейсы JavaScript для создания впечатляющих функций, которые в настоящее время являются лидерами рынка и широко приняты и приняты разработчиками JavaScript со смешанной реальности:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Бабилон — это трехмерный модуль JavaScript, который упрощает разработку трехмерного содержимого и впечатляющих приложений. Прежде чем приступить к работе с иммерсивное приложение, рекомендуется изучить основы разработки Babylon.js.<br/><br/>Узнайте, как создавать трехмерные приложения с помощью babylon.js [Приступая к работе](https://doc.babylonjs.com/start).<br/>-Играть с трехмерными примерами и их исходным кодом с помощью babylon.js [Playground](https://doc.babylonjs.com/examples/)<br/>Подробное углубление в [вебкср](https://doc.babylonjs.com/divingDeeper/webXR)<br/>Узнайте, как приступить к работе с нашими учебниками [Создание первого приложения "Hello World!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Логотип Бабилонжс](images/babylon.js.example.png) |
|[**A-кадр**](https://aframe.io/) <br/><br/>A-Frame — это декларативная платформа JavaScript, позволяющая начать работу с Virtual Reality в Интернете. Ознакомьтесь с [документацией по кадрам,](https://aframe.io/docs/1.2.0/introduction/) чтобы узнать больше. |![A-кадр](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js — популярная трехмерная библиотека для создания впечатляющих возможностей. Дополнительные сведения о [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) на странице документации и о [примерах](https://threejs.org/examples/#webgl_animation_cloth)см. здесь. |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Доступ к API устройства Вебкср можно получить непосредственно с помощью API-интерфейсов WebGL. WebGL (Библиотека веб-графики) — это API JavaScript для визуализации высокопроизводительной интерактивной трехмерной и двухмерной графики в любом совместимом веб-браузере без использования подключаемых модулей. |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>См. также:

* [Обзор Вебкср](webxr-overview.md)
* [Спецификация API устройства Вебкср](https://immersive-web.github.io/webxr/)
* [Документация по API устройства Вебкср](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Примеры Вебкср](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Использование Babylon.js для создания Вебксрных возможностей](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* Расширения [API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) и [игровой](https://w3c.github.io/gamepad/extensions.html) планшета
* [Windows Mixed Reality и новый Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [Обработка потерянного контекста в WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [поинтерлокк](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Группа иммерсивного веб-сообщества](https://www.w3.org/community/immersive-web/)
* [Иммерсивное веб-сайт W3C GitHub](https://github.com/immersive-web)