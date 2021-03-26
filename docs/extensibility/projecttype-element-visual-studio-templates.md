---
title: Элемент ProjectType (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе ProjectType и о том, как он классифицирует шаблон проекта, чтобы он появился в диалоговом окне Новый проект или Добавление нового элемента.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d494d27b2a3302d0beff68b770d0172edb520f35
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068691"
---
# <a name="projecttype-element-visual-studio-templates"></a>Элемент ProjectType (шаблоны Visual Studio)
Классификация шаблона проекта, чтобы он появился в указанной группе в диалоговом окне **Новый проект** или **Добавление нового элемента** .

> [!WARNING]
> Шаблоны проектов поддерживаются для C++ начиная с Visual Studio 2012. Они не поддерживаются для C++ в Visual Studio 2010 и более ранних версиях.

 \<VSTemplate> \<TemplateData>
 \<ProjectType>

## <a name="syntax"></a>Синтаксис

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Это значение указывает тип проекта, который будет создан шаблоном и должен содержать одно из следующих значений:

- `CSharp`: Указывает, что шаблон создает [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] проект или элемент.

- `VisualBasic`: Указывает, что шаблон создает [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] проект или элемент.

- `Web`: Указывает, что шаблон создает веб-проект или элемент. Если `ProjectType` элемент содержит это значение, язык проекта или элемента определяется в [элементе ProjectSubType (шаблоны Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).

## <a name="remarks"></a>Remarks
 `ProjectType` — обязательный дочерний элемент элемента `TemplateData`.

 Значение `ProjectType` элемента указывает, где находится шаблон: в диалоговом окне **Новый проект** или **Добавление нового элемента** . Например, шаблон со `ProjectType` значением `CSharp` отображается в узле **Visual C#** диалогового окна **Новый проект** .

 Подтип шаблона можно указать с помощью элемента [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) .

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
- [Элемент ProjectSubType (шаблоны Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
