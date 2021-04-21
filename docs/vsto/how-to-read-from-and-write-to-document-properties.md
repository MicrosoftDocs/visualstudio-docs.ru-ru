---
title: Руководство. чтение и запись в свойства документа
description: Узнайте, как можно использовать Visual Studio для получения или задания свойств документа в Microsoft Excel и Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3474d86a7408e841d383c82e5ab38da90253dbbf
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826685"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Руководство. чтение и запись в свойства документа
  Свойства документа можно сохранять вместе с документом. Приложения Office содержат различные встроенные свойства, например автора, название и тему. В этом разделе показано, как задать свойства документа в Microsoft Office Excel и Microsoft Office Word.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Задание свойств документа в Excel
 Для работы со встроенными свойствами в Excel используйте следующие свойства.

- В проекте на уровне документа используйте свойство <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> класса `ThisWorkbook` .

- В проекте надстройки VSTO используйте свойство <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> объекта <xref:Microsoft.Office.Interop.Excel.Workbook> .

  Эти свойства возвращают объект <xref:Microsoft.Office.Core.DocumentProperties> , который представляет собой коллекцию объектов <xref:Microsoft.Office.Core.DocumentProperty> . Для извлечения конкретного свойства по имени или по индексу в коллекции можно использовать свойство `Item` коллекции.

  В следующем примере кода показано, как изменить встроенное свойство **Revision Number** в проекте на уровне документа.

### <a name="to-change-the-revision-number-property-in-excel"></a>Изменение свойства «Номер редакции» в Excel

1. Назначьте переменной встроенные свойства документа.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet7":::

2. Увеличьте значение свойства `Revision Number` на единицу.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet8":::

## <a name="set-document-properties-in-word"></a>Задание свойств документа в Word
 Для работы со встроенными свойствами в Word используйте следующие свойства.

- В проекте на уровне документа используйте свойство <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> класса `ThisDocument` .

- В проекте надстройки VSTO используйте свойство <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> объекта <xref:Microsoft.Office.Interop.Word.Document> .

  Эти свойства возвращают объект <xref:Microsoft.Office.Core.DocumentProperties> , который представляет собой коллекцию объектов <xref:Microsoft.Office.Core.DocumentProperty> . Для извлечения конкретного свойства по имени или по индексу в коллекции можно использовать свойство `Item` коллекции.

  В следующем примере кода показано, как изменить встроенное свойство **Subject** в проекте на уровне документа.

### <a name="to-change-the-subject-property"></a>Изменение свойства темы

1. Назначьте переменной встроенные свойства документа.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet1":::

2. Измените значение свойства `Subject` на «Техническая документация».

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet2":::

## <a name="robust-programming"></a>Отказоустойчивость
 В примерах предполагается, что код написан в классе `ThisWorkbook` в проекте на уровне документа для Excel и в классе `ThisDocument` в проекте на уровне документа для Word.

 Несмотря на то что вы работаете с Word и Excel и их объектами, Microsoft Office предоставляет список доступных встроенных свойств документа. В случае попытки доступа к неопределенному свойству возникает исключение.

## <a name="see-also"></a>См. также статью
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)
- [Как создавать и изменять пользовательские свойства документа](../vsto/how-to-create-and-modify-custom-document-properties.md)
