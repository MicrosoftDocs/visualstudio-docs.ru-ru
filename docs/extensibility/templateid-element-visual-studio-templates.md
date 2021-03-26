---
title: Элемент TemplateID (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе TemplateID и о том, как он задает идентификатор для шаблона элемента, отнесенного к группе шаблонов элементов с помощью элемента TemplateGroupID.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e33f2d5c424e5d48cff212dc736bbc13e58801d5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056016"
---
# <a name="templateid-element-visual-studio-templates"></a>Элемент TemplateID (шаблоны Visual Studio)
Задает идентификатор для шаблона элемента, разбитого по категориям в группе шаблонов элементов с помощью элемента [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .

 \<VSTemplate> \<TemplateData>
 \<TemplateID>

## <a name="syntax"></a>Синтаксис

```
<TemplateID> ... </TemplateID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Объект `string` , представляющий идентификатор шаблона элемента, отнесенного к группе шаблонов элементов по `TemplateGroupID` элементу.

## <a name="remarks"></a>Remarks
 Параметр `TemplateID` является необязательным элементом.

 Если файл VSTEMPLATE пропускает `TemplateID` элемент, то в качестве идентификатора шаблона используется элемент [Name](../extensibility/name-element-visual-studio-templates.md) .

 Значение `TemplateID` элемента используется вместе с регистрацией системы проекта (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\ ) для фильтрации шаблонов, которые отображаются в диалоговом окне **Добавление нового элемента** .

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
