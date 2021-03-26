---
title: Элемент ProjectItem (шаблоны элементов Visual Studio) | Документация Майкрософт
description: Сведения об элементе ProjectItem для шаблонов элементов и о том, как он принимает различные атрибуты в зависимости от того, предназначен ли шаблон для проекта или элемента.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0910486202bca781ec19b6d5895e68ed93f8c3d5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068730"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Элемент ProjectItem (шаблоны элементов Visual Studio)
Указывает файл, включенный в шаблон элемента.

> [!NOTE]
> `ProjectItem`Элемент принимает различные атрибуты в зависимости от того, предназначен ли шаблон для проекта или элемента. В этом разделе описывается `ProjectItem` элемент для элемента. Описание `ProjectItem` элемента для шаблонов проектов см. в разделе [элемент ProjectItem (шаблоны проектов Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).

 \<VSTemplate> \<TemplateContent>
 \<ProjectItem>

## <a name="syntax"></a>Синтаксис

```
<ProjectItem
    SubType="Form/Component/CustomControl/UserControl"
    CustomTool="string"
    ItemType="string"
    ReplaceParameters="true/false"
    TargetFileName="TargetFileName.ext">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

| Атрибут | Описание |
|---------------------| - |
| `SubType` | Необязательный атрибут.<br /><br /> Указывает подтип элемента в многофайлового шаблона элемента. Это значение используется для определения редактора, который [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] будет использовать для открытия элемента. |
| `CustomTool` | Необязательный атрибут.<br /><br /> Задает CustomTool для элемента в файле проекта. |
| `ItemType` | Необязательный атрибут.<br /><br /> Задает значение ItemType для элемента в файле проекта. |
| `ReplaceParameters` | Необязательный атрибут.<br /><br /> Логическое значение, указывающее, содержит ли элемент значения параметров, которые должны быть заменены при создании проекта из шаблона. Значение по умолчанию — `false`. |
| `TargetFileName` | Необязательный атрибут.<br /><br /> Указывает имя элемента, созданного на основе шаблона. Этот атрибут полезен при использовании замены параметров для создания имени элемента. |

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Задает содержимое шаблона.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Значение типа `string` , представляющее имя файла в *ZIP* -файле шаблона.

## <a name="remarks"></a>Remarks
 `ProjectItem` является необязательным дочерним элементом `TemplateContent` .

 `TargetFileName`Атрибут может использоваться для переименования файлов с параметрами. Например, если файл *MyFile. vb* существует в корневом каталоге *ZIP* -файла шаблона, но вы хотите, чтобы имя файла основывалось на имени файла, предоставленного пользователем в диалоговом окне **Добавление нового элемента** , используйте следующий код XML:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 При создании элемента на основе этого шаблона имя файла будет основываться на имени пользователя, введенном в диалоговом окне **Добавление нового элемента** . Это полезно при создании шаблонов элементов с несколькими файлами. Дополнительные сведения см. [в разделе инструкции. создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md) и [параметров шаблона](../ide/template-parameters.md).

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для стандартного шаблона элемента для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] класса.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Практическое руководство. Создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)
