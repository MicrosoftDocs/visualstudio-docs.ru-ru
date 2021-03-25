---
title: Элемент GuidSymbol | Документация Майкрософт
description: 'Элемент GuidSymbol содержит GUID пары GUID: ID, представляющей меню, группу или команду.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb683c99614797fa8b05eae87c758ec33f675c99
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057459"
---
# <a name="guidsymbol-element"></a>GuidSymbol, элемент
`GuidSymbol`Элемент содержит GUID пары GUID: ID, представляющей меню, группу или команду. Идентификатор берется из `IDSymbol` элемента в `GuidSymbol` элементе. `GuidSymbol`Элемент имеет `name` атрибут, предоставляющий понятное имя GUID, которое содержится в `value` атрибуте.

## <a name="syntax"></a>Синтаксис

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|name|Обязательный. Имя символа GUID.|
|значение|Обязательный. Идентификатор GUID символа GUID.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[IDSymbol, элемент](../extensibility/idsymbol-element.md)|Содержит идентификатор пары GUID: ID, представляющей меню, группу или команду.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Symbols](../extensibility/symbols-element.md)|Группирует `GuidSymbol` элементы в *vsct* -файл.|

## <a name="remarks"></a>Remarks
 Как правило, *vsct* -файл содержит три `GuidSymbol` элемента в своем `Symbols` разделе: один для самого пакета, один для набора команд (коллекция меню, групп и команд, доступных для пакета), и один для точечных рисунков, которые предоставляют значки для кнопок и других визуальных компонентов. Каждый `IDSymbol` элемент в заданном `GuidSymbol` элементе должен иметь уникальное значение `value` . Однако `IDSymbol` в пакете могут существовать элементы, имеющие одинаковые значения, если они имеют разные родительские объекты.

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
