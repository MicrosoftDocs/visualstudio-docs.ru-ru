---
title: Руководство. Программная печать документов Visio
description: Сведения о том, как распечатать полный документ Microsoft Visio или напечатать только определенную страницу в этом документе.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 13e18b1d1e20c836be740a6b44a591be6df6e926
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827192"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Руководство. Программная печать документов Visio
  Можно напечатать полный документ Microsoft Office Visio или только определенную страницу.

 Подробные сведения о методах печати см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) и метода [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) .

## <a name="print-a-visio-document"></a>Печать документа Visio

### <a name="to-print-a-complete-document"></a>Печать всего документа

- Вызовите метод `Microsoft.Office.Interop.Visio.Document.Print` документа `Microsoft.Office.Interop.Visio.Document` , который требуется напечатать.

     В следующем примере кода печатается активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet8":::

## <a name="print-a-page-of-a-visio-document"></a>Печать страницы документа Visio

### <a name="to-print-a-page-of-a-document"></a>Печать страницы документа

- Вызовите метод `Microsoft.Office.Interop.Visio.Pages.Print` документа `Microsoft.Office.Interop.Visio.Pages` , который требуется напечатать.

     В следующем примере кода печатается первая страница активного документа. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>См. также статью
- [Решения Visio](../vsto/visio-solutions.md)
- [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Как программно создавать новые документы Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Руководство. Программное открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Руководство. программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Как программно сохранять документы Visio](../vsto/how-to-programmatically-save-visio-documents.md)
