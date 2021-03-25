---
title: Элемент Folder (шаблоны проектов Visual Studio) | Документация Майкрософт
description: Сведения об элементе Folder и о том, как он указывает папку, которая будет добавлена в проект.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40e1df1d5efeab17adf60a8e1732991cb2cac02a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070132"
---
# <a name="folder-element-visual-studio-project-templates"></a>Элемент Folder (шаблоны проектов Visual Studio)
Указывает папку, которая будет добавлена в проект.

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<Folder>

## <a name="syntax"></a>Синтаксис

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный атрибут.<br /><br /> Имя папки проекта.|
|`TargetFolderName`|Необязательный атрибут.<br /><br /> Указывает имя, присваиваемое папке при создании проекта из шаблона. Этот атрибут полезен при использовании замены параметров для создания имени папки или именования папки со международной строкой, которая не может использоваться непосредственно в *ZIP* -файле.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|`Folder`|Указывает папку для добавления в проект. `Folder` элементы могут содержать дочерние `Folder` элементы.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Указывает файл, добавляемый в проект.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Необязательный дочерний элемент [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Remarks
 `Folder` является необязательным дочерним элементом `Project` .

 Для организации элементов проекта в папки шаблона можно использовать любой из следующих методов:

- Включите папки в *ZIP* -файл шаблона и добавьте их в проект в *VSTEMPLATE* -файле, указав путь к файлу в `ProjectItem` элементах без `Folder` элементов. Рекомендуем использовать этот метод. Пример:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Включите папки в *ZIP* -файл шаблона и добавьте их в проект в *VSTEMPLATE* -файле с `Folder` элементами. Пример:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Не включайте папки в *ZIP* -файл шаблона, но добавляйте папки с помощью `TargetFileName` атрибута `ProjectItem` элемента. Пример:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для шаблона проекта для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
