---
title: Элемент EnableEditOfLocationField (шаблоны Visual Studio)
description: Сведения об элементе EnableEditOfLocationField и о том, как он указывает, может ли пользователь изменять поле расположения.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- EnableEditOfLocationField (Visual Studio project templates)
ms.assetid: 51a91963-8a3f-4741-928e-bc90c11473bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3f2ca8799b0816ffe5c33d954d362183f330f25
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070197"
---
# <a name="enableeditoflocationfield-element-visual-studio-templates"></a>Элемент EnableEditOfLocationField (шаблоны Visual Studio)
Указывает, может ли пользователь изменять поле расположения.

 \<VSTemplate> \<TemplateData>
 \<EnableEditOfLocationField>

## <a name="syntax"></a>Синтаксис

```
<EnableEditOfLocationField> true/false </EnableEditOfLocationField>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 None

### <a name="child-elements"></a>Дочерние элементы
 Нет

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст должен иметь значение `true` или `false` , что указывает, может ли пользователь изменять текстовое поле **Расположение** в диалоговом окне **Новый проект** .

## <a name="remarks"></a>Remarks
 Параметр `EnableEditOfLocationField` является необязательным элементом. Значение по умолчанию — `true` , что позволяет пользователю изменять значение в текстовом поле **Расположение** в диалоговом окне **Новый проект** .

 В диалоговом окне **Новый проект** в текстовом поле **Расположение** указывается каталог, в котором сохранен новый проект.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableEditOfLocationField>false</EnableEditOfLocationField>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
