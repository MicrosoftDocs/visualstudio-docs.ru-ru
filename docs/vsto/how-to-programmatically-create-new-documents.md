---
title: Руководство. Программное создание новых документов
description: Узнайте, как программным способом создавать новые документы в Microsoft Word с помощью Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e9ff98654da8d7125ecf788fadc9cbf7ff4bdfc7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964073"
---
# <a name="how-to-programmatically-create-new-documents"></a>Руководство. Программное создание новых документов
  При создании документа программным образом новый документ является собственным объектом <xref:Microsoft.Office.Interop.Word.Document>. Этот объект не имеет дополнительных событий и возможностей привязки данных, которые имеет ведущий элемент <xref:Microsoft.Office.Tools.Word.Document>. Дополнительные сведения см. в разделе [программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 При разработке проекта на уровне документа добавлять ведущие элементы <xref:Microsoft.Office.Tools.Word.Document> в проект программным образом нельзя. В проекте надстройки VSTO любой объект <xref:Microsoft.Office.Interop.Word.Document> можно преобразовать в ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> во время выполнения. Дополнительные сведения см. [в разделе Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Создание нового документа на основе шаблона «Обычный»

- Для создания нового документа на основе шаблона «Обычный» используйте метод <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> коллекции <xref:Microsoft.Office.Interop.Word.Documents>. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]

## <a name="use-custom-templates"></a>Использование настраиваемых шаблонов
 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A>Метод имеет необязательный аргумент *шаблона* для создания нового документа на основе шаблона, отличного от обычного шаблона. Необходимо указать имя файла и полный путь к шаблону.

### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Создание нового документа на основе пользовательского шаблона

- Вызовите метод <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> коллекции <xref:Microsoft.Office.Interop.Word.Documents> и укажите путь к шаблону. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]

## <a name="see-also"></a>См. также раздел
- [Руководство. Программное открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
