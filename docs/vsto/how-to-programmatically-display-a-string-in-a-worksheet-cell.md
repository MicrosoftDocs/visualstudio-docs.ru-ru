---
title: Руководство. программное отображение строки в ячейке листа
description: Сведения о программном отображении строки в ячейке листа Microsoft Excel с помощью элемента управления NamedRange или собственного объекта диапазона Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8a7bc48df6e30381ff275b9f11dabe04a25d6dd7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825931"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Руководство. программное отображение строки в ячейке листа
  В этом примере показано, как программным способом отобразить текст в ячейке. Чтобы отобразить текст в ячейке, используйте либо <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления, либо собственный объект диапазона Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange
 В этом примере используется <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления с именем `message` . Элемент управления должен быть добавлен в настройку на уровне документа во время разработки. Следующий код должен быть помещен в класс листа, а не в `ThisWorkbook` класс.

### <a name="to-display-text-in-a-namedrange-control"></a>Отображение текста в элементе управления NamedRange

1. Присвойте <xref:Microsoft.Office.Tools.Excel.NamedRange> элементу управления значение **Hello World**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet68":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet68":::

## <a name="use-a-native-excel-range"></a>Использовать собственный диапазон Excel
 Следующий код создает новый диапазон программным способом, а затем присваивает ему значение.

### <a name="to-display-text-in-an-excel-range"></a>Отображение текста в диапазоне Excel

1. Получите диапазон в ячейке **a1** `Sheet1` и задайте для него значение **Hello World**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet69":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet69":::

## <a name="see-also"></a>См. также статью
- [Пошаговое руководство. получение данных с помощью формы Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Устранение неполадок решений Office](../vsto/troubleshooting-office-solutions.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
