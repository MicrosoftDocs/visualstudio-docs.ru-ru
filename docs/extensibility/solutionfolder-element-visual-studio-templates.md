---
title: Элемент SolutionFolder (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе SolutionFolder и о том, как он группирует проекты в многопроектных шаблонах.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f65607a5411270e7f21e6ec6cdac0c087824b32b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056341"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>Элемент SolutionFolder (шаблоны Visual Studio)
Группирует проекты в многопроектных шаблонах.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>
 \<SolutionFolder>

## <a name="syntax"></a>Синтаксис

```
<SolutionFolder Name="DirectoryName">
    ...
</SolutionFolder>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный атрибут.<br /><br /> Имя папки решения.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Задает путь к VSTEMPLATE-файлу для одного проекта в многопроектном шаблоне.|
|`SolutionFolder`|Необязательный элемент.<br /><br /> Группирует проекты в многопроектных шаблонах.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Указывает организацию и содержимое многопроектных шаблонов.|
|`SolutionFolder`|Группирует проекты в многопроектных шаблонах.|

## <a name="remarks"></a>Remarks
 Многопроектные шаблоны используются в качестве контейнера для двух или нескольких проектов. Элемент `SolutionFolder` используется для распределения проектов в шаблоне по группам. Папки, указанные элементами `SolutionFolder`, создаются в виде папок решения в проекте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения о многопроектных шаблонах см. [в разделе как создавать Многопроектные шаблоны](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Пример
 В этом примере используется элемент `SolutionFolder`, чтобы разделить многопроектный шаблон на две группы — `Math Classes` и `Graphics Classes`. Шаблон содержит четыре проекта, два из которых размещаются в отдельных папках решения.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Пошаговое руководство. Создание многопроектных шаблонов](../ide/how-to-create-multi-project-templates.md)
