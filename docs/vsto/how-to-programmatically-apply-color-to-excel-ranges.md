---
title: Руководство. Программное применение цвета к диапазонам Excel
description: Сведения о том, как применить цвет к тексту в пределах диапазона ячеек, можно использовать элемент управления NamedRange или собственный объект диапазона Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 081985dbd4b235fe5dd8d3472d0ab574603abe1b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828323"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Руководство. Программное применение цвета к диапазонам Excel
  Чтобы применить цвет к тексту внутри диапазона ячеек, используйте <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления или собственный объект диапазона Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange
 Этот пример предназначен для настроек на уровне документа.

### <a name="to-apply-color-to-a-namedrange-control"></a>Применение цвета к элементу управления NamedRange

1. Создание <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления в ячейке a1.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet65":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet65":::

2. Задает цвет текста в <xref:Microsoft.Office.Tools.Excel.NamedRange> элементе управления.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet66":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet66":::

## <a name="use-native-excel-ranges"></a>Использовать собственные диапазоны Excel

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Применение цвета к объекту в собственном диапазоне Excel

1. Создайте диапазон в ячейке a1, а затем задайте цвет текста.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet67":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet67":::

## <a name="see-also"></a>См. также статью
- [Работа с диапазонами](../vsto/working-with-ranges.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Как программно ссылаться на диапазоны листов в коде](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
