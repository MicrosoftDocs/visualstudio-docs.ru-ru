---
title: Руководство. Программное применение стилей к диапазонам в книгах
description: Узнайте, как применять именованные стили к регионам в книгах. В Excel реализовано несколько предварительно определенных стилей.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1ce30c9a0e21bd4b8860f7a4d17191c48cd2ad9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828310"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Руководство. Программное применение стилей к диапазонам в книгах
  К областям в книгах можно применять именованные стили. В Excel реализовано несколько предварительно определенных стилей.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 В диалоговом окне **Формат ячеек** отображаются все параметры, которые можно использовать для форматирования ячеек, причем каждый такой параметр доступен из кода. Для отображения этого диалогового окна в Excel щелкните пункт **Ячейки** в меню **Формат** .

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Применение стиля к именованному диапазону в настройке на уровне документа

1. Создайте новый стиль и задайте его атрибуты.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet53":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet53":::

2. Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange>, назначьте ему текст, а затем примените новый стиль. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet54":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet54":::

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Удаление стиля из именованного диапазона в настройке на уровне документа

1. Примените к диапазону стиль «Обычный». Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet55":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet55":::

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Применение стиля к именованному диапазону в надстройке VSTO

1. Создайте новый стиль и задайте его атрибуты.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet28":::

2. Создайте <xref:Microsoft.Office.Interop.Excel.Range>, назначьте ему текст, а затем примените новый стиль.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet29":::

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Очистка стиля из именованного диапазона в надстройке VSTO

1. Примените к диапазону стиль «Обычный».

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet56":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet56":::

## <a name="see-also"></a>См. также статью
- [Работа с диапазонами](../vsto/working-with-ranges.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
