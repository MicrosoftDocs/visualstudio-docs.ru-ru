---
title: Приступая к работе с инструментами Visual Studio для Unity | Документы Майкрософт
description: Узнайте, как установить и настроить Visual Studio для разработки Unity.
ms.date: 01/27/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 706700c8343d934f7a9a5ce32f98bf96e67d4259
ms.sourcegitcommit: 07e6db4bf2966863093e3974c60c3b46e6953416
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2021
ms.locfileid: "112488849"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Начало работы с Visual Studio и Unity

> [!NOTE]
> В этом учебнике предполагается, что Unity уже установлен с помощью программы концентратора Unity. Если вы не знакомы с Unity, мы рекомендуем ознакомиться с Unity и сначала заполним [путь обучения Unity Essentials](https://learn.unity.com/pathway/unity-essentials) .

## <a name="install-unity-support-for-visual-studio"></a>Установка поддержки Unity для Visual Studio

Инструменты Visual Studio для Unity — это бесплатное расширение, которое обеспечивает поддержку написания и отладки C# и многое другое. Полный список включенных расширений см. в [обзоре средств для Unity](./visual-studio-tools-for-unity.md) .

:::zone pivot="windows"

> [!NOTE]
> Это руководства по установке для Visual Studio. Если вы используете Visual Studio Code, ознакомьтесь [с документацией по разработке Unity с VS Code](https://code.visualstudio.com/docs/other/unity).

1. [Скачайте установщик Visual Studio](/visualstudio/install/install-visual-studio.md)или запустите его, если он уже установлен.
2. Щелкните **Изменить** (если установлено) или **Установка** (для новой установки) для требуемой версии Visual Studio.
3. На вкладке **рабочие нагрузки** перейдите к разделу **игры** и выберите рабочую нагрузку **Разработка игр с помощью Unity** .

    ![Поле "Разработка игр с рабочей нагрузкой Unity" в установщике](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Это руководства по установке предназначено для Visual Studio для Mac. Если вы используете Visual Studio Code, ознакомьтесь [с документацией по разработке Unity с VS Code](https://code.visualstudio.com/docs/other/unity).

Средства для Unity включены в установку Visual Studio для Mac и отдельные шаги по установке не требуются. Это можно проверить в меню **Visual Studio для Mac > extensions > Game Development** . **Средства Visual Studio для Mac для Unity** должны быть включены.

![Представление "Диспетчер расширений" с включенными инструментами Visual Studio для Mac для Unity](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Проверка обновлений

Рекомендуется поддерживать обновление Visual Studio и Visual Studio для Mac, чтобы получить последние исправления ошибок, функции и поддержку Unity. Для этого не требуется обновление версий Unity.

:::zone pivot="windows"

1. Откройте меню **Help > проверить наличие обновлений** .

    ![Меню Проверка обновлений в Visual Studio 2019](../media/vs/check-for-updates.png)

2. Если доступно обновление, Visual Studio Installer отобразит новую версию. Нажмите кнопку **Обновить**.

:::zone-end
:::zone pivot="macos"

1. Щелкните **Visual Studio для Mac > проверить обновления...** , чтобы открыть диалоговое окно **обновления Visual Studio** .
2. Если доступно обновление, нажмите кнопку **установить** .

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Настройка Unity для использования Visual Studio

По умолчанию Unity уже должен быть настроен на использование Visual Studio или Visual Studio для Mac в качестве редактора скриптов. Вы можете подтвердить это или изменить внешний редактор скриптов на определенную версию Visual Studio в редакторе Unity.

:::zone pivot="windows"

1. В редакторе Unity выберите меню **изменить > предпочтения** .
2. Выберите вкладку **Внешние инструменты** слева.
3. Раскрывающийся список **внешний редактор скриптов** позволяет выбрать различные установки Visual Studio. Можно также нажать кнопку **Обзор...** в раскрывающемся списке, чтобы добавить неограниченную версию.

    ![Меню настроек внешних средств в редакторе Unity в Windows](../media/vs/preferences-external-tools.png)

4. Если было выбрано **Обзор...** , необходимо перейти в каталог **Common7/IDE**, находящийся в каталоге установки Visual Studio, и выбрать файл **devenv.exe**. Затем нажмите кнопку **Открыть**.
5. После выбора Visual Studio из списка **внешнего редактора скриптов**, убедитесь, что флажок **Editor Attaching** (Присоединение редактора) установлен.
6. Чтобы завершить процесс настройки, закройте диалоговое окно **Параметры**.

:::zone-end
:::zone pivot="macos"

1. В редакторе Unity выберите меню **параметров > Unity** .
2. Выберите вкладку **Внешние инструменты** слева.
3. Раскрывающийся список **внешний редактор скриптов** позволяет выбрать различные установки Visual Studio. Можно также нажать кнопку **Обзор...** в раскрывающемся списке, чтобы добавить неограниченную версию.

    ![Меню настроек внешних средств в редакторе Unity на macOS](../media/vsm/preferences-external-tools.png)

4. Чтобы завершить процесс настройки, закройте диалоговое окно **Параметры**.

:::zone-end

## <a name="next-steps"></a>Дальнейшие шаги

 Чтобы узнать, как работать с проектом Unity и выполнить его отладку в Visual Studio, перейдите по адресу [инструменты Visual Studio для Unity](using-visual-studio-tools-for-unity.md).
