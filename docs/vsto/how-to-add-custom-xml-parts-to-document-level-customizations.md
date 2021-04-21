---
title: Как добавить пользовательские XML-части в настройки уровня документа
description: Сведения о хранении XML-данных в книге Microsoft Office Excel или Microsoft Office документе Word путем создания пользовательской XML-части в настройке на уровне документа.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 99374a2daded3c4b49b60053a69cd1ff7c4dffe8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827699"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Как добавить пользовательские XML-части в настройки уровня документа
  XML-данные можно сохранять в книге Microsoft Office Excel или документе Microsoft Office Word путем создания настраиваемой XML-части в настройке на уровне документа. Дополнительные сведения см. в разделе [Общие сведения о пользовательских XML-частях](../vsto/custom-xml-parts-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio не предоставляет проекты уровня документа для Microsoft Office PowerPoint. Дополнительные сведения о добавлении пользовательской XML-части в презентацию PowerPoint с помощью надстройки VSTO см. в разделе [как добавить пользовательские XML-части в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Добавление пользовательской XML-части в книгу Excel

1. Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Core.CustomXMLParts> в книге. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML-строку, которую требуется сохранить в книге.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb" id="Snippet1":::

2. Добавьте метод `AddCustomXmlPartToWorkbook` в класс `ThisWorkbook` в проекте уровня документа для Excel.

3. Вызовите метод из другого кода в проекте. Например, для создания настраиваемой XML-части, когда пользователь открывает книгу, вызовите метод из обработчика событий `ThisWorkbook_Startup` .

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Добавление пользовательской XML-части в документ Word

1. Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Core.CustomXMLParts> в документе. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML-строку, которую требуется сохранить в документе.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs" id="Snippet1":::

2. Добавьте метод `AddCustomXmlPartToDocument` в класс `ThisDocument` в проекте уровня документа для Word.

3. Вызовите метод из другого кода в проекте. Например, для создания настраиваемой XML-части, когда пользователь открывает документ, вызовите метод из обработчика событий `ThisDocument_Startup` .

## <a name="robust-programming"></a>Отказоустойчивость
 Для простоты в этом примере используется XML-строка, которая определена как локальная переменная в методе. Обычно следует получать XML из внешнего источника, например файла или базы данных.

## <a name="see-also"></a>См. также статью
- [Общие сведения о пользовательских XML-частях](../vsto/custom-xml-parts-overview.md)
- [Инструкции. Добавление пользовательских XML-частей в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
