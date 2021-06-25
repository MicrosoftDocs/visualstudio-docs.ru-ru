---
title: Элемент CommandPlacements | Документация Майкрософт
description: Элемент CommandPlacements группирует элементы CommandPlacement и другие группирования CommandPlacements. Элемент CommandPlacements является необязательным.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21e0feb3913b148b4320e69461bc5035655a392d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901894"
---
# <a name="commandplacements-element"></a>CommandPlacements, элемент
Элемент CommandPlacements группирует элементы CommandPlacement и другие группирования CommandPlacements.

 Элемент CommandPlacements является необязательным. Если команды, группы или меню не должны включаться в дополнительное расположение, не нужно включать этот раздел в *vsct* -файл.

## <a name="syntax"></a>Синтаксис

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|Условие|Необязательный элемент. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|CommandPlacements|Группирует элементы CommandPlacement и другие группирования CommandPlacements.|
|[CommandPlacement, элемент](../extensibility/commandplacement-element.md)|Позволяет включать кнопки, группы и меню в несколько групп или меню.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Коммандтабле, элемент](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды.|

## <a name="example"></a>Пример

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>См. также
- [CommandPlacement, элемент](../extensibility/commandplacement-element.md)
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
