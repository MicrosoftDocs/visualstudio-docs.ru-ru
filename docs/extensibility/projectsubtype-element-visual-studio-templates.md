---
title: Элемент ProjectSubType (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе ProjectSubType и о том, как он классифицирует шаблон в подкатегорию значения, указанного в элементе ProjectType.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02dd5573de12e4626c267fa014f6c7fc8f243b72
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068682"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>Элемент ProjectSubType (шаблоны Visual Studio)
Классифицирует шаблон в подкатегорию значения, указанного в `ProjectType` элементе.

 \<VSTemplate> \<TemplateData>
 \<ProjectSubType>

## <a name="syntax"></a>Синтаксис

```xml
<ProjectSubType> SubType </ProjectSubType>
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

 Это значение указывает подкатегорию шаблона.

## <a name="remarks"></a>Remarks
 `ProjectSubType` — необязательный дочерний элемент элемента `TemplateData`.

 `ProjectSubType`Элемент предоставляет подкатегорию для элемента [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) . Это значение может включать:

- `SmartDevice-NETCFv1`: Указывает, что шаблон предназначен для [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] версии 1,0.

- `SmartDevice-NETCFv2`: Указывает, что шаблон предназначен для [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] версии 2,0.

  Если шаблон содержит `ProjectType` элемент со значением `Web` , `ProjectSubType` элемент указывает язык программирования шаблона. Этот элемент может иметь следующие значения:

- `CSharp`: Указывает, что шаблон создает [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] веб-проект или элемент.

- `VisualBasic`: Указывает, что шаблон создает [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] веб-проект или элемент.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для шаблона проекта для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения устройства, предназначенного для [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] версии 2,0.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
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
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Элемент ProjectType (шаблоны Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)
