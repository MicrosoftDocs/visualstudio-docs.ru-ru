---
title: Пошаговое руководство. кэширование данных в документе, защищенном паролем
description: Сведения о том, что при добавлении данных в кэш данных в документе или книге, защищенной паролем, можно сохранить изменения в кэшированные данные путем переопределения двух методов в проекте.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ccdb906022d4dcfc321af294eec59afa36832773
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824189"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Пошаговое руководство. кэширование данных в документе, защищенном паролем
  При добавлении данных в кэш данных в документе или книге, защищенной паролем, изменения в кэшированных данных не сохраняются автоматически. Вы можете сохранить изменения в кэшированные данные, переопределив два метода в проекте.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Кэширование в документах Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Кэширование данных в документе Word, защищенном паролем

1. Пометьте в `ThisDocument` классе открытое поле или свойство для кэширования. Дополнительные сведения см. в разделе [кэширование данных](../vsto/caching-data.md).

2. Переопределите <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> метод в `ThisDocument` классе и удалите защиту из документа.

     При сохранении документа [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность снять защиту с документа. Это позволяет сохранять изменения в кэшированных данных.

3. Переопределите <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> метод в `ThisDocument` классе и повторно примените защиту к документу.

     После сохранения документа [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность повторно применить защиту к документу.

### <a name="example"></a>Пример
 В следующем примере кода показано, как кэшировать данные в документе Word, защищенном паролем. Перед тем как код удалит защиту в <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> методе, он сохраняет текущее <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> значение, чтобы тот же тип защиты можно было повторно применить в <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> методе.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb" id="Snippet1":::

### <a name="compile-the-code"></a>Компиляция кода
 Добавьте этот код в `ThisDocument` класс проекта. В этом коде предполагается, что пароль хранится в поле с именем `securelyStoredPassword` .

## <a name="cache-in-excel-workbooks"></a>Кэш в книгах Excel
 В проектах Excel эта процедура необходима только в том случае, если вся книга защищена паролем с помощью <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> метода. Эта процедура необязательна, если вы защищаете с помощью метода только конкретный лист с паролем <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> .

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Кэширование данных в книге Excel, защищенной паролем

1. В `ThisWorkbook` классе или в одном из классов `Sheet` *n* пометьте открытое поле или свойство для кэширования. Дополнительные сведения см. в разделе [кэширование данных](../vsto/caching-data.md).

2. Переопределите <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> метод в `ThisWorkbook` классе и удалите защиту из книги.

     При сохранении книги [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность снять защиту книги. Это позволяет сохранять изменения в кэшированных данных.

3. Переопределите <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> метод в `ThisWorkbook` классе и повторно примените защиту к документу.

     После сохранения книги [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность повторно применить защиту к книге.

### <a name="example"></a>Пример
 В следующем примере кода показано кэширование данных в книге Excel, защищенной паролем. Перед тем как код удалит защиту в <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> методе, он сохраняет текущие <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> значения и <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> , чтобы в методе можно было повторно применить тот же тип защиты <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs" id="Snippet1":::

### <a name="compile-the-code"></a>Компиляция кода
 Добавьте этот код в `ThisWorkbook` класс проекта. В этом коде предполагается, что пароль хранится в поле с именем `securelyStoredPassword` .

## <a name="see-also"></a>См. также статью
- [Кэширование данных](../vsto/caching-data.md)
- [Как кэшировать данные для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Руководство. программный кэш источника данных в документе Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
