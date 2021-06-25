---
title: Внешний элемент | Документация Майкрософт
description: Элемент extern ссылается на любые файлы внешних заголовков (h) для слияния с vsct-файлом во время компиляции.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 502b93f18aacfed26d3ea440c017e6de5281a35d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900191"
---
# <a name="extern-element"></a>Внешний элемент
Элемент extern ссылается на любые файлы внешних заголовков (*h*) для слияния с *vsct* -файлом во время компиляции. Объединяемые файлы должны находиться на пути включения, заданном компилятору VSCT или на который ссылается [элемент include](../extensibility/include-element.md). Файлы могут быть другими *vsct* или файлами заголовков C++.

 Определения в заголовочных файлах должны иметь формат "#define [символ] [значение]" значение может быть другим символом, если он был определен ранее. Определения могут использоваться в условных операторах командных элементов. Любой символ, который фактически не используется, будет отклонен.

 Элемент Коммандтабле extern

## <a name="syntax"></a>Синтаксис

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|href|Обязательный. Путь к файлу заголовка:<br /><br /> href = "стдидкмд. h"|
|Условие|Необязательный элемент. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|Язык|Необязательный элемент. Язык по умолчанию для всех [\<Strings>](../extensibility/strings-element.md) элементов в таблице команд:<br /><br /> Language = "en-US"|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Нет.|Отсутствует.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Коммандтабле, элемент](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, т. е. пункты меню, меню, панели инструментов и поля со списком, которые пакет VSPackage предоставляет интегрированной среде разработки.|

## <a name="example"></a>Пример

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
