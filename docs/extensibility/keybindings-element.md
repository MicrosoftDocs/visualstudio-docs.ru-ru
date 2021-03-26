---
title: Элемент сочетания клавиш | Документация Майкрософт
description: Элемент сочетания клавиш группирует элементы настраиваемое сочетание клавиш и другие группирования сочетания клавиш. В этой статье содержится пример.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- KeyBindings
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBindings element (VSCT XML schema)
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a590dc8bc1313e5c32b26465ae3dd346ed0564fd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074019"
---
# <a name="keybindings-element"></a>Сочетания клавиш, элемент
Элемент сочетания клавиш группирует элементы настраиваемое сочетание клавиш и другие группирования сочетания клавиш.

## <a name="syntax"></a>Синтаксис

```xml
<KeyBindings>
  <KeyBinding>... </KeyBinding>
  <KeyBinding>... </KeyBinding>
</KeyBindings>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|Условие|Необязательный параметр. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Настраиваемое сочетание клавиш, элемент](../extensibility/keybinding-element.md)|Задает сочетания клавиш для команд.|
|[Сочетания клавиш](../extensibility/keybindings-element.md)|Группирует элементы настраиваемое сочетание клавиш и другие группирования сочетания клавиш.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Коммандтабле, элемент](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды.|

## <a name="example"></a>Пример

```xml
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>См. также
- [Настраиваемое сочетание клавиш, элемент](../extensibility/keybinding-element.md)
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
