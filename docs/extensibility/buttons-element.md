---
title: Элемент Buttons | Документация Майкрософт
description: Элементы Button группы элементов кнопки, представляющие отдельные команды. В этой статье содержится пример.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2952f9f6747e52604e9f24cd173ab07f8d5a4756
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900802"
---
# <a name="buttons-element"></a>Button, элемент
Группирует элементы [кнопки](../extensibility/button-element.md) , представляющие отдельные команды.

## <a name="syntax"></a>Синтаксис

```
<Buttons>
  <Button>... </Button>
  <Button>... </Button>
</Buttons>
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
|[Button, элемент](../extensibility/buttons-element.md)|Группирует элементы кнопки.|
|[Button, элемент](../extensibility/button-element.md)|Определяет команду, с которой пользователь может взаимодействовать.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Commands](../extensibility/commands-element.md)|Представляет коллекцию команд на панели инструментов VSPackage.|

## <a name="example"></a>Пример

```
<Buttons>
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>
    <Strings>
      <ButtonText>C# Command Sample</ButtonText>
    </Strings>
  </Button>
</Buttons>
```

## <a name="see-also"></a>См. также
- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
