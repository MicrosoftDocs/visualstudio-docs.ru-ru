---
title: Элемент Combo | Документация Майкрософт
description: 'Элемент ComboBox определяет команды, которые отображаются в поле со списком. Существует четыре типа: Дропдовнкомбо, Динамиккомбо, Индекскомбо и Мрукомбо.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 431d68b6e545506f5fc90cc5a98a52dd4f1c33ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904959"
---
# <a name="combo-element"></a>Элемент Combo
Определяет команды, которые отображаются в поле со списком. Существует четыре типа полей со списками: Дропдовнкомбо, Динамиккомбо, Индекскомбо и Мрукомбо.

## <a name="syntax"></a>Синтаксис

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный. Идентификатор GUID идентификатора команды GUID/ID.|
|идентификатор|Обязательный. Идентификатор идентификатора команды GUID/ID.|
|дефаултвидс|Обязательный. Целое число, задающее ширину в пикселе для поля со списком.|
|идкоммандлист|Обязательный. Идентификатор, который отправляется целевому объекту активной команды для получения списка элементов, отображаемых в поле со списком. Идентификатор будет находиться в той же области GUID, что и элемент управления.|
|priority|Необязательный элемент. Числовое значение, указывающее приоритет.|
|тип|Необязательный элемент. Перечислимое значение, указывающее тип кнопки.<br /><br /> Если значение не задано, функция использует кнопку.<br /><br /> дропдовнкомбо<br /> Пакет VSPackage отвечает за заполнение содержимого этого поля со списком. Пользователь не может ввести что-либо в текстовое поле этого раскрывающегося списка.<br /><br /> динамиккомбо<br /> Пакет VSPackage отвечает за заполнение содержимого этого поля со списком. Пользователь может изменить это поле со списком, а также выбрать в нем элементы.<br /><br /> индекскомбо<br /> То же, что и Динамиккомбо, за исключением того, что он создает индекс элемента, а не его текст.<br /><br /> мрукомбо<br /> Заполняется интегрированной средой разработки (IDE) от имени VSPackage.  Пользователь может изменить в этом поле со списком. Интегрированная среда разработки запоминает до 16 последних записей в поле со списком.<br /><br /> Когда пользователь выбирает что-либо в поле со списком или вводит что-нибудь новое, интегрированная среда разработки уведомляет соответствующий пакет VSPackage.|
|Условие|Необязательный элемент. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Parent|Необязательный элемент. Родительский элемент кнопки.|
|CommandFlag|Обязательный. См. раздел [флаг команды](../extensibility/command-flag-element.md). Допустимые значения CommandFlag для кнопки:<br /><br /> -CaseSensitive<br /><br /> -Коммандвеллонли<br /><br /> -Дефаултдисаблед<br /><br /> -Дефаултинвисибле<br /><br /> -Динамиквисибилити<br /><br /> -Фильтрация ввода<br /><br /> -Иконандтекст<br /><br /> -Ноаутокомплете<br /><br /> -Нобуттонкустомизе<br /><br /> -Не настроено<br /><br /> -Нокэйкустомизе<br /><br /> -Стретчхоризонталли|
|Строки|Обязательный. См. [элемент strings](../extensibility/strings-element.md). Необходимо определить дочерний элемент ButtonText.|
|Annotation|Необязательный комментарий.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Commands](../extensibility/commands-element.md)|Представляет коллекцию команд на панели инструментов VSPackage.|

## <a name="example"></a>Пример

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
