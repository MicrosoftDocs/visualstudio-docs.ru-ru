---
title: Структура файла .xml [Content_types] | Документация Майкрософт
description: Сведения о структуре файла типов содержимого, которая содержит сведения о типах содержимого в пакете VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96d4d0eeea34300894674a2105d080e8a6abb607
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900425"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Структура файла [типы_содержимого].xml
Содержит сведения о типах содержимого в пакете VSIX. Visual Studio использует файл [Content_Types] .xml для установки пакета, но не устанавливает сам файл.

> [!NOTE]
> Хотя этот раздел применим только к файлам [Content_Type] .xml, которые используются в пакетах VSIX, тип файла .xml [Content_Types] является частью стандарта *Open Packaging Conventions (OPC)* . Дополнительные сведения см. в статье [OPC: новый стандарт для упаковки данных](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) на веб-сайте MSDN.

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описывается корневой элемент, его атрибуты и дочерние элементы.

### <a name="root-element"></a>Корневой элемент

|Элемент|Описание|
|-------------|-----------------|
|`Types`|Содержит дочерние элементы, которые перечисляют типы файлов в пакете VSIX.|

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Xmlns`|(Обязательно.) Расположение схемы, используемой для этого файла .xml [Content_Types].|

### <a name="attribute-name-attribute"></a>{Имя атрибута} Версию

| Значение | Описание |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | Расположение схемы типов содержимого. |

### <a name="child-elements"></a>Дочерние элементы
 Элемент `Types` может содержать любое число элементов `Default`.

|Элемент|Описание|
|-------------|-----------------|
|`Default`|Описывает тип содержимого в пакете VSIX. Каждый тип файлов в пакете должен иметь собственный `Default` элемент.|

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Extension`|Расширение имени файла в пакете VSIX.|
|`ContentType`|Описывает тип содержимого, связанного с расширением имени файла.|

### <a name="attribute-name-attribute"></a>{Имя атрибута} Версию
 Visual Studio распознает следующие `ContentType` значения для связанных `Extension` типов.

|Расширение|ContentType|
|---------------|-----------------|
|txt|text/plain|
|pkgdef|text/plain|
|Xml|text/xml|
|vsixmanifest|text/xml|
|htm или HTML|text/html|
|RTF|приложение/RTF|
|pdf|приложение/PDF|
|GIF|image/gif|
|JPG или JPEG|Image/JPG|
|tiff|image/tiff|
|vsix|приложение/ZIP-файл|
|zip|приложение/ZIP-файл|
|Файл DLL.|application/octet-stream|
|Все прочие типы файлов|application/octet-stream|

## <a name="example"></a>Пример

### <a name="description"></a>Описание
 Следующий файл [Content_Types] .xml описывает типичный пакет VSIX.

### <a name="code"></a>Код

```
<?xml version="1.0" encoding="utf-8" ?>
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
    <Default Extension="vsixmanifest" ContentType="text/xml" />
    <Default Extension="dll" ContentType="application/octet-stream" />
    <Default Extension="png" ContentType="application/octet-stream" />
    <Default Extension="txt" ContentType="text/plain" />
    <Default Extension="pkgdef" ContentType="text/plain" />
</Types>
```

## <a name="see-also"></a>См. также
- [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Справочник по схеме расширения VSIX 1,0](/previous-versions/dd393700(v=vs.110))
- [OPC: новый стандарт для упаковки данных](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)