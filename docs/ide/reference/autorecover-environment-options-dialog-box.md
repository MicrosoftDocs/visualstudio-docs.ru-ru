---
title: Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"
description: Сведения о диалоговом окне "Параметры" в разделе "Среда" на странице "Автовосстановление" и о том, как использовать его для настройки автоматического резервного копирования файлов.
ms.custom: SEO-VS-2020
ms.date: 08/14/2020
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 007e82ee7c1c2839ba266794432605f1f92a1669
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307795"
---
# <a name="autorecover-environment-options-dialog-box"></a>Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"

Эта страница диалогового окна **Параметры** служит для настройки автоматического резервного копирования файлов. Можно указать необходимость восстановления измененных файлов в случае неожиданного завершения работы Visual Studio.

Чтобы открыть это диалоговое окно, последовательно выберите в меню пункты **Инструменты** > **Параметры** > **Среда** > **Автовосстановление**.

:::image type="content" source="media/autorecover-options.png" alt-text="Снимок экрана: раздел &quot;Автовосстановление&quot; в диалоговом окне &quot;Параметры&quot;":::

**Сохранять данные автовосстановления каждые [n] мин**

::: moniker range=">=vs-2022"

Используйте этот параметр, чтобы настроить периодичность автоматического сохранения файла в редакторе. Что касается ранее сохраненных файлов, Visual Studio сохраняет копию файла в папке ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles\\[projectname]***. Если этот файл новый и еще не был сохранен, Visual Studio автоматически сохраняет его, используя случайно созданное имя файла.

::: moniker-end

::: moniker range="vs-2019"

Используйте этот параметр, чтобы настроить периодичность автоматического сохранения файла в редакторе. Что касается ранее сохраненных файлов, Visual Studio 2019 версии 16.2 и более поздних версий сохраняет копию файла в папке ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles\\[имя_проекта]***. Если этот файл новый и еще не был сохранен, Visual Studio автоматически сохраняет его, используя случайно созданное имя файла.

> [!NOTE]
> Если вы используете Visual Studio 2019 версии 16.1 или более ранней версии, файл будет расположен в папке *%USERPROFILE%\Documents\Visual Studio [версия]\Backup Files\\[имя_проекта]* . Дополнительные сведения см. в [журнале заметок о выпуске Visual Studio 2019](/visualstudio/releases/2019/release-notes-history/).

::: moniker-end

::: moniker range="vs-2017"

Используйте этот параметр, чтобы настроить периодичность автоматического сохранения файла в редакторе. Для ранее сохраненных файлов Visual Studio 2017 сохраняет копию файла в папке *%USERPROFILE%\Documents\Visual Studio [версия]\Backup Files\\[имя проекта]* . Если этот файл новый и еще не был сохранен, Visual Studio автоматически сохраняет его, используя случайно созданное имя файла.

::: moniker-end

**Хранить данные автовосстановления [n] дн.**

Используйте этот параметр, чтобы указать период, в течение которого Visual Studio будет хранить файлы, созданные для автоматического восстановления.

### <a name="see-also"></a>См. также раздел

- [Параметры - диалоговое окно](../../ide/reference/options-dialog-box-visual-studio.md)
