---
title: Элемент PreviewImage (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе PreviewImage и о том, как он указывает имя файла для предварительного просмотра изображения, которое будет отображаться в диалоговом окне Новый проект или Добавление нового элемента.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fc7a370885d24a586262bebd4182daacd84a9b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090230"
---
# <a name="previewimage-element-visual-studio-templates"></a>Элемент PreviewImage (шаблоны Visual Studio)
Указывает изображение предварительного просмотра в виде имени файла для изображения предварительного просмотра, которое будет отображаться в диалоговом окне **Создание проекта** или **Добавление нового элемента** .

 \<VSTemplate> \<TemplateData>
 \<PreviewImage>

## <a name="syntax"></a>Синтаксис

```
<PreviewImage>"filename"</PreviewImage>
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

 Текст должен быть строкой, представляющей имя файла.

## <a name="remarks"></a>Remarks
 Параметр `PreviewImage` является необязательным элементом.

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
