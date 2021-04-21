---
title: Руководство. программное закрытие книг
description: Узнайте, как можно закрыть активную книгу или указать книгу для закрытия программным способом.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d09cbff06b1bb7048316629b7b958ee299029ec8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825268"
---
# <a name="how-to-programmatically-close-workbooks"></a>Руководство. программное закрытие книг
  Можно закрыть активную книгу или указать, какую книгу следует закрыть.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Закрытие активной книги
 Для закрытия активной книги можно использовать две процедуры: одну для настроек на уровне документа и одну для надстроек VSTO.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Закрытие активной книги в настройке на уровне документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> , чтобы закрыть книгу, связанную с настройкой. Чтобы использовать следующий пример кода, запустите его в классе `Sheet1` в проекте уровня документа для Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet3":::

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Закрытие активной книги в надстройке VSTO

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> , чтобы закрыть активную книгу. Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Excel.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet1":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="close-a-workbook-that-you-specify-by-name"></a>Закрытие книги, указанной с помощью имени
 Процедура закрытия книги с заданным именем идентична процедуре для надстройки VSTO и настроек на уровне документа.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Закрытие книги, указанной по имени

1. Укажите имя книги в качестве аргумента коллекции <xref:Microsoft.Office.Interop.Excel.Workbooks> . В следующем примере кода предполагается, что в Excel открыта книга с именем **NewWorkbook** .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="see-also"></a>См. также статью
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Как программно сохранять книги](../vsto/how-to-programmatically-save-workbooks.md)
- [Руководство. Программное открытие книг](../vsto/how-to-programmatically-open-workbooks.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
