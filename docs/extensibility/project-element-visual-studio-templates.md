---
title: Элемент Project (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе Project и о том, как он указывает файлы или каталоги, добавляемые в проект.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52bfb5f65aa9d42c46eece619a21152c51e8fa28
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068808"
---
# <a name="project-element-visual-studio-templates"></a>Элемент Project (шаблоны Visual Studio)
Указывает файлы или каталоги, добавляемые в проект.

 \<VSTemplate> \<TemplateContent>
 \<Project>

## <a name="syntax"></a>Синтаксис

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`File`|Обязательный атрибут.<br /><br /> Указывает имя файла проекта в *ZIP* -файле шаблона.|
|`ReplaceParameters`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, содержит ли файл проекта значения параметров, которые необходимо заменить при создании проекта из шаблона. Значение по умолчанию — `false`.|
|`TargetFileName`|Необязательный атрибут.<br /><br /> Указывает имя файла проекта при создании проекта на основе шаблона.|
|`IgnoreProjectParameter`|Необязательный атрибут.<br /><br /> Указывает, следует ли добавить проект в текущее решение. Если значение пользовательского параметра "$*микустомпараметер*$" существует в файле замены параметров, проект создается, но не добавляется как часть текущего открытого решения.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Папка](../extensibility/folder-element-visual-studio-project-templates.md)|Необязательный элемент.<br /><br /> Указывает папку для добавления в проект.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Необязательный элемент.<br /><br /> Указывает файл, добавляемый в проект.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Обязательный элемент.|

## <a name="remarks"></a>Remarks
 `Project` — необязательный дочерний элемент элемента `TemplateContent`.

 `Project`Элемент используется для указания проекта и, следовательно, допустим только в шаблонах проектов.

 `Project` элементы могут иметь дочерние элементы [папки](../extensibility/folder-element-visual-studio-project-templates.md) или дочерние элементы [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) , но не `Folder` оба `ProjectItem` дочерних элемента.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически переименовывает имя файла проекта на основе имени, введенного пользователем в диалоговом окне **Новый проект** . Используйте `TargetFileName` атрибут, если требуется указать альтернативное имя файла для файлов проекта, созданных с помощью шаблона.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для шаблона проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
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
- [Элемент ProjectItem (шаблоны проектов Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Элемент Folder (шаблоны проектов Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
