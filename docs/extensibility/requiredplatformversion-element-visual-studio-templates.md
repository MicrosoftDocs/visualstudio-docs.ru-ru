---
description: Указывает минимальную версию операционной системы, которую должен правильно работать шаблон проекта.
title: RequiredPlatformVersion - элемент (шаблоны Visual Studio)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b1d7e3b8cc67f839977eb1e53d80731e59c064e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068431"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Элемент Рекуиредплатформверсион (шаблоны Visual Studio)

Указывает минимальную версию операционной системы, которую должен правильно работать шаблон проекта. Этот элемент используется для шаблонов проектов, которые создают [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложения.

 `RequiredPlatformVersion`Значение сравнивается непосредственно с версией операционной системы. Если значение `RequiredPlatformVersion` выше версии операционной системы, шаблон не отображается в диалоговом окне **Новый проект** . Чтобы указать шаблон для [!INCLUDE[win8](../debugger/includes/win8_md.md)] или более поздней версии, задайте для параметра значение `RequiredPlatformVersion` 6.2.0. Чтобы указать шаблон для [!INCLUDE[win81](../debugger/includes/win81_md.md)] или более поздней версии, задайте для параметра значение `RequiredPlatformVersion` 6.3.0.

 Шаблоны, которые указывают `RequiredPlatformVersion` = 8, совместимы с предыдущими [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] шаблонами клиента.

 VSTemplate TemplateData.... Таржетплатформнаме Рекуиредплатформверсион

## <a name="syntax"></a>Синтаксис

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 Отсутствует.

### <a name="attributes"></a>Атрибуты

 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[темплатеплатформнаме](../extensibility/templatedata-element-visual-studio-templates.md)|Задает платформу, для которой предназначен шаблон проекта.|

## <a name="text-value"></a>Текстовое значение

 Текстовое значение является обязательным.

## <a name="remarks"></a>Remarks

 Этот текст указывает минимальную версию операционной системы, требуемую для шаблона.

## <a name="example"></a>Пример

 В этом примере указывается, что шаблон проекта предназначен для [!INCLUDE[win8](../debugger/includes/win8_md.md)] или более поздней версии.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также

- [Элемент Таржетплатформнаме (шаблоны Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
