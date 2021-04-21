---
title: Программное добавление текста & форматирования в ячейки таблицы Word
description: Узнайте, как программным способом добавлять текст и форматировать ячейки в Microsoft Office таблицы Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 58c9e7f7d5537e4b052a732a85ad9d1c7298afa0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828401"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Руководство. Программное добавление текста и форматирования в ячейки в таблицах Word
  Каждая таблица представляет собой набор ячеек. Каждый отдельный объект <xref:Microsoft.Office.Interop.Word.Cell> представляет одну ячейку в таблице. Обращайтесь к каждой ячейке по ее расположению в таблице. Этот пример ссылается на ячейку, расположенную в первой строке и первом столбце таблицы, добавляет в ячейку текст и применяет форматирование.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>Добавление текста и форматирования в ячейки

1. Обратитесь к ячейке по ее расположению в таблице, добавьте текст в ячейку и примените форматирование.

     Следующий пример кода можно использовать в настройке на уровне документа. Чтобы использовать этот пример, запустите код из класса `ThisDocument` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet97":::

     Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet97":::

## <a name="see-also"></a>См. также статью
- [Руководство. Программное создание таблиц Word](../vsto/how-to-programmatically-create-word-tables.md)
- [Как программно добавлять строки и столбцы в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Руководство. Программное заполнение таблиц Word свойствами документа](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
