---
title: Руководство. Программное добавление фигур в документ Visio
description: Узнайте, как добавлять фигуры в Microsoft Office документ Visio путем извлечения образцов из трафарета и удаления фигур на активной странице.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f5eabd18ac915e6cc10ff05de3d13d0263fa1eee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828414"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Руководство. Программное добавление фигур в документ Visio
  Вы можете добавлять фигуры в документ Microsoft Office Visio, извлекая образцы из набора элементов и помещая фигуры на активной странице.

 Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Documents.Add) , свойства [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) и метода [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) .

## <a name="add-shapes-to-a-visio-document"></a>Добавление фигур в документ Visio

### <a name="to-add-shapes-to-a-visio-document"></a>Добавление фигур в документ Visio

- В активном документе извлеките образцы из коллекции Documents.Masters и поместите фигуры в активный документ. Можно извлечь образец, используя индекс или имя образца.

     В следующем примере кода создается пустой документ Visio, который затем открывается с прикрепленным набором элементов **Основные фигуры** . Затем код извлекает несколько фигур и помещает их на активной странице.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>См. также статью
- [Решения Visio](../vsto/visio-solutions.md)
- [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)
- [Руководство. программное копирование и вставка фигур в документ Visio](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
