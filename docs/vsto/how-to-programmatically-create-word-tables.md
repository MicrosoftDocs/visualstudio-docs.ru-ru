---
title: Руководство. Программное создание таблиц Word
description: Узнайте, как использовать метод Add коллекции Tables для добавления таблицы в указанный диапазон документа Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5651487e280d7fb9912734b919b00fab28a702db
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827387"
---
# <a name="how-to-programmatically-create-word-tables"></a>Руководство. Программное создание таблиц Word
  Коллекция <xref:Microsoft.Office.Interop.Word.Tables> является членом классов <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> и <xref:Microsoft.Office.Interop.Word.Range>. Это означает, что таблицу можно создать в любом из их контекстов. Для добавления таблицы в указанном диапазоне можно использовать метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> коллекции <xref:Microsoft.Office.Interop.Word.Tables>.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="create-tables-in-document-level-customizations"></a>Создание таблиц в настройках уровня документа

### <a name="to-add-a-table-to-a-document"></a>Добавление таблицы в документ

- Для добавления таблицы, состоящей из трех строк и четырех столбцов, в начало документа используйте метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>.

   Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet86":::

  При создании таблицы она автоматически добавляется в коллекцию <xref:Microsoft.Office.Interop.Word.Tables> ведущего элемента <xref:Microsoft.Office.Tools.Word.Document>. Затем на таблицу можно ссылаться по номеру ее элемента с помощью свойства <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, как показано в следующем коде.

### <a name="to-refer-to-a-table-by-item-number"></a>Ссылка на таблицу по номеру элемента

1. Используйте свойство <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> и укажите номер элемента таблицы, на которую необходимо ссылаться.

    Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet87":::

   Каждый объект <xref:Microsoft.Office.Interop.Word.Table> также имеет свойство <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, которое позволяет настроить атрибуты форматирования.

### <a name="to-apply-a-style-to-a-table"></a>Применение стиля к таблице

1. Для применения одного из встроенных стилей Word к таблице используйте свойство <xref:Microsoft.Office.Interop.Word.Table.Style%2A>.

     Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet88":::

## <a name="create-tables-in-vsto-add-ins"></a>Создание таблиц в надстройках VSTO

### <a name="to-add-a-table-to-a-document"></a>Добавление таблицы в документ

- Для добавления таблицы, состоящей из трех строк и четырех столбцов, в начало документа используйте метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>.

   Следующий пример кода добавляет таблицу в активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet86":::

  При создании таблицы она автоматически добавляется в коллекцию <xref:Microsoft.Office.Interop.Word.Tables> в <xref:Microsoft.Office.Interop.Word.Document>. Затем на таблицу можно ссылаться по номеру ее элемента с помощью свойства <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, как показано в следующем коде.

### <a name="to-refer-to-a-table-by-item-number"></a>Ссылка на таблицу по номеру элемента

1. Используйте свойство <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> и укажите номер элемента таблицы, на которую необходимо ссылаться.

    В следующем примере кода используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet87":::

   Каждый объект <xref:Microsoft.Office.Interop.Word.Table> также имеет свойство <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, которое позволяет настроить атрибуты форматирования.

### <a name="to-apply-a-style-to-a-table"></a>Применение стиля к таблице

1. Для применения одного из встроенных стилей Word к таблице используйте свойство <xref:Microsoft.Office.Interop.Word.Table.Style%2A>.

     В следующем примере кода используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet88":::

## <a name="see-also"></a>См. также статью
- [Руководство. Программное добавление текста и форматирования в ячейки в таблицах Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Как программно добавлять строки и столбцы в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Руководство. Программное заполнение таблиц Word свойствами документа](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
