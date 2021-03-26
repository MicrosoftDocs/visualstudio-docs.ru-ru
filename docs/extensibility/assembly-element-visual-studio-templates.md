---
title: Элемент Assembly (шаблоны Visual Studio) | Документация Майкрософт
titleSuffix: ''
description: Сведения об элементе Assembly и о том, как он указывает сведения о сборке, которую шаблон использует для добавления ссылки на эту сборку в проекты.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 54fc5cfccde99776136f0cb904d02bf6a4971045
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097322"
---
# <a name="assembly-element-visual-studio-templates"></a>Элемент Assembly (шаблоны Visual Studio)
Указывает сведения о сборке, которую шаблон использует для добавления ссылки на эту сборку в проекты.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>
 \<Assembly>

## <a name="syntax"></a>Синтаксис

```
<Assembly> AssemblyName </Assembly>
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
|[Ссылки](../extensibility/reference-element-visual-studio-templates.md)|Указывает ссылку на сборку, которую нужно добавить при добавлении элемента в проект.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Этот текст указывает сборку, добавляемую в проект при создании экземпляра шаблона элемента. Это имя сборки должно быть указано одним из следующих способов:

- Как полное имя сборки. Пример:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Как простая ссылка на текст. Пример:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Remarks
 `Assembly` — обязательный дочерний элемент элемента `Reference`.

 `Reference`Элементы, `References,` и `Assembly` можно использовать только в *VSTEMPLATE* -файлах, имеющих `Type` значение атрибута `Item` .

## <a name="example"></a>Пример
 В следующем примере показан `TemplateContent` элемент шаблона элемента. Этот XML-файл добавляет ссылки на сборки *System.dll* и *System.Data.dll* .

```
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
