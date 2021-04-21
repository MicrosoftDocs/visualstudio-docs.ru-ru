---
title: Как программным способом восстановить выделенные элементы после поиска
description: Узнайте, как можно использовать Visual Studio для программного восстановления параметров после поиска в документе Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2a9f804e218ec9dfa0e0550501dec0c1aa8388ff
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824020"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Как программным способом восстановить выделенные элементы после поиска
  При поиске и замене текста в документе может потребоваться восстановить исходный фрагмент пользователя после завершения поиска.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Код в примере процедуры использует два <xref:Microsoft.Office.Interop.Word.Range> объекта. В одном из них хранится текущее значение <xref:Microsoft.Office.Interop.Word.Selection> , а в качестве диапазона поиска используется весь документ.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>Восстановление исходного фрагмента пользователя после поиска

1. Создание <xref:Microsoft.Office.Interop.Word.Range> объектов для документа и текущего выделения.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet83":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet83":::

2. Выполните операцию поиска и замены.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet84":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet84":::

3. Выберите начальный диапазон для восстановления исходного выбора пользователя.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet85":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet85":::

   В следующем примере показан полный метод.

## <a name="example"></a>Пример
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet82":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet82":::

## <a name="see-also"></a>См. также
- [Руководство. Программный поиск и замена текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Как программно задать параметры поиска в Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Пошаговое руководство. Программный перебор найденных элементов в документах](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
