---
title: Элемент Висибилитиконстраинтс | Документация Майкрософт
description: Элемент Висибилитиконстраинтс определяет статическую видимость групп команд и панелей инструментов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 160a3950e31567aafc2d675971fd7263adb2ad5b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905466"
---
# <a name="visibilityconstraints-element"></a>Висибилитиконстраинтс, элемент
Элемент Висибилитиконстраинтс определяет статическую видимость групп команд и панелей инструментов. Видимость сначала контролируется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной средой разработки (IDE) без загрузки VSPackage.

## <a name="syntax"></a>Синтаксис

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
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
|[Висибилититем, элемент](../extensibility/visibilityitem-element.md)|Определяет статическую видимость команд и панелей инструментов.|
|[висибилитиконстраинтс](../extensibility/visibilityconstraints-element.md)|Определяет статическую видимость групп команд и панелей инструментов.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Коммандтабле, элемент](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды (например, пункты меню, меню, панели инструментов и поля со списком), которые пакет VSPackage предоставляет интегрированной среде разработки.|

## <a name="example"></a>Пример

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>См. также
- [Висибилититем, элемент](../extensibility/visibilityitem-element.md)
- [Командная таблица Visual Studio (. Vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
