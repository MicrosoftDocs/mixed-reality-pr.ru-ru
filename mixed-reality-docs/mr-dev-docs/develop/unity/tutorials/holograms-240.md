---
title: 240. HoloLens (1-го поколения). Совместный доступ — несколько устройств HoloLens
description: выполните приведенное ниже пошаговое руководство по программированию с помощью Unity, Visual Studio и HoloLens, чтобы получить сведения о голограммах общего доступа.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-unity, совместное использование, работа в сети, academy, учебник, HoloLens, academy "смешанная реальность", unity, гарнитура смешанной реальности, гарнитура windows Mixed reality, гарнитура виртуальной реальности, Windows 10
ms.openlocfilehash: 97dec324033b733944fe78eb0a5c268fe7d34928
ms.sourcegitcommit: bea83261bf9ce7a27a618e5bc54dc4d7711f5435
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2021
ms.locfileid: "130154666"
---
# <a name="hololens-1st-gen-sharing-240-multiple-hololens-devices"></a>HoloLens (1-й общий) общий доступ 240: несколько HoloLensных устройств

>[!IMPORTANT]
>учебники по смешанной реальности Academy были разработаны с учетом HoloLens (1-го поколения), Unity 2017 и впечатляющих головных телефонов смешанной реальности.  Поэтому мы считаем, что важно оставить эти руководства для разработчиков, которые ищут рекомендации по разработке для этих устройств. эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2 и могут быть несовместимы с более новыми версиями Unity.  Они будут сохранены для работы на поддерживаемых устройствах. Опубликован [новый цикл руководств](mrlearning-base.md) для HoloLens 2.

Голограммы получит присутствие в нашем мире, оставшееся на месте, по мере перемещения о пространстве. HoloLens сохраняет голограммы на месте, используя различные [системы координат](../../../design/coordinate-systems.md) для наблюдения за расположением и ориентацией объектов. При совместном использовании этих систем координат между устройствами мы можем создать общий интерфейс, который позволит нам принять участие в совместном мире Holographic.

В этом учебнике мы выполним следующее:

* Настройте сеть для совместной работы.
* делитесь голограммами на HoloLens устройствах.
* Знакомство с другими людьми в нашей общей жизни.
* Создайте общедоступную интерактивную среду, где вы можете ориентироваться на другие игроки и запустить снаряды.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td>240. Общий доступ в смешанной реальности: несколько устройств HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>Предварительные условия

