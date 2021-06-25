---
title: Определение элемента | Документация Майкрософт
description: Элемент define определяет пару "имя символа" и "значение". Этот символ может быть вычислен с помощью условных атрибутов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 409621410db727f933e41bae894f125dc877b4c2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898049"
---
# <a name="define-element"></a>Определение элемента
Определяет пару "имя символа" и "значение". Этот символ может быть вычислен с помощью условных атрибутов. Дополнительные сведения см. в разделе [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md). См. также [элемент Symbols](../extensibility/symbols-element.md).

## <a name="syntax"></a>Синтаксис

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|name|Обязательный. Имя символа:<br /><br /> Name = "Mode"|
|значение|Обязательный. Значение символа:<br /><br /> value = "Standard"|
|Условие|Необязательный элемент. Дополнительные сведения см. в разделе [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Коммандтабле, элемент](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, предоставляемые пакетом VSPackage в интегрированной среде разработки (IDE). Например, пункты меню, меню, панели инструментов и поля со списком.|

## <a name="example"></a>Пример

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
