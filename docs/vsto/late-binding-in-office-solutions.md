---
title: Позднее связывание в решениях Office
description: Узнайте, как некоторые типы в объектных моделях в Microsoft Office приложениях предоставляют функциональные возможности, доступные с помощью функций позднего связывания.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e618dcd0cc699b4626f825890cf0fc8bd7ddd853
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823890"
---
# <a name="late-binding-in-office-solutions"></a>Позднее связывание в решениях Office
  Некоторые типы в объектных моделях приложений Office предоставляют функциональные возможности, доступные с помощью функций позднего связывания. Например, некоторые методы и свойства могут возвращать различные типы объектов в зависимости от контекста приложения Office, а некоторые типы могут предоставлять различные методы или свойства в разных контекстах.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic проекты, в которых **параметр optioned** имеет значение OFF, а проекты Visual C#, предназначенные для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или, [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] могут работать непосредственно с типами, которые используют эти функции позднего связывания.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Неявное и явное приведение возвращаемых значений объекта
 Многие методы и свойства в Microsoft Office основных сборках взаимодействия (PIA) возвращают <xref:System.Object> значения, так как они могут возвращать несколько различных типов объектов. Например, <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> свойство возвращает, <xref:System.Object> так как его возвращаемое значение может быть <xref:Microsoft.Office.Interop.Excel.Worksheet> объектом или <xref:Microsoft.Office.Interop.Excel.Chart> , в зависимости от того, что является активным листом.

 Если метод или свойство возвращает <xref:System.Object> , необходимо явно преобразовать (в Visual Basic) объект в правильный тип в Visual Basic проектах, где **параметр Option-on** имеет значение ON. Нет необходимости явно приводить <xref:System.Object> возвращаемые значения в проектах Visual Basic, где **параметр optioned** имеет значение OFF.

 В большинстве случаев справочная документация содержит список возможных типов возвращаемого значения для элемента, который возвращает <xref:System.Object> . Преобразование или приведение объекта позволяет IntelliSense для объекта в редакторе кода.

 Сведения о преобразовании в Visual Basic см. в разделе явные и неявные [преобразования &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) и [CType Function &#40;](/dotnet/visual-basic/language-reference/functions/ctype-function)Visual Basic.

### <a name="examples"></a>Примеры
 В следующем примере кода показано, как привести объект к конкретному типу в проекте Visual Basic, где **параметр Option-on** имеет значение ON. В проекте этого типа необходимо явным образом привести <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> свойство к типу <xref:Microsoft.Office.Interop.Excel.Range> . Для этого примера требуется проект Excel уровня документа с классом листа с именем `Sheet1` .

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet9":::

 В следующем примере кода показано, как неявно привести объект к конкретному типу в Visual Basic проекте, где **параметр Option строго** имеет значение OFF, или в проекте Visual C#, предназначенном для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . В проектах этих типов <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> свойство неявно приводится к типу <xref:Microsoft.Office.Interop.Excel.Range> . Для этого примера требуется проект Excel уровня документа с классом листа с именем `Sheet1` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet10":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="access-members-that-are-available-only-through-late-binding"></a>Доступ к членам, доступным только через позднее связывание
 Некоторые свойства и методы в основных сборках взаимодействия Office доступны только через позднее связывание. В Visual Basic проектах, где **параметр optioned** имеет значение OFF или в проектах Visual C#, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , можно использовать функции позднего связывания на этих языках для доступа к элементам с поздним связыванием. Для доступа к этим членам в Visual Basic проектах, где **параметр Option-on** имеет значение ON, необходимо использовать отражение.

### <a name="examples"></a>Примеры
 В следующем примере кода показано, как получить доступ к элементам с поздним связыванием в проекте Visual Basic, где **параметр optioned** имеет значение OFF, или в проекте Visual C#, предназначенном для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . В этом примере осуществляется доступ к свойству **имени** с поздним связыванием диалогового окна **открытия файла** в Word. Чтобы использовать этот пример, запустите его из `ThisDocument` класса или `ThisAddIn` в проекте Word.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 В следующем примере кода показано, как использовать отражение для выполнения той же задачи в проекте Visual Basic, где **параметр Option-on** имеет значение ON.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>См. также статью
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Использование инструкции по программированию типа Dynamic &#40;C&#35;&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Оператор Option Case](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Отражение (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Отражение (Visual Basic))
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
