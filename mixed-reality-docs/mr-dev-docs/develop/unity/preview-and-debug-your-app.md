---
title: Предварительный просмотр и отладка приложения с помощью holographic, удаленного взаимодействия и режима воспроизведения
description: Используйте holographic для удаленного взаимодействия и режима воспроизведения для предварительного просмотра и отладки приложения
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: опенкср, unity, hololens, hololens 2, mixed reality, мртк, смешанная реальность набор средств, дополненная реальность, виртуальная реальность, гарнитуры смешанной реальности, обучение, учебник, начало работы, holographic удаленное взаимодействие, настольный, предварительный просмотр, отладка
ms.openlocfilehash: fe15d55037f09c47fe1e8a1dd996d0c69480f7b2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203860"
---
# <a name="preview-and-debug-your-app-using-holographic-remoting-and-play-mode"></a>Предварительный просмотр и отладка приложения с использованием удаленного взаимодействия и режима воспроизведения holographic

В этой статье описывается следующий вариант использования для удаленного взаимодействия с Holographic. 

- **Вы хотите выполнить предварительный просмотр и отладку приложения в процессе разработки**: вы можете запустить приложение локально в редакторе Unity на компьютере в режиме воспроизведения и передать его в HoloLens. Это позволяет быстро выполнить отладку приложения без создания и развертывания полного проекта. Мы вызываем приложение этого типа с помощью _предварительной версии "holographic Remoting" в режиме воспроизведения_. входные данные HoloLens--взгляда, жеста, голоса и пространственного сопоставления — отправляются на компьютер, где содержимое подготавливается к просмотру в виртуальном иммерсивное представление. Затем отображаемые кадры отправляются в HoloLens. 

Дополнительные сведения об удаленном взаимодействии с holographic см. в статье [Обзор удаленного взаимодействия](../platform-capabilities-and-apis/holographic-remoting-overview.md) с Holographic.

обратите внимание, что можно также использовать holographic удаленное взаимодействие, если [вы хотите, чтобы ресурсы пк могли](use-pc-resources.md) работать с приложением, а не полагаться на HoloLensные ресурсы.

## <a name="set-up-holographic-remoting"></a>Настройка удаленного взаимодействия с holographic

чтобы использовать удаленное взаимодействие с holographic, необходимо установить приложение с помощью [удаленного проигрывателя holographic](../platform-capabilities-and-apis/holographic-remoting-player.md) из Microsoft Store на HoloLens. Как описано ниже, после загрузки и запуска приложения вы увидите номер версии и IP-адрес для подключения. **Для работы с подключаемым модулем опенкср потребуется v 2.4 или более поздней версии**.

Для удаленного взаимодействия с holographic требуется быстрый ПК и Wi-Fiное подключение. Дополнительные сведения см. в статье, посвященной удаленному проигрывателю Holographic.

![Снимок экрана: проигрыватель holographic Remoting, работающий на HoloLens](images/openxr-features-img-01.png)

[!INCLUDE[](includes/unity-play-mode.md)]

## <a name="see-also"></a>См. также:
* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Учебник. Начало работы с PC holographic для удаленного взаимодействия](tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Учебник. Создание приложения для удаленного взаимодействия holographic](tutorials/mr-learning-pc-holographic-remoting-02.md)