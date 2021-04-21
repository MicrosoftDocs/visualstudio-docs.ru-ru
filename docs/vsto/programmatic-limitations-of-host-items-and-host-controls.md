---
title: Программные ограничения ведущих элементов и элементов управления ведущего приложения
description: Изучите фундаментальные различия между поведением ведущих элементов и элементов управления ведущего приложения и собственными объектами Office во время выполнения.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 463543a40ac9443959b06cf9f65dad4c99c52ee3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828830"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Программные ограничения ведущих элементов и элементов управления ведущего приложения
  Каждый ведущий элемент и элемент управления ведущего приложения создается, чтобы работать аналогично собственному объекту Microsoft Office Word или Microsoft Office Excel с дополнительными функциями. Но есть ряд фундаментальных различий между поведением во время выполнения ведущих элементов и элементов управления ведущего приложения с одной стороны и собственных объектов Office с другой стороны.

 Общие сведения о ведущих элементах и элементах управления ведущего приложения см. в разделе Общие сведения о ведущих элементах [и элементах управления узла](../vsto/host-items-and-host-controls-overview.md).

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>Программное создание ведущих элементов
 При программном создании или открытии документа, книги или листа во время выполнения с использованием объектной модели Word или Excel элемент не является ведущим. Вместо этого новый объект является собственным объектом Office. Например, при использовании метода <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> для создания документа Word во время выполнения он будет собственным объектом <xref:Microsoft.Office.Interop.Word.Document> , а не ведущим элементом <xref:Microsoft.Office.Tools.Word.Document> . Аналогично, при создании листа с помощью метода <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> во время выполнения вы получаете собственный объект <xref:Microsoft.Office.Interop.Excel.Worksheet> , а не ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> .

 В проектах уровня документа нельзя создавать ведущие элементы во время выполнения. Ведущие элементы можно создавать в проектах уровня документа только во время разработки. Дополнительные сведения см. в статьях [ведущий элемент документа](../vsto/document-host-item.md), [ведущий элемент книги](../vsto/workbook-host-item.md)и [ведущий элемент листа](../vsto/worksheet-host-item.md).

 В проектах надстроек VSTO можно создавать ведущие элементы <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>и <xref:Microsoft.Office.Tools.Excel.Worksheet> во время выполнения. Дополнительные сведения см. [в разделе Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="programmatically-create-host-controls"></a>Создание элементов управления ведущего приложения программными средствами
 Во время выполнения можно программными средствами добавлять элементы управления ведущего приложения в ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> или <xref:Microsoft.Office.Tools.Excel.Worksheet> . Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Нельзя добавлять элементы управления ведущего приложения в собственный объект <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Worksheet>.

> [!NOTE]
> Следующие элементы управления ведущего приложения нельзя добавлять программными средствами в листы и документы: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>и <xref:Microsoft.Office.Tools.Word.XMLNodes>.

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Общие сведения о различиях между ведущими элементами, элементами управления ведущего приложения и собственными объектами Office
 Для каждого ведущего элемента и элемента управления ведущего приложения существует собственный объект Microsoft Office Word или Microsoft Office Excel. Доступ к базовому объекту можно получить с помощью свойства Иннеробжект ведущего элемента или элемента управления ведущего приложения. Однако невозможно привести собственный объект Office к соответствующему ведущему элементу или элементу управления ведущего приложения. При попытке привести собственный объект Office к типу ведущего элемента или элемента управления ведущего приложения возникает исключение <xref:System.InvalidCastException> .

 Существует несколько сценариев, в которых различия между типами ведущих элементов, элементов управления ведущего приложения и базовых собственных объектов Office могут повлиять на код.

### <a name="pass-host-controls-to-methods-and-properties"></a>Передача элементов управления ведущего приложения в методы и свойства
 В приложении Word невозможно передать элемент управления ведущего приложения в метод или свойство, для которого требуется собственный объект Word в качестве параметра. Для возврата базового объекта Word необходимо использовать свойство Иннеробжект элемента управления ведущего приложения. Например, можно передать объект <xref:Microsoft.Office.Interop.Word.Bookmark> в метод путем передачи в метод свойства <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark> .

 В Excel необходимо использовать свойство Иннеробжект элемента управления ведущего приложения, чтобы передать элемент управления ведущего приложения методу или свойству, если метод или свойство предполагает наличие базового объекта Excel.

 В приведенном ниже примере создается элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> , который затем передается в метод <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> . Код использует свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> именованного диапазона для возврата базового объекта <xref:Microsoft.Office.Interop.Excel.Range> Office, требующегося для метода <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet28":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet28":::

### <a name="return-types-of-native-office-methods-and-properties"></a>Типы возвращаемых данных собственных методов и свойств Office
 Большинство методов и свойств ведущих элементов возвращают собственные объекты Office, на которых основаны ведущие элементы. Например, свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.NamedRange> в Excel возвращает объект <xref:Microsoft.Office.Interop.Excel.Worksheet> , а не ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> . Аналогично, свойство <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в Word возвращает объект <xref:Microsoft.Office.Interop.Word.Document> , а не ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> .

### <a name="access-collections-of-host-controls"></a>Доступ к коллекциям элементов управления ведущего приложения
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] не предоставляет отдельных коллекций для каждого типа элементов управления ведущего приложения. Вместо этого используйте свойство Controls ведущего элемента для перебора всех управляемых элементов управления (как элементов управления ведущего приложения, так и элементов управления Windows Forms) в документе или листе, а затем найдите элементы, соответствующие типу интересующего вас элемента управления ведущего приложения. В примере кода ниже рассматривается каждый элемент управления в документе Word и определяется, является ли он <xref:Microsoft.Office.Tools.Word.Bookmark>.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet10":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet10":::

 Дополнительные сведения о свойстве элементов управления ведущего элемента см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Объектные модели Word и Excel включают свойства, которые предоставляют коллекции собственных элементов управления для документов и листов. С помощью этих свойств нельзя получить доступ к управляемым элементам управления. Например, невозможно перечислить каждый элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark> в документе с помощью свойства <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> объекта <xref:Microsoft.Office.Interop.Word.Document> или свойства <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> объекта <xref:Microsoft.Office.Tools.Word.Document>. Эти свойства включают в документ только элементы управления <xref:Microsoft.Office.Interop.Word.Bookmark> ; они не включают в документ элементы управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark> .

## <a name="see-also"></a>См. также статью
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Ведущий элемент листа](../vsto/worksheet-host-item.md)
- [Ведущий элемент книги](../vsto/workbook-host-item.md)
- [Ведущий элемент документа](../vsto/document-host-item.md)
