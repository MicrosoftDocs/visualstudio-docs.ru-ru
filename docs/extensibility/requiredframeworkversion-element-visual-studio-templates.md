---
description: Указывает минимальную версию платформа .NET Framework, необходимую для шаблона.
title: Элемент RequiredFrameworkVersion (шаблоны Visual Studio)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 661e4067ac0191444be8ec7f1136f805ea8b39b5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068457"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Элемент Рекуиредфрамеворкверсион (шаблоны Visual Studio)

Указывает минимальную версию платформа .NET Framework, необходимую для шаблона. В результате раскрывающийся список **версии целевой платформы** будет отображаться в диалоговом окне **Новый проект** . `RequiredFrameworkVersion`Элемент также определяет наименьшее значение, доступное в раскрывающемся списке.

> [!IMPORTANT]
> Начиная с Visual Studio 2017 версии 15,6, раскрывающийся список **версии целевой платформы** больше не является фильтром для отображаемых шаблонов в разделе " **шаблоны** " диалогового окна " **Создание проекта** ". Вместо этого раскрывающийся список выступает в качестве средства выбора платформы для выбранного шаблона.

 \<VSTemplate> \<TemplateData>
 \<RequiredFrameworkVersion>

## <a name="syntax"></a>Синтаксис

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Классификация шаблона и определение его отображения в диалоговом окне " **Новый проект** " или " **Добавление нового элемента** ".|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст должен быть минимальным номером версии платформа .NET Framework, который необходим для шаблона.

## <a name="remarks"></a>Remarks

Параметр `RequiredFrameworkVersion` является необязательным элементом. Используйте этот элемент, только если шаблон поддерживает определенную минимальную версию (и более поздние версии, если таковые имеются) платформа .NET Framework. Если указать элемент, `RequiredFrameworkVersion` а шаблон не поддерживает определенную минимальную версию платформа .NET Framework, раскрывающийся список **Версия целевой платформы** будет отображаться, если он неприменим.

## <a name="example"></a>Пример

В следующем примере показаны метаданные для стандартного [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] шаблона класса.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

В этом примере минимальная версия платформа .NET Framework, необходимая для шаблона, представленная `RequiredFrameworkVersion` , — 3,0. Проект, созданный с помощью этого шаблона, может ориентироваться платформа .NET Framework версиями, начиная с 3,0.

## <a name="see-also"></a>См. также

- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Общие сведения о настройке для платформы](../ide/visual-studio-multi-targeting-overview.md)
