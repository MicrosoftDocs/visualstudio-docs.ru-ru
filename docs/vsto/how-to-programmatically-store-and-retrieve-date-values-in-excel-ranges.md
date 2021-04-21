---
title: Хранение & получение значений дат в диапазонах Excel программными средствами
description: Узнайте, как использовать Visual Studio для программного хранения и извлечения значений дат в диапазонах Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6e3115e00147a5dff850f6e0c051ffc3b6733218
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826243"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Как программно сохранять и извлекать значения дат в диапазонах Excel
  Можно сохранять и извлекать значения в <xref:Microsoft.Office.Tools.Excel.NamedRange> элементе управления или в собственном объекте Excel Range.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Если вы храните значение даты, которое попадает в диапазон или после 1/1/1900 в диапазоне с помощью средств разработки Office в Visual Studio, оно сохраняется в формате OLE Automation (OA). <xref:System.DateTime.FromOADate%2A>Для получения значений дат OLE-автоматизации (OA) необходимо использовать метод. Если дата более ранняя, чем 1/1/1900, она сохраняется в виде строки.

> [!NOTE]
> Даты Excel отличаются от дат OLE Automation на первые два месяца 1900. Существуют также различия, если установлен параметр **системы даты 1904** . Приведенные ниже примеры кода не устраняют эти различия.

## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange

- Этот пример предназначен для настроек на уровне документа. Следующий код должен быть помещен в класс листа, а не в `ThisWorkbook` класс.

### <a name="to-store-a-date-value-in-a-named-range"></a>Сохранение значения даты в именованном диапазоне

1. Создание <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления в ячейке **a1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet50":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet50":::

2. Установите сегодняшнюю дату в качестве значения параметра `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet51":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet51":::

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Получение значения даты из именованного диапазона

1. Получите значение даты из `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet52":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet52":::

## <a name="use-native-excel-ranges"></a>Использовать собственные диапазоны Excel

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Сохранение значения даты в собственном объекте Excel Range

1. Создайте объект <xref:Microsoft.Office.Interop.Excel.Range> , представляющий ячейку **a1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet25":::

2. Установите сегодняшнюю дату в качестве значения параметра `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet26":::

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Получение значения даты из собственного объекта диапазона Excel

1. Получите значение даты из `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet27":::

## <a name="see-also"></a>См. также статью
- [Работа с диапазонами](../vsto/working-with-ranges.md)
- [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Как программно ссылаться на диапазоны листов в коде](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Как добавить элементы управления NamedRange в листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
