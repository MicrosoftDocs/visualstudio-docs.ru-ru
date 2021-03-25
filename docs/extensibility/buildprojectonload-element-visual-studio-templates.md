---
title: Элемент BuildProjectOnload (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе BuildProjectOnload и о том, как он создает только новые проекты при создании и добавлении их в решение.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9d50d33824be70a7df09cee878d516ddaaf9f8d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068171"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>Элемент BuildProjectOnload (шаблоны Visual Studio)
Создает только новые проекты при создании и добавлении их в решение. Все решение не строится.

Иерархия элементов:

```xml
<VSTemplate>
  <TemplateData>
    <BuildProjectOnLoad>
```

## <a name="syntax"></a>Синтаксис

```vb
<BuildProjectOnLoad> true/false </BuildProjectOnLoad>
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
|`TemplateData`|Классификация шаблона и определение его отображения в диалоговых окнах **Новый проект** и **Добавление нового элемента** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст должен иметь значение `true` или `false` , чтобы указать, следует ли создавать новый проект только при его создании на основе шаблона.

## <a name="remarks"></a>Remarks
 Параметр `BuildProjectOnLoad` является необязательным элементом. Значение по умолчанию — `false`.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для шаблона Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildProjectOnload>true</BuildProjectOnLoad>
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

- [Атрибут и элемент Буилдонлоад](buildonload-visual-studio-templates.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
