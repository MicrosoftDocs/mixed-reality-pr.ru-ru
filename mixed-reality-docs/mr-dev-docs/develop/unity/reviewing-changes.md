---
title: Авторизация изменений в проекте
description: Узнайте, как авторизовать изменения в проекте с помощью Mixed Reality Feature Tool при разработке решений для HoloLens и виртуальной реальности.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: актуальность, инструменты, начало работы, основы, Unity, Visual Studio, набор средств, гарнитура смешанной реальности, гарнитура Windows Mixed Reality, гарнитура виртуальной реальности, установка, Windows, HoloLens, эмулятор, Unreal, OpenXR
ms.openlocfilehash: db7ae079e19c7739f57f0b9e4a375a3e6f9a3cdd
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230788"
---
# <a name="authorizing-project-changes"></a>Авторизация изменений в проекте

Перед внесением изменений в проект Unity необходимо проверить и утвердить все изменения в файлах манифеста и проекта.

![Запрос на авторизацию](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a>манифеста

Предложенные изменения манифеста можно просмотреть в столбце **Manifest** (Манифест) слева. Его содержимое будет в точности записано в манифест проекта (**Packages/manifest.json**):

![Предварительный просмотр манифеста](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a>Файлы, которые будут скопированы в проект

В разделе **Files to be copied into the project** (Файлы, которые будут скопированы в проект) справа представлен список конкретных файлов пакетов функций, которые будут скопированы в проект Unity:

![Предварительный просмотр манифеста и файлов, которые будут скопированы](images/FilesToCopy.png)

## <a name="compare-manifests"></a>Сравнение манифестов

Вы можете сравнить версии всех предлагаемых изменений, выбрав **Compare** (Сравнить).

![Сравнение манифестов](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a>Утверждение изменений

Когда вы утвердите предложенные изменения, включенные в список файлы будут скопированы в проект Unity, а в манифест будут добавлены ссылки на эти файлы.

> [!NOTE]
> Файлы пакетов функций (*.tgz) нужно добавить в систему управления версиями. Ссылки на них указываются в формате относительного пути, что позволяет группам разработчиков легко предоставлять общий доступ к изменениям функций и манифестов.

 В процессе изменений будет создана резервная копия текущего файла **manifest.json**.

> [!IMPORTANT]
> В списке резервных копий манифеста самая старая всегда имеет имя **manifest.json.backup**. Более новые резервные копии дополняются числовыми значениями, начиная с нуля (0).

## <a name="going-back-to-the-previous-step"></a>Переход к предыдущему шагу

Если вам нужно изменить выбранные функции, выберите **Go Back** (Назад), чтобы вернуться к шагу [Import](importing-features.md) (Импорт).

## <a name="see-also"></a>См. также

- [Вас приветствует Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)
- [Импорт выбранных пакетов](importing-features.md)
