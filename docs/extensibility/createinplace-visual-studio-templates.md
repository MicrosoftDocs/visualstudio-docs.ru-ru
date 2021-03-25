---
title: Элемент CreateInPlace (шаблоны Visual Studio)
description: Сведения об элементе CreateInPlace и о том, как он указывает, следует ли создавать проект и выполнять замену параметров в определенном или временном расположении.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace
helpviewer_keywords:
- CreateInPlace element [Visual Studio Templates]
- <CreateInPlace> element [Visual Studio Templates]
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3da93439b245c2f8f23a8fa5b79d9fef3a48a9d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089489"
---
# <a name="createinplace-element-visual-studio-templates"></a>Элемент CreateInPlace (шаблоны Visual Studio)
Указывает, следует ли создать проект и выполнить замену параметров в указанном расположении или выполнить замену параметров во временном расположении, а затем сохранить проект в указанном расположении.

 \<VSTemplate> \<TemplateData>
 \<CreateInPlace>

## <a name="syntax"></a>Синтаксис

```
<CreateInPlace> true/false </CreateInPlace>
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

 Этот текст должен быть либо `true`, либо `false`. Если задано `true` значение, создается проект и выполняется замена параметров в расположении, указанном в диалоговом окне **Новый проект** . Если значение `false` равно, то замена параметров выполняется во временном расположении, а затем проект копируется в указанное расположение.

## <a name="remarks"></a>Remarks
 Параметр `CreateInPlace` является необязательным элементом. Значение по умолчанию — `true`.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для шаблона [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateInPlace>false</CreateInPlace>
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
