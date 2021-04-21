---
title: Руководство. Программное перемещение листов в книгах
description: Узнайте, как программным способом изменить расположение листов относительно других листов в книге Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd05dcb39c295d4d1ebb39d933c643f61c6d921c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827296"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Руководство. Программное перемещение листов в книгах
  Вы можете программными средствами изменять положение листов относительно других листов в книге. Если не указать расположение для перемещаемого листа, Excel создает для него новую книгу.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Перемещение листа в настройке уровня документа

1. Назначьте переменной общее число листов в книге и затем переместите первый лист, чтобы он стал последним.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet24":::

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Перемещение листа в надстройке VSTO

1. Назначьте переменной общее число листов в книге и затем переместите первый лист, чтобы он стал последним.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet16":::

## <a name="see-also"></a>См. также статью
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Как программно скрыть листы](../vsto/how-to-programmatically-hide-worksheets.md)
- [Руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Как программно защитить листы](../vsto/how-to-programmatically-protect-worksheets.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
