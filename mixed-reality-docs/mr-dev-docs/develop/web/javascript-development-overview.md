---
title: Общие сведения о разработке JavaScript
description: Общие сведения о разработке смешанной реальности с использованием JavaScript для веб-, мобильных и высококачественных головных телефонов Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript, Вебкср, Винмр, Вебар, Вебвр, Виндовсмикседреалити, HoloLens, Windows Mixed Reality, веб-VR, Web XR, Web MR, Web AR, 360, 360 Video, 360 видео, 360 Photo, 360 фотографии, 360 Content, иммерсивное Интернет, иммерсивное веб-сайт, IW, иммерсивевеб
ms.openlocfilehash: 573db6f739292b7e67148d260a5ba1880d24fb20
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580324"
---
# <a name="javascript-development-overview"></a>Обзор разработки в JavaScript

## <a name="mixed-reality-applications-on-the-web"></a>Приложения смешанной реальности в Интернете

Функции смешанной реальности доступны в Интернете с помощью [API-интерфейсов устройств вебкср](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) и [устаревших API вебвр](webxr-overview.md). Для браузеров, которые не поддерживают полные функции Вебкср, можно добавить [вебксрные заливки](https://github.com/immersive-web/webxr-polyfill) на веб-сайт.

## <a name="what-is-webxr-polyfill"></a>Что такое Вебксрная Заливка

Реализация API устройства Вебкср на JavaScript, а также модуль игровой планшет Вебкср. Эта Заливка позволяет разработчикам писать в соответствии с последней спецификацией, предоставляя поддержку при запуске в браузерах, которые реализуют спецификацию Вебвр 1,1, или на мобильных устройствах без поддержки Вебвр/Вебкср.

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a>Библиотеки JavaScript для создания приложений смешанной реальности в Интернете

## <a name="babylonjs"></a>Babylon.js

Бабилон — это трехмерный модуль JavaScript, который упрощает разработку трехмерного содержимого и впечатляющих приложений. Прежде чем приступить к работе с иммерсивное приложение, рекомендуется изучить основы разработки Babylon.js.

Узнайте, как создать приложение смешанной реальности с помощью Бабилон в [разделе Приступая к работе](https://doc.babylonjs.com/). Воспроизводите трехмерные примеры и их исходный код с помощью [Бабилон Playground](https://doc.babylonjs.com/examples/). Познакомьтесь с разработкой смешанной реальности в [разделе вебкср](https://doc.babylonjs.com/how_to/introduction_to_webxr) документации. 

## <a name="a-frame"></a>A-кадр

A-Frame — это декларативная платформа JavaScript, позволяющая начать работу с Virtual Reality в Интернете. Ознакомьтесь с [документацией по кадрам,](https://aframe.io/) чтобы узнать больше.

## <a name="threejs"></a>Three.js

Three.js — популярная трехмерная библиотека для создания впечатляющих возможностей. Дополнительные сведения о [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) на странице документации и о [примерах](https://threejs.org/examples/#webgl_animation_cloth)см. здесь.

## <a name="webgl"></a>WebGL

Доступ к API устройства Вебкср можно получить непосредственно с помощью API-интерфейсов WebGL. WebGL (Библиотека веб-графики) — это API JavaScript для визуализации высокопроизводительной интерактивной трехмерной и двухмерной графики в любом совместимом веб-браузере без использования подключаемых модулей. Дополнительные сведения об [API-интерфейсах WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a>Собственные мобильные приложения смешанной реальности с использованием JavaScript

С помощью нескольких библиотек JavaScript вы можете писать свои возможности смешанной реальности и развертывать их в Интернете и на собственных платформах, таких как гарнитуры Windows Mixed Reality, устройства Android и iOS.

## <a name="babylon-native"></a>Бабилон Native

[Бабилон собственная](https://www.babylonjs.com/native/) платформа позволяет любому пользователю получить свой код Babylon.js и создать собственное приложение с ним, разблокируя возможности собственных технологий. Вы можете скачать [Бабилон Native на сайте GitHub](https://github.com/BabylonJS/BabylonNative) и узнать больше о нем в [Babylon.js блоге](https://medium.com/@babylonjs/babylon-native-821f1694fffc).

## <a name="react-native"></a>React Native

[Реакция на машинный код](https://reactnative.dev/) — это еще одна библиотека с открытым исходным кодом, которая позволяет разработчикам создавать с помощью JavaScript и развертывать на нескольких платформах Вы можете скачать [собственное реагирование на GitHub](https://github.com/facebook/react-native) и узнать больше о нем в блоге, посвященном [собственному реагированию](https://reactnative.dev/blog/).

## <a name="see-also"></a>См. также:

* [Обзор Вебкср](webxr-overview.md)
* [Спецификация API устройства Вебкср](https://immersive-web.github.io/webxr/)
* [Документация по API устройства Вебкср](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Иммерсивевеб. dev](https://immersiveweb.dev/)
* [Примеры Вебкср](https://immersive-web.github.io/webxr-samples/)
* [Использование Babylon.js для создания Вебксрных возможностей](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality и новая Microsoft ребро](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [Иммерсивное веб-сайт W3C GitHub](https://github.com/immersive-web)
* [API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* Расширения [API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) и [игровой](https://w3c.github.io/gamepad/extensions.html) планшета
* [Обзор Вебвр](webvr-overview.md)