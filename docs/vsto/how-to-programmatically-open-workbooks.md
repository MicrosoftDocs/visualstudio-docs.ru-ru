---
title: Руководство. Программное открытие книг
description: Узнайте, как можно использовать Visual Studio для программного открытия книги Microsoft Excel или работы с существующей книгой.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4dba79b1b0eea03ca3aae23e98fb93e6ef776d80
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824787"
---
# <a name="how-to-programmatically-open-workbooks"></a>Руководство. Программное открытие книг
  <xref:Microsoft.Office.Interop.Excel.Workbooks>Коллекция в Microsoft Office Excel дает возможность работать со всеми открытыми книгами и открывать книги.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Открытие существующей книги

1. Используйте <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> метод <xref:Microsoft.Office.Interop.Excel.Workbooks> коллекции, передав в нее путь к книге.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet2":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера кода требуется следующее.

- Книга с именем `YourWorkbook.xls` должна находиться в каталоге с именем `Test` на диске C.

## <a name="see-also"></a>См. также статью
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Руководство. Программное открытие текстовых файлов в виде книг](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Как создать новые книги программным способом](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Как программно сохранять книги](../vsto/how-to-programmatically-save-workbooks.md)
- [Руководство. программное закрытие книг](../vsto/how-to-programmatically-close-workbooks.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
