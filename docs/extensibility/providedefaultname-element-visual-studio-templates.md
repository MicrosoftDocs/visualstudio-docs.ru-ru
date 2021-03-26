---
title: Элемент Провидедефаултнаме (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе Провидедефаултнаме и о том, как он указывает, будет ли Visual Studio создавать имя по умолчанию Visual Studio в диалоговом окне "Добавление нового элемента" или "Создание проекта".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d29ca3075ee6e5ef031bb360ecfd10d6cb341c26
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068651"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Элемент Провидедефаултнаме (шаблоны Visual Studio)
Указывает, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] будет ли система проекта создавать имя по умолчанию для шаблона в диалоговом окне " **Добавление нового элемента** " или " **Создание проекта** ".

 \<VSTemplate> \<TemplateData>
 \<ProvideDefaultName>

## <a name="syntax"></a>Синтаксис

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
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

 Текст должен иметь значение `true` или `false` , что указывает, следует ли создавать имя по умолчанию для шаблона в диалоговом окне **Добавление нового элемента** или **Создание проекта** .

## <a name="remarks"></a>Remarks
 Параметр `ProvideDefaultName` является необязательным элементом. Значение по умолчанию — `true`.

 Если `ProvideDefaultName` элемент имеет `false` значение, поля **Name** диалоговых окон **Добавление нового элемента** и **Новый проект** содержат значения `<Enter_name>` .

 Используйте элемент [дефаултнаме](../extensibility/defaultname-element-visual-studio-templates.md) , чтобы указать имя проекта или элемента по умолчанию в диалоговых окнах **Добавление нового элемента** и **Новый проект** . Если значение элемента равно, то при пропуске `ProvideDefaultName` `true` `DefaultName` элемента для проектов в диалоговом окне заносится имя шаблона, то есть значение из элемента [Name](../extensibility/name-element-visual-studio-templates.md) .

## <a name="example"></a>Пример
 В следующем примере кода для элемента задается `ProvideDefaultName` значение `false` .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
