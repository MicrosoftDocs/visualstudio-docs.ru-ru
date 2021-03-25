---
title: Новые возможности пакета SDK для Visual Studio 2019 | Документация Майкрософт
description: В Visual Studio SDK добавлены новые и обновленные функции Visual Studio 2019, включая улучшения регистрации в редакторе.
ms.custom: SEO-VS-2020
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2d8e08136eb142e5e72c08e23860bf94f01dc87c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061905"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Новые возможности пакета SDK для Visual Studio 2019

Пакет SDK для Visual Studio содержит следующие новые и обновленные функции Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Предупреждение о синхронных автозагружаемых расширениях

Пользователи увидят предупреждение, если какое-либо из установленных расширений синхронно автоматически загружается при запуске. Вы можете узнать больше о предупреждении в [синхронно загружаемых расширениях](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Единый унифицированный пакет SDK для Visual Studio

Теперь все ресурсы пакета SDK для Visual Studio можно получить с помощью одного пакета NuGet [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Усовершенствования регистрации в редакторе

С момента создания Visual Studio поддерживала регистрацию пользовательского редактора, в которой редактор может объявить свое сходство для конкретных расширений (например,. XAML и. RC) или что подходит для любого расширения (. *). Начиная с Visual Studio 2019 версии 16,1, мы расширили поддержку регистрации редактора.

### <a name="filenames"></a>Имена файлов

В дополнение к или вместо регистрации поддержки для конкретного расширения файла редактор может зарегистрировать, что он поддерживает определенные имена файлов, применив новый `ProvideEditorFilename` атрибут к пакету редактора.

Например, редактор, поддерживающий все JSON файлы, применяет этот `ProvideEditorExtension` атрибут к пакету:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Начиная с 16,1, если Медитор поддерживает только несколько хорошо известных JSON-файлов, вместо этого можно применить эти `ProvideEditorFilename` атрибуты к пакету:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>Объектов UIContext

Редактор может зарегистрировать один или несколько объектов UIContext, которые представляют, когда он включен. Объектов UIContext регистрируются путем применения одного или нескольких экземпляров `ProvideEditorUIContextAttribute` к пакету, который регистрирует редактор.

Если редактор зарегистрировал объектов UIContext:

- Если по крайней мере один из зарегистрированных объектов UIContext активен при открытии файла с данным расширением, редактор включается в поиск редактора.
- Если ни один из зарегистрированных объектов UIContext не активен, редактор не включается в поиск редактора.

Если редактор не регистрирует объектов UIContext, он всегда включается в поиск этого расширения в редакторе.

Например, если редактор доступен только при открытом проекте C#, он может объявить это сходство, применив `ProvideEditorUIContext` атрибут:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
