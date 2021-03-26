---
title: Элемент SortOrder (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе SortOrder и о том, как он указывает значение, используемое для размещения шаблона в том виде, в каком он отображается в диалоговом окне Новый проект или Добавление нового элемента.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a195e3801ce505d2c1f069c07ff4457e1c1042b3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073798"
---
# <a name="sortorder-element-visual-studio-templates"></a>Элемент SortOrder (шаблоны Visual Studio)
Задает значение, используемое для упорядочения шаблона (помимо других шаблонов в той же категории), которое отображается в диалоговом окне **Создание проекта** или **Добавление нового элемента** .

 \<VSTemplate> \<TemplateData>
 \<SortOrder>

## <a name="syntax"></a>Синтаксис

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Объект `integer` , представляющий значение порядка сортировки.

## <a name="remarks"></a>Remarks
 Параметр `SortOrder` является необязательным элементом. Значение по умолчанию — 100, а все значения должны быть кратными 10.

 `SortOrder`Элемент не учитывается для шаблонов, созданных пользователем. Все созданные пользователем шаблоны сортируются в алфавитном порядке.

 Шаблоны с низким порядком сортировки отображаются в диалоговом окне **Создание проекта** или **Добавление элемента** перед шаблонами, имеющими значения с высоким порядком сортировки.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для стандартного [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] шаблона класса.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 В этом примере `SortOrder` элемент относительно высокий. Вполне вероятно, что другие [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] шаблоны элементов будут иметь `SortOrder` значение ниже `290` и будут отображаться перед этим шаблоном в диалоговом окне **новый элемент** .

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
