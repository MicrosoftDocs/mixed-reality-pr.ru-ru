---
title: Журнал версий службы удаленного взаимодействия с holographic
description: Оставайтесь в курсе изменений в журнале версий функции удаленного взаимодействия holographic для HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, удаленное взаимодействие, holographic удаленное взаимодействие, журнал версий, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности
ms.openlocfilehash: 8fa1671657a7cb057f88da24fe4cfe68b0401397
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496042"
---
# <a name="holographic-remoting-version-history"></a>Журнал версий службы удаленного взаимодействия с holographic

> [!IMPORTANT]
> Это руководство относится к удаленному взаимодействию с HoloLens 2.

## <a name="version-250-february-12-2021"></a>Версия 2.5.0 (12 февраля, 2021) <a name="v2.5.0"></a>
* Holographic удаленное взаимодействие с помощью [API опенкср](../native/openxr.md) теперь поддерживает:
  * Расширение XR_MSFT_spatial_anchor. Это расширение позволяет приложению создавать пространственные привязки, которые являются произвольными точками свободного места в физической среде пользователя, которые будут записаны средой выполнения.
  * Расширение XR_MSFT_controller_model. Это расширение предоставляет механизм для загрузки моделей ГЛТФ для контроллеров.
  * Пользовательские каналы данных как часть расширения XR_MSFT_holographic_remoting. Пример для этого показан в [опенкср Remote Sample](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).
