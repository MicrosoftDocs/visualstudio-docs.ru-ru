---
title: Родительский элемент | Документация Майкрософт
description: Родительский элемент указывает, что элемент является родительским по отношению к кнопке, полю со списком, меню или группе.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3dbf7202ac7fb94762ea132a2620625fae97ddfb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901556"
---
# <a name="parent-element"></a>Родительский элемент
Родительским элементом кнопки или поля со списком может быть только группа. Родительским элементом меню или группы может быть любое другое меню или группа. В [элементе CommandPlacement](../extensibility/commandplacement-element.md)этот элемент является обязательным; во всех остальных случаях это необязательно. Если этот элемент опущен, то родительский объект `Group_Undefined:0` будет подразумеваемым.

## <a name="syntax"></a>Синтаксис

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный. Идентификатор GUID идентификатора команды GUID/ID.|
|идентификатор|Обязательный. Идентификатор идентификатора команды GUID/ID.|

### <a name="child-elements"></a>Дочерние элементы
 Нет

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Коммандтабле, элемент](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, предоставляемые пакетом VSPackage в интегрированной среде разработки (IDE). Например, пункты меню, меню, панели инструментов и поля со списком.|
|[Button, элемент](../extensibility/buttons-element.md)|Группирует элементы [элемента Button](../extensibility/button-element.md) .|
|[Элемент menus](../extensibility/menus-element.md)|Определяет все меню, которые реализует VSPackage.|
|[Элемент Groups](../extensibility/groups-element.md)|Содержит записи, определяющие группы команд VSPackage.|

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
