---
title: Руководство. Программная защита книг
description: Узнайте, как защитить книгу Microsoft Excel, чтобы пользователи не могли добавлять или удалять листы, а также программно снимать защиту книги.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f0b479c56be6da7b14f87263c8c01d66910ac20
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827114"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Руководство. Программная защита книг
  Можно защитить книгу Excel Microsoft Office, чтобы пользователи не могли добавлять или удалять листы, а также программно снимать защиту книги. При необходимости можно указать пароль, указать, должна ли быть защищена структура (так что пользователи не смогут перемещать листы), и указать, должна ли быть защищена Windows книги.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Защита книги не останавливает редактирование ячеек пользователями. Чтобы защитить данные, необходимо защитить листы. Дополнительные сведения см. [в разделе руководство. Программная защита листов](../vsto/how-to-programmatically-protect-worksheets.md).

 В следующих примерах кода используется переменная, которая содержит пароль, полученный от пользователя.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Защита книги, которая является частью настройки уровня документа

### <a name="to-protect-a-workbook"></a>Защита книги

1. Вызовите <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> метод книги и включите пароль. Чтобы использовать следующий пример кода, запустите его в `ThisWorkbook` классе, а не в классе листа.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet10":::

### <a name="to-unprotect-a-workbook"></a>Снятие защиты с книги

1. Вызовите <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> метод, передав пароль, если он требуется. Чтобы использовать следующий пример кода, запустите его в `ThisWorkbook` классе, а не в классе листа.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet11":::

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Защита книги с помощью надстройки уровня приложения

### <a name="to-protect-a-workbook"></a>Защита книги

1. Вызовите <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> метод книги и включите пароль. В этом примере кода используется активная книга. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet6":::

### <a name="to-unprotect-a-workbook"></a>Снятие защиты с книги

1. Вызовите <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> метод активной книги, передав пароль, если он требуется. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>См. также статью
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Как программно защитить листы](../vsto/how-to-programmatically-protect-worksheets.md)
- [Как программно скрыть листы](../vsto/how-to-programmatically-hide-worksheets.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
