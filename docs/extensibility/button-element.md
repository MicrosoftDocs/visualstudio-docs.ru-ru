---
title: Элемент Button | Документация Майкрософт
description: 'Элемент Button определяет элемент, с которым пользователь может взаимодействовать. Кнопки могут быть разными видами: Button, Менубуттон и Сплитдропдовн.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec0640313195d6a15599d1a765081557c0c1a75a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068150"
---
# <a name="button-element"></a>Button, элемент
Определяет элемент, с которым пользователь может взаимодействовать. Кнопки могут принадлежать разным типам: Button, Менубуттон и Сплитдропдовн.

## <a name="syntax"></a>Синтаксис

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный. Идентификатор GUID идентификатора команды GUID/ID.|
|идентификатор|Обязательный. Идентификатор идентификатора команды GUID/ID.|
|priority|Необязательный параметр. Числовое значение, указывающее приоритет.|
|тип|Необязательный параметр. Перечислимое значение, указывающее тип кнопки.<br /><br /> Если значение не задано, функция использует кнопку.<br /><br /> Кнопка<br /> Стандартная команда, которая отображается на панелях инструментов (обычно в виде значков), меню и контекстных меню.<br /><br /> менубуттон<br /> Пункт меню, который не выполняет команду, но создает другое меню.<br /><br /> сплитдропдовн<br /> Элементы управления, такие как кнопки Отменить и повторить на стандартной панели инструментов в Microsoft Word.|
|Условие|Необязательный параметр. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Родительский элемент](../extensibility/parent-element.md)|Необязательный параметр. Родительский элемент кнопки.|
|[Icon, элемент](../extensibility/icon-element.md)|Необязательный параметр. Значок, связанный с кнопкой.|
|[Элемент флага команды](../extensibility/command-flag-element.md)|Обязательный. Допустимые значения CommandFlag для кнопки:<br /><br /> -Алловпарамс<br /><br /> -Коммандвеллонли<br /><br /> -Дефаултдисаблед<br /><br /> -Дефаултинвисибле<br /><br /> -Донткаче<br /><br /> -ДинамиЦитемстарт<br /><br /> -Динамиквисибилити<br /><br /> -Фиксменуконтроллер<br /><br /> -Иконандтекст<br /><br /> -Нобуттонкустомизе<br /><br /> -Не настроено<br /><br /> -Нокэйкустомизе<br /><br /> -Ношовонменуконтроллер<br /><br /> -PICT<br /><br /> -I Exec<br /><br /> -Проффередкмд<br /><br /> -Раутетодокс<br /><br /> -Тексткаскадеусебтн<br /><br /> -Текстменуусебуттон<br /><br /> -Текстчанжес<br /><br /> -Текстчанжесбуттон<br /><br /> -Текстконтекстусебуттон<br /><br /> -Текстменуктрлусемену<br /><br /> -Текстменуусебуттон<br /><br /> -TextOnly|
|[Элемент strings](../extensibility/strings-element.md)|Обязательный. Необходимо определить дочерний [элемент ButtonText](../extensibility/buttontext-element.md) .|
|Annotation|Необязательный комментарий.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Button, элемент](../extensibility/buttons-element.md)|Группирует элементы кнопки.|

## <a name="example"></a>Пример
 В следующем примере определяется кнопка в *vsct* -файле.

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
