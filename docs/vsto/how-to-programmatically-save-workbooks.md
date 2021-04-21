---
title: Как программно сохранять книги
description: Программное сохранение книг Microsoft Excel без изменения пути и сохранение копии книги без изменения открытой книги в памяти.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4559d098a80a1dfd8f1d3f5c2c21cbebc992fcb7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828986"
---
# <a name="how-to-programmatically-save-workbooks"></a>Как программно сохранять книги
  Сохранить книгу можно несколькими способами. Можно сохранить книгу без изменения пути к файлу. Если книга не сохранялась ранее, следует сохранить книгу, указав путь. Без явного пути Microsoft Office Excel сохраняет файл в текущей папке с именем, заданным при его создании. Можно также сохранить копию книги, не изменяя открытую книгу в памяти.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>Сохранение книги без изменения пути

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Сохранение книги, связанной с настройкой на уровне документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> класса `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet4":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Сохранение активной книги в надстройке VSTO

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A>, чтобы сохранить активную книгу. Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="save-a-workbook-with-a-new-path"></a>Сохранение книги с новым путем
 Вы можете сохранить указанную книгу в новой папке или с новым именем, указав при необходимости формат файла, пароль, режим доступа и т. д.

> [!NOTE]
> Может потребоваться установить <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> свойство в **значение false** перед сохранением книги с новым путем, так как сохранение в некоторых форматах требует взаимодействия. Установка этого свойства в **значение false** приводит к тому, что Excel будет использовать все значения по умолчанию.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Сохранение книги, связанной с настройкой на уровне документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> класса `ThisWorkbook` . Чтобы использовать следующий пример кода, запустите его из класса `ThisWorkbook`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet5":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Сохранение активной книги в надстройке VSTO

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A>, чтобы сохранить активную книгу с новым путем. Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="save-a-copy-of-the-workbook"></a>Сохранение копии книги
 Вы можете также сохранить копию книги в файл, не изменяя открытую книгу в памяти. Это полезно, если вам нужно создать резервную копию без изменения местоположения книги.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Сохранение книги, связанной с настройкой на уровне документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> класса `ThisWorkbook` . Чтобы использовать следующий пример кода, запустите его из класса `ThisWorkbook`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet6":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Сохранение активной книги в надстройке VSTO

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A>, чтобы сохранить копию активной книги. Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="robust-programming"></a>Отказоустойчивость
 Интерактивная отмена любых методов, которые сохраняют или копируют книгу, вызывает ошибку времени выполнения в коде. Например, если процедура вызывает <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> метод, но не отключает запросы из Excel, и пользователь нажимает кнопку **Отмена** при появлении запроса, Excel вызывает ошибку времени выполнения.

## <a name="see-also"></a>См. также статью
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Ведущий элемент книги](../vsto/workbook-host-item.md)
- [Руководство. программное закрытие книг](../vsto/how-to-programmatically-close-workbooks.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