* Windows 10 пк, для которого настроены правильные [средства, установленные](../../../develop/install-the-tools.md) с доступом к интернету.
* по крайней мере два HoloLens устройства, [настроенные для разработки](../../../develop/advanced-concepts/using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Файлы проекта

* Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) , необходимые для проекта. Требуется Unity 2017,2 или более поздней версии.
  * Если вам по-прежнему требуется поддержка Unity 5,6, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Если вам по-прежнему требуется поддержка Unity 5,5, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Если вам по-прежнему требуется поддержка Unity 5,4, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Отмена архивации файлов на Рабочий стол или другого места для удобства доступа. В качестве имени папки используйте **шаредхолограмс**.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он будет [доступен на GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Глава 1 — Холо World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

В этой главе мы создадим наш первый проект Unity и пошаговым процессом сборки и развертывания.

### <a name="objectives"></a>Задачи

* Настройте Unity для разработки holographic приложений.
* Ознакомьтесь с голограммой!

### <a name="instructions"></a>Instructions

* Запустите Unity.
* Выберите **Открыть**.
* Введите Location в качестве ранее неархивированной папки **шаредхолограмс** .
* выберите **Project имя** и щелкните **выбрать папку**.
* В **иерархии** щелкните правой кнопкой мыши **основную камеру** и выберите **Удалить**.
* В папке **холотулкит-Shared-240/Prefabs/Camera** найдите **главную камеру** prefab.
* Перетащите **основную камеру** в **иерархию**.
* В **иерархии** щелкните **создать** и **создать пустой**.
* Щелкните правой кнопкой мыши новый **GameObject** и выберите команду **Переименовать**.
* Переименуйте GameObject в **холограмколлектион**.
* Выберите объект **холограмколлектион** в **иерархии**.
* В **инспекторе** задайте для параметра **Расположение преобразования** значение: **X: 0, Y:-0,25, Z: 2**.
* в папке **Голограммы** на **панели Project** найдите ресурс **енергихуб** .
* перетащите объект **енергихуб** с **панели Project** в **иерархию** в качестве **дочернего элемента холограмколлектион**.
* Выберите **файл > сохранить сцену как...**
* Присвойте сцене имя **шаредхолограмс** и нажмите кнопку **сохранить**.
* Нажмите кнопку **воспроизвести** в Unity, чтобы просмотреть голограммы.
* Чтобы выйти из режима предварительного просмотра, нажмите кнопку **воспроизвести** еще раз.

**Экспорт проекта из Unity в Visual Studio**

* в Unity выберите **файл > сборка Параметры**.
* Щелкните **Добавить открытые сцены** , чтобы добавить сцену.
* выберите **универсальная платформа Windows** в списке **платформа** и щелкните **параметр платформа**.
* Задайте для **пакета SDK** значение **универсальное 10**.
* задайте для параметра **целевое устройство** значение **HoloLens** и для **типа сборки UWP** — **D3D**.
* Проверьте **проекты C# для Unity**.
* Щелкните **Построить**.
* В открывшемся окне проводника создайте **новую папку** с именем App.
* Щелкните папку **приложения** одним щелчком мыши.
* Нажмите кнопку **выбрать папку**.
* После завершения Unity появится окно проводника.
* Откройте папку **приложения** .
* Откройте **шаредхолограмс. sln** для запуска Visual Studio.
* с помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **X86**.
* Щелкните стрелку раскрывающегося списка рядом с пунктом локальный компьютер и выберите **удаленное устройство**.
    * Укажите в качестве **адреса** имя или IP-адрес HoloLens. если вы не знакомы с IP-адресом устройства, найдите **Параметры > сеть & интернет > дополнительные параметры** или запросите Кортана **"эй Кортана, что такое мой IP-адрес?".**
    * Оставьте для параметра **режим проверки подлинности** значение **универсальное**.
    * Нажмите кнопку **Выбрать**.
* Щелкните **отладка > начать без отладки** или нажмите клавиши **CTRL + F5**. При первом развертывании на устройстве необходимо [связать его с Visual Studio](../../../develop/advanced-concepts/using-visual-studio.md#pairing-your-device).
* помещайтесь на HoloLens и находите голограмму енергихуб.

## <a name="chapter-2---interaction"></a>Глава 2 — взаимодействие

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

В этой главе мы будем взаимодействовать с нашими голограммами. Сначала мы добавим курсор для визуализации нашего [взгляда](../../../design/gaze-and-commit.md). Затем мы добавим [жесты](../../../design/gaze-and-commit.md#composite-gestures) и будем использовать нашу руку, чтобы разместить наши голограммы в пространстве.

### <a name="objectives"></a>Задачи

* Для управления курсором используйте ввод с помощью указателя.
* Используйте ввод жестов для взаимодействия с голограммами.

### <a name="instructions"></a>Инструкции

**Взгляд**

* На **панели Иерархия** выберите объект **холограмколлектион** .
* На **панели инспектора** нажмите кнопку **Добавить компонент** .
* В меню введите в поле поиска пункт **Менеджер**. Выберите результат поиска.
* В папке **HoloToolkit-Sharing-240\Prefabs\Input** найдите ресурс **cursor** .
* Перетащите в **иерархию** ресурс с **курсором** .

**Жест**

* На **панели Иерархия** выберите объект **холограмколлектион** .
* Щелкните **Добавить компонент** и введите **Диспетчер жестов** в поле поиска. Выберите результат поиска.
* На **панели Иерархия** разверните узел **холограмколлектион**.
* Выберите дочерний объект **енергихуб** .
* На **панели инспектора** нажмите кнопку **Добавить компонент** .
* В меню введите текст в поле поиска с **голограммой**. Выберите результат поиска.
* Сохраните сцену, выбрав **файл > сохранить сцену**.

**Развертывание и наслаждайтесь**

* выполните сборку и развертывание в HoloLens, следуя инструкциям из предыдущей главы.
* когда приложение запустится на HoloLens, переместите заголовок и обратите внимание на то, как енергихуб соответствует вашему взгляду.
* Обратите внимание на то, что курсор отображается при взгляде на голограмму, и меняется на светло-точечный, когда не облаками на голограмме.
* Выполните касание, чтобы разместить голограмму. В настоящее время в нашем проекте можно разместить голограмму только один раз (повторное развертывание, чтобы повторить попытку).

## <a name="chapter-3---shared-coordinates"></a>Глава 3. Общие координаты

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

Приятно видеть голограммы и взаимодействовать с ними, но давайте дальше. Мы настроили наш первый общий интерфейс, который все может видеть одновременно.

### <a name="objectives"></a>Задачи

* Настройте сеть для совместной работы.
* Создание общей контрольной точки.
* Совместное использование систем координат на разных устройствах.
* Все видят одну голограмму!

>[!NOTE]
>Для подключения приложения к серверу общего доступа необходимо объявить возможности **интернетклиентсервер** и **приватенетворкклиентсервер** . это делается для вас, уже наГолограммы 240, но не забывайте об этом с учетом собственных проектов.

>1. в редакторе Unity перейдите к параметрам проигрывателя, перейдя в раздел "изменение > Project Параметры > player".
>2. щелкните вкладку "хранилище Windows".
>3. в разделе "возможности публикации Параметры >" проверьте возможность **интернетклиентсервер** и возможности **приватенетворкклиентсервер** .

### <a name="instructions"></a>Инструкции

* на **панели Project** перейдите в папку **HoloToolkit-Sharing-240\Prefabs\Sharing** .
* Перетащите prefab **доступа** на **панель Иерархия**.

Далее необходимо запустить службу общего доступа. Только **один компьютер** в общем интерфейсе должен выполнить этот шаг.

* В Unity — в меню верхнего уровня — выберите **меню холотулкит-Sharing-240**.
* В раскрывающемся списке выберите пункт **запустить службу общего доступа** .
* Проверьте параметр **частная сеть** и нажмите кнопку **Разрешить доступ** при появлении окна брандмауэра.
* Запишите IPv4-адрес, отображаемый в окне консоли службы общего доступа. Это тот же IP-адрес, что и у компьютера, на котором выполняется служба.

Следуйте остальным инструкциям на **всех ПК** , которые будут присоединяться к общему интерфейсу.

* В **иерархии** выберите объект **общего доступа** .
* В **инспекторе** в компоненте " **этап предоставления общего доступа** " измените **адрес сервера** с "localhost" на IPv4-адрес компьютера, на котором выполняется SharingService.exe.
* В **иерархии** выберите объект **холограмколлектион** .
* В **инспекторе** нажмите кнопку **Добавить компонент** .
* В поле поиска введите **Импорт экспорт привязки диспетчер**. Выберите результат поиска.
* на **панели Project** перейдите к папке **scripts** .
* Дважды щелкните скрипт **холограмплацемент** , чтобы открыть его в Visual Studio.
* Замените его содержимое кодом, приведенным ниже.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Вернитесь в Unity, выберите **холограмколлектион** на **панели Иерархия**.
* На **панели инспектора** нажмите кнопку **Добавить компонент** .
* В меню введите в поле поиска **диспетчер состояний приложения**. Выберите результат поиска.

**Развертывание и наслаждайтесь**

* постройте проект для HoloLens устройств.
* назначьте один HoloLens для первого развертывания. Необходимо подождать, пока привязка будет отправлена в службу, прежде чем можно будет поместить Енергихуб (это может занять около 30-60 секунд). Пока передача не будет выполнена, жесты касания будут игнорироваться.
* после размещения енергихуб его расположение загружается в службу, а затем можно выполнить развертывание на всех других HoloLens устройствах.
* когда новый HoloLens впервые присоединяется к сеансу, расположение енергихуб может быть неправильным на этом устройстве. Однако, как только расположения привязки и Енергихуб загружаются из службы, Енергихуб должен перейти к новому общему расположению. если это не происходит в течение ~ 30-60 секунд, изучите расположение исходной HoloLens при установке привязки для сбора дополнительных сведений о среде. Если расположение по-прежнему не блокируется, выполните повторное развертывание на устройстве.
* Когда устройства готовы и запускают приложение, найдите Енергихуб. Можно ли принять все согласие на расположение голограммы и направление текста?

## <a name="chapter-4---discovery"></a>Глава 4. Обнаружение

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Теперь все могут видеть одну голограмму! Теперь давайте посмотрим все, кто еще подключен к нашему миру. в этой главе мы будем перехватить расположение и поворот всех других HoloLens устройств в одном сеансе совместного доступа.

### <a name="objectives"></a>Задачи

* Найдите друг друга в нашем общем интерфейсе.
* Выберите и поделитесь с вами аватаром игрока.
* Вложите аватар игрока рядом с головами всех.

### <a name="instructions"></a>Instructions

* на **панели Project** перейдите к папке **Голограммы** .
* Перетащите **плайераватарсторе** в **иерархию**.
* на **панели Project** перейдите к папке **scripts** .
* Дважды щелкните скрипт **аватарселектор** , чтобы открыть его в Visual Studio.
* Замените его содержимое кодом, приведенным ниже.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* В **иерархии** выберите объект **холограмколлектион** .
* В **инспекторе** щелкните **Добавить компонент**.
* В поле поиска введите " **диспетчер локальных игроков**". Выберите результат поиска.
* В **иерархии** выберите объект **холограмколлектион** .
* В **инспекторе** щелкните **Добавить компонент**.
* В поле поиска введите **Remote Player Manager**. Выберите результат поиска.
* Откройте скрипт **холограмплацемент** в Visual Studio.
* Замените его содержимое кодом, приведенным ниже.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Откройте скрипт **аппстатеманажер** в Visual Studio.
* Замените его содержимое кодом, приведенным ниже.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**Развертывание и наслаждайтесь**

* выполните сборку и развертывание проекта на HoloLens устройствах.
* Когда вы слышите звуковой сигнал, найдите меню выбора аватара и выберите аватар с помощью жеста касания.
* если вы не просматриваете какие-либо голограммы, то при взаимодействии HoloLens со службой, световая точка вокруг курсора будет иметь другой цвет: инициализация (темно-фиолетовый), загрузка привязки (зеленый цвет), импорт/экспорт данных о расположении (желтый цвет), отправка привязки (синий). Если точкой вокруг курсора является цвет по умолчанию (светло-сиреневый), вы готовы к взаимодействию с другими игроками в вашем сеансе!
* Взгляните на других пользователей, подключенных к своему модулю. в этом случае у вас будет один и тот же робот, а затем копируя свои головные движения!

## <a name="chapter-5---placement"></a>Глава 5. размещение

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

В этой главе привязку можно разместить на реальных поверхностях. Мы будем использовать общие координаты для размещения этой привязки в средней точке между всеми, подключенными к общему интерфейсу.

### <a name="objectives"></a>Задачи

* Размещайте голограммы в сетке пространственных сопоставлений на основе головного расположения игроков.

### <a name="instructions"></a>Инструкции

* на **панели Project** перейдите к папке **Голограммы** .
* Перетащите **кустомспатиалмаппинг** prefab на **иерархию**.
* на **панели Project** перейдите к папке **scripts** .
* Дважды щелкните скрипт **аппстатеманажер** , чтобы открыть его в Visual Studio.
* Замените его содержимое кодом, приведенным ниже.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* на **панели Project** перейдите к папке **scripts** .
* Дважды щелкните скрипт **холограмплацемент** , чтобы открыть его в Visual Studio.
* Замените его содержимое кодом, приведенным ниже.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**Развертывание и наслаждайтесь**

* выполните сборку и развертывание проекта на HoloLens устройствах.
* Когда приложение будет готово, наведите на окружность и обратите внимание на то, как Енергихуб отображается в центре всех.
* Коснитесь, чтобы поместить Енергихуб.
* Попробуйте выполнить команду "Сброс целевого объекта", чтобы выбрать Енергихуб резервное копирование и совместная работа в качестве группы для перемещения голограммы в новое место.

## <a name="chapter-6---real-world-physics"></a>Глава 6-Real-Worldая физика

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

В этой главе мы добавим голограммы, которые возводят на реальные поверхности. Просматривайте свое пространство с помощью проектов, запущенных вами и вашими друзьями!

### <a name="objectives"></a>Задачи

* Запустите снаряды, который перевернут на реальные поверхности.
* Предоставьте общий доступ к снаряды, чтобы другие игроки могли видеть их.

### <a name="instructions"></a>Инструкции

* В **иерархии** выберите объект **холограмколлектион** .
* В **инспекторе** щелкните **Добавить компонент**.
* В поле поиска введите **Прожектиле Launcher**. Выберите результат поиска.

**Развертывание и наслаждайтесь**

* выполните сборку и развертывание на устройствах HoloLens.
* Когда приложение выполняется на всех устройствах, выполните воздушное касание, чтобы запустить прожектиле на реальных поверхностях.
* Узнайте, что происходит, когда прожектиле конфликтует с аватаром другого игрока!

## <a name="chapter-7---grand-finale"></a>Глава 7-Общий итог

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

В этой главе мы расскажем о портале, который может быть обнаружен только при совместной работе.

### <a name="objectives"></a>Задачи

* Совместное использование позволяет запустить достаточно снаряды на привязке, чтобы обнаружить секретный портал.

### <a name="instructions"></a>Instructions

* на **панели Project** перейдите к папке **Голограммы** .
* Перетащите **этот ресурс в качестве** **дочернего для холограмколлектион**.
* Выбрав **холограмколлектион** , нажмите кнопку **Добавить компонент** в **инспекторе**.
* В меню введите **експлодетаржет** в поле поиска. Выберите результат поиска.
* Выбрав **холограмколлектион** , из **иерархии** перетащите объект **енергихуб** в **целевое** поле в **инспекторе**.
* Выбрав **холограмколлектион** , из **иерархии** перетащите объект «незаполненный **мир** » в поле «незаполненный **мир** » в **инспекторе**.

**Развертывание и наслаждайтесь**

* выполните сборку и развертывание на устройствах HoloLens.
* После запуска приложения совместная работа для запуска снаряды на Енергихуб.
* Когда появится подсветка, запустите снаряды в подсвете роботов (нажмите робота три раза, чтобы получить дополнительные развлечения).