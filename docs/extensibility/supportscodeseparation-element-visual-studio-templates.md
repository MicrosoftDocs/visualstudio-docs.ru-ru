---
title: Элемент SupportsCodeSeparation (шаблоны проектов Visual Studio)
titleSuffix: ''
description: Сведения об элементе Суппортскодесепаратион и о том, как он указывает, включен ли флажок Размещать код в отдельном файле в диалоговом окне "Добавление нового элемента".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 699d38f712885d1e2b08a111baa7db75fb7829da
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056133"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>Элемент SupportsCodeSeparation (шаблоны проектов Visual Studio)
Указывает, включен ли флажок « **размещать код в отдельном файле** » в диалоговом окне « **Добавление нового элемента** ».

 \<VSTemplate> \<TemplateData>
 \<SupportsCodeSeparation>

## <a name="syntax"></a>Синтаксис

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Классификация шаблона и определение его отображения в диалоговом окне **Новый проект** или **новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст должен иметь значение `true` или `false` , что указывает, включен ли флажок " **размещать код в отдельном файле** " в диалоговом окне " **Добавление нового элемента** ".

## <a name="remarks"></a>Remarks
 Параметр `SupportsCodeSeparation` является необязательным элементом. Значение по умолчанию — `false`.

 `SupportsCodeSeparation`Элемент доступен только для шаблонов веб-элементов.

 Разделение кода или модель страницы кода программной части позволяет размещать разметку в одном файле и программном коде в другом файле. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] и другие языки .NET используют эту модель.

## <a name="example"></a>Пример
 В следующем примере указывается, чтобы отобразить **код места в отдельном файле** .

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsCodeSeparation>true</SupportsCodeSeparation>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