* Улучшенная синхронизация между проигрывателем и удаленной стороной. Это позволяет динамически изменять буферы объектов и буферизации, что обеспечивает непрерывное отображение удаленного отображения содержимого при ожидаемой частоте целевых кадров.
* Улучшена производительность плеера holographic Remoting, доступного через Microsoft Store. В HoloLens 2 игрок теперь работает в 60 кадрах в секунду.
* Оптимизированная передача сеток пространственных поверхностей, которые можно запрашивать через [спатиалсурфацеобсервер](https://docs.microsoft.com/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) в удаленном приложении.
* Исправлена проблема, при которой вызов методов Спатиаланчорманажер или освобождение привязок вызывали исключения при отключении.
* Исправлена проблема с потоками, приводящая к сбоям при закрытии экземпляров Плайерконтекст или Ремотеконтекст.
* Множество других исправлений и улучшений стабильности.

## <a name="version-241-january-22-2021"></a>Версия 2.4.1 (22 января, 2021) <a name="v2.4.1"></a>

* Исправлена проблема с Спатиаланчорманажер:: Рекуестстореасинк не работает надежно при вызове во время соединения.
* Исправлена проблема с Спатиаланчорманажер:: Трисаве неправильное сохранение привязки, если привязка в вопросе не размещаемые.

## <a name="version-240-december-1-2020"></a>Версия 2.4.0 (1 декабря 2020 г.) <a name="v2.4.0"></a>

* Holographic удаленное взаимодействие теперь поддерживает запись удаленных приложений с помощью [API опенкср](../native/openxr.md). Чтобы приступить к работе, ознакомьтесь с [написанием удаленного приложения holographic с использованием API-интерфейсов опенкср](holographic-remoting-create-remote-openxr.md) .
* Исправления ошибок и стабильность.

## <a name="version-231-october-10-2020"></a>Версия 2.3.1 (10 октября, 2020) <a name="v2.3.1"></a>

* Исправлена регрессия с удаленным прогнозированием, что привело к ухудшению визуального элемента.
* Реализован Перцептиондевицесеткреатефакторйоверриде, который гарантирует, что PerceptionDevice.dll, поставляемые с holographic, не мешают работе с версией, поставляемой с Windows 10.

## <a name="version-230-october-2-2020"></a>Версия 2.3.0 (2 октября, 2020) <a name="v2.3.0"></a>

* Исправлены сбои, которые могут произойти, когда приостанавливается работающий плеер Holographic.
* Улучшение стабильности.

## <a name="version-223-august-28-2020"></a>Версия 2.2.3 (28 августа 2020) <a name="v2.2.3"></a>

* Исправления ошибок и стабильность.

## <a name="version-222-july-10-2020"></a>Версия 2.2.2 (10 июля, 2020) <a name="v2.2.2"></a>

* Исправлена проблема с [холографиккамера. лефтвиевпортпараметерс](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) и [холографиккамера. ригхтвиевпортпараметерс](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) не возвращает никаких скрытых вершин сетки областей при потоковой передаче с головного телефона Windows Mixed Reality.
* Исправлена проблема, которая может произойти при плохом сетевом подключении.

## <a name="version-221-july-6-2020"></a>Версия 2.2.1 (6 июля, 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> Проверка [комплекта сертификации приложений Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) с версией [2.2.0](holographic-remoting-version-history.md#v2.2.0) завершится ошибкой. Если вы используете версию [2.2.0](holographic-remoting-version-history.md#v2.2.0) и хотите отправить приложение в аренду Microsoft Store p с обновлением по меньшей мере до версии 2.2.1.
* Исправлены проблемы соответствия [комплекта сертификации приложений для Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) .

## <a name="version-220-july-1-2020"></a>Версия 2.2.0 (1 июля 2020 г.) <a name="v2.2.0"></a>

* Проигрыватель holographic Remoting теперь можно установить на ПК под управлением [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md), что позволяет выполнять потоковую передачу на впечатляющие гарнитуры.
* [Контроллеры Motion](../../design/motion-controllers.md) теперь поддерживаются с помощью удаленного взаимодействия, а данные, зависящие от контроллера, можно получить через [спатиалинтерактионсаурце. Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller).
* [Спатиалстажефрамеофреференце](/uwp/api/windows.perception.spatial.spatialstageframeofreference) теперь поддерживается, и текущий этап можно получить с помощью [спатиалстажефрамеофреференце. Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current). Кроме того, можно запросить новый этап с помощью [спатиалстажефрамеофреференце. рекуестневстажеасинк](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync).
* В предыдущих версиях прогнозирование на стороне игрока было обработано проигрывателем holographic Remoting. Начиная с версии 2.2.0, holographic удаленное взаимодействие имеет синхронизацию времени, а прогноз полностью выполняется удаленным приложением. Кроме того, в случае сложных сетевых ситуаций пользователи должны были повысить стабильность работы.

## <a name="version-213-may-25-2020"></a>Версия 2.1.3 (25 мая, 2020) <a name="v2.1.3"></a>

* Изменено поведение события [холографикспаце. камерааддед](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) . В предыдущих версиях **не** было гарантировано, что добавленный [холографиккамера](/uwp/api/windows.graphics.holographic.holographiccamera) также имеет допустимый [холографиккамерапосе](/uwp/api/windows.graphics.holographic.holographiccamerapose) при создании следующего кадра через [холографикспаце. креатенекстфраме](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe). Начиная с версии 2.1.3, [холографикспаце. камерааддед](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) синхронизируется с данными, поступающими от удаленного плеера Holographic. Пользователи могут рассчитывать на то, что при добавлении камеры в следующем кадре также доступен допустимый [холографиккамерапосе](/uwp/api/windows.graphics.holographic.holographiccamerapose) для этой камеры.
* Добавлена **отключенная** в депсбуфферстреамресолутион, которую можно использовать для отключения потоковой передачи буфера глубины через RemoteContext.Configуредепсвидеостреам. Обратите внимание, что при использовании [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) завершится с ошибкой *E_ILLEGAL_METHOD_CALL*.
* Экран запуска удаленного проигрывателя holographic был переработан и теперь не блокирует представление пользователей.
* Улучшения стабильности и исправления ошибок.

## <a name="version-212-april-5-2020"></a>Версия 2.1.2 (5 апреля, 2020) <a name="v2.1.2"></a>

* Исправлена проблема совместимости аудио обратной связи между последним удаленным проигрывателем удаленного взаимодействия и удаленных приложений с использованием версии меньше 2.1.0.
* Исправлена ошибка пространственной привязки, которая неожиданно закрыла удаленный плеер Holographic. Эта проблема также затрагивает пользовательские проигрыватели.

## <a name="version-211-march-20-2020"></a>Версия: (20 марта, 2020) <a name="v2.1.1"></a>

* Исправлена проблема кодирования видео с удаленными приложениями при использовании GPU AMD.
* Улучшена производительность удаленного проигрывателя Holographic.

## <a name="version-210-march-11-2020"></a>Версия 2.1.0 (11 марта, 2020) <a name="v2.1.0"></a>

* Сетевой транспорт переключился на использование [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) через UDP. Безопасные подключения используют [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) сейчас. Обратите внимание, что [проигрыватель holographic Remoting](holographic-remoting-player.md) по-прежнему совместим со всеми ранее выпущенными версиями с удаленным взаимодействием. Чтобы воспользоваться преимуществами нового сетевого транспорта и, по вашему мнению, проигрыватель holographic Remoting и удаленное приложение должны использовать версию 2.1.0.
* Добавлена поддержка [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Версия 2.0.20 (2 февраля 2020 г.) <a name="v2.0.20"></a>

* Исправлены различные ошибки, приводящие к сбоям.

## <a name="version-2018-december-17-2019"></a>Версия 2.0.18 (17 декабря, 2019) <a name="v2.0.18"></a>

* Добавлена поддержка [холографиквиевконфигуратион](/uwp/api/windows.graphics.holographic.holographicviewconfiguration) .
* Исправлены различные ошибки, приводящие к сбоям.
* Исправлена ошибка обратного вызова Холографикспаце. Камерааддед, чтобы Холографиккамера был принят и показана как добавленная Камера в Холографикфраме.

## <a name="version-2016-november-11-2019"></a>Версия 2.0.16 (11 ноября, 2019) <a name="2.0.16"></a>

* Исправлена взаимоблокировка при отслеживании QR-кода.
* Исправлено исключение унханделед из-за блокировки ожидания в основном потоке.

## <a name="version-2014-october-26-2019"></a>Версия 2.0.14 (26 октября, 2019) <a name="v2.0.14"></a>

* Поддержка новых API Перцептиондевице (обновление Windows 10 за ноябрь 2019).
* Исправлена проблема, препятствующая срабатыванию событий жестов с помощью Спатиалжестуререкогнизер.
* Исправлена проблема с потоками при использовании Спатиалсурфацеобсервер. Сетбаундингволуме.

## <a name="version-2012-october-18-2019"></a>Версия 2.0.12 (18 октября, 2019) <a name="v2.0.12"></a>

* Исправлена проблема сбоя в Спатиалжестуререкогнизер при использовании Навигатионраил (X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Версия 2.0.10 (10 октября, 2019) <a name="v2.0.10"></a>

* Исправлена аварийное завершение работы при использовании кнопки триггера контроллеров VR. Holographic удаленное взаимодействие не полностью поддерживает контроллеры, только кнопка "триггер" и кнопка Windows работают при связывании с HoloLens 2.

## <a name="version-209-september-19-2019"></a>Версия 2.0.9 (19 сентября 2019 г.) <a name="v2.0.9"></a>

* Добавлена поддержка [спатиаланчорекспортер](/uwp/api/windows.perception.spatial.spatialanchorexporter) .
* Добавлен новый интерфейс ```IPlayerContext2``` (реализованный ```PlayerContext``` ), предоставляющий следующие члены:
  - Свойство [блитремотефраметимеаут](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* Добавлено ```Failed_RemoteFrameTooOld``` значение в ```BlitResult```
* Улучшения стабильности и надежности

## <a name="version-208-august-20-2019"></a>Версия 2.0.8 (20 августа 2019 г.) <a name="v2.0.8"></a>

* Исправлена сбой при вызове [холографиккамерарендерингпараметерс. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) с параметром [IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) в качестве параметра.
* Улучшения стабильности и надежности

## <a name="version-207-july-26-2019"></a>Версия 2.0.7 (26 июля, 2019) <a name="v2.0.7"></a>

* Первый общедоступный выпуск holographic Remoting для HoloLens 2.

## <a name="see-also"></a>См. также:

* [Создание удаленного приложения holographic с удаленным взаимодействием с помощью API-интерфейсов Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Создание удаленного приложения holographic с удаленным взаимодействием с помощью API-интерфейсов Опенкср](holographic-remoting-create-remote-openxr.md)
* [Создание пользовательского проигрывателя для голографического удаленного взаимодействия](holographic-remoting-create-player.md)
* [Устранение неполадок и ограничения удаленного взаимодействия с holographic](holographic-remoting-troubleshooting.md)
* [Условия лицензии на использование ПО для голографического удаленного взаимодействия](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Заявление Майкрософт о конфиденциальности](https://go.microsoft.com/fwlink/?LinkId=521839)