---
title: Мост МРТК фигма для Unity
description: мост мртк фигма для unity позволяет перенести макет из фигма набор средств в Unity.
author: dongpark
ms.author: dongpark
ms.date: 03/29/2021
ms.topic: article
keywords: фигма, эскиз, Adobe XD, проектирование, конструктор, файл проекта, проектирование UX, HoloLens, мртк, смешанная реальность набор средств
ms.openlocfilehash: d21caa796907ebc7ea1fb46ce940cf210e9fc49d
ms.sourcegitcommit: 9431e9d6d7e959954ab3e18ecc0e420a3583d1a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/21/2021
ms.locfileid: "128053864"
---
# <a name="mrtk-figma-bridge-for-unity-beta"></a>Мост МРТК фигма для Unity (бета-версия)

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWKiO4]

мост мртк фигма для unity позволяет перенести макет из фигма набор средств в Unity. мост может импортировать макет пользовательского интерфейса, созданный с помощью мртк фигма набор средств, а затем создает соответствующий мртк prefabs с правильным положением и размером. Фигма Bridge поможет спроектировать процесс интеграции и совместную работу между дизайнерами и разработчиками.


сведения о фигма набор средств, который является файлом проекта с библиотекой пользовательского интерфейса для HoloLens 2, см. на странице [мртк фигма набор средств](figma-toolkit.md) .

## <a name="prerequisites"></a>Предварительные требования
- См. статью [Установка инструментов](/windows/mixed-reality/develop/install-the-tools) для необходимого программного обеспечения для разработки смешанной реальности.
- Unity 2019 или более поздней версии
- [МРТК-Unity 2.7.0 или более поздней версии](/windows/mixed-reality/mrtk-unity/)

> [!IMPORTANT]
> **Требуется MRTK-Unity 2.7.0 или более поздней версии**
> 
> так как фигма набор средств и фигма Bridge основаны на мртк 2.7.0 prefabs, требуется мртк 2.7.0 или более поздней версии. При использовании с более ранней версией МРТК некоторые компоненты не будут переведены должным образом.

## <a name="how-to-use-mrtk-figma-bridge"></a>Как использовать мост МРТК фигма

### <a name="1-installation"></a>1. Установка

Мост фигма Unity можно установить с помощью [инструмента для функций смешанной реальности](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool). Скачайте и запустите инструмент "функция смешанной реальности".

на странице **обнаружение компонентов** в разделе **смешанная реальность набор средств** выберите **мост мртк фигма Unity**. Выполните действия, чтобы завершить работу с компонентом MR Tool и вернуться к проекту Unity. Unity импортирует пакет для моста МРТК фигма.

### <a name="2-open-figma-bridge-window"></a>2. Открытие окна моста фигма

когда процесс импорта будет завершен, вы сможете найти мост фигма в меню **> смешанной реальности набор средств > моста фигма** .

<img src="images/FigmaToolkit/FigmaBridge_Menu.png" width="500px" alt="Figma Bridge - Menu"><br>

### <a name="3-generate-and-enter-your-figma-token"></a>3. Создайте и введите свой токен фигма.

На веб-сайте фигма щелкните меню фигма в левом верхнем углу, откройте справку и учетную запись > параметры учетной записи. Создайте новый личный маркер доступа в разделе "личные маркеры доступа".

<img src="images/FigmaToolkit/FigmaToolkit_Token.png" width="500px" alt="Figma Bridge - Get Token"><br>

<img src="images/FigmaToolkit/FigmaBridge_Token.png" width="500px" alt="Figma Bridge - Enter Token"><br>


### <a name="4-enter-id-for-a-figma-document"></a>4. Введите идентификатор для документа фигма
Каждый документ фигма имеет уникальный идентификатор в URL-адресе. Скопируйте и вставьте этот идентификатор в фигма Bridge.

<img src="images/FigmaToolkit/FigmaToolkit_DocID.png" alt="Figma Bridge - Doc ID"><br>

Щелкните **получить файл** , чтобы скачать файл фигма. Вы можете скачать другие файлы фигма, введя новый идентификатор.

Нажмите кнопку **загрузить файл** , чтобы открыть файл фигма.

<img src="images/FigmaToolkit/FigmaBridge_Files.png" width="500px" alt="Figma Bridge - Files"><br>

### <a name="5-build-a-page"></a>5. Создание страницы

Фигма Bridge отобразит список страниц в файле фигма. Проверьте страницы, которые требуется собрать в Unity. Нажмите кнопку **сборки страниц** .

<img src="images/FigmaToolkit/FigmaBridge_Pages.png" width="500px" alt="Figma Bridge - Pages"><br>

<img src="images/FigmaToolkit/FigmaBridge_Result.png" alt="Figma Bridge - Result"><br>

### <a name="6-refresh-a-document-for-changes"></a>6. обновление документа для внесения изменений

Вы можете изменить файл фигма в Интернете (или с помощью редактора настольных систем) и нажать кнопку **Обновить** , чтобы получить все изменения. Щелкните **сборки страницы** , чтобы выполнить сборку с обновлениями. Таким образом можно легко выполнить итерацию по проекту в фигма и увидеть его в Unity.



## <a name="see-also"></a>См. также раздел
* [Набор средств Figma](figma-toolkit.md)
* [Курсоры](cursors.md)
* [Телекинез](point-and-commit.md)
* [Кнопка](button.md)
* [Активный объект](interactable-object.md)
* [Ограничивающая рамка и панель приложения](app-bar-and-bounding-box.md)
* [Оперирование](direct-manipulation.md)
* [Меню руки](hand-menu.md)
* [Быстрое меню](near-menu.md)
* [Коллекция объектов](object-collection.md)
* [Голосовая команда](voice-input.md)
* [Клавиатура](keyboard.md)
* [Подсказка](tooltip.md)
* [Планшет](slate.md)
* [Ползунок](slider.md)
* [Шейдер](shader.md)
* [Биллбординг и закрепление элемента в пространстве](billboarding-and-tag-along.md)
* [Индикация хода выполнения](progress.md)
* [Притяжение к поверхности](surface-magnetism.md)
