---
title: Элемент Шовбидефаулт (шаблоны Visual Studio)
description: Сведения об элементе Шовбидефаулт и о том, как, если задано значение false, шаблон будет отображаться только под указанным TemplateGroupID.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ShowByDefault
helpviewer_keywords:
- <ShowByDefault> element [Visual Studio Templates]
- ShowByDefault element [Visual Studio Templates]
ms.assetid: 7be783f6-0ef6-42bc-924a-df9a2eba7781
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 25ba91a6276615929fed9494000abbfde07ef2b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056432"
---
# <a name="showbydefault-element-visual-studio-templates"></a>Элемент Шовбидефаулт (шаблоны Visual Studio)
Если задано `false` значение, шаблон будет отображаться только под указанным [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md).

 \<VSTemplate> \<TemplateData>
 \<ShowByDefault>

## <a name="syntax"></a>Синтаксис

```
<ShowByDefault> true/false </ShowByDefault>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Этот текст должен быть либо `true`, либо `false`. Значение true указывает, что шаблон будет отображаться для всех типов проектов. Значение false указывает, что шаблон будет отображаться только под указанным элементом `TemplateGroupID`.

## <a name="remarks"></a>Remarks
 Параметр `ShowByDefault` является необязательным элементом. Значение по умолчанию — `true`.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для шаблона [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ShowByDefault>false</ShowByDefault>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Элемент TemplateGroupID (шаблоны Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md)
