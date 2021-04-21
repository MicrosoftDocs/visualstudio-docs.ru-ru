---
title: Как программно задать параметры поиска в Word
description: Узнайте, как использовать Visual Studio для программного задания параметров поиска для выбора в Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 605f782bf6dc3bb56b52bdcd896d1c6419cf5f51
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825034"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Как программно задать параметры поиска в Word
  Существует два способа задать параметры поиска для выбора в Microsoft Office документах Word:

- Задание отдельных свойств <xref:Microsoft.Office.Interop.Word.Find> объекта.

- Используйте аргументы <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метода <xref:Microsoft.Office.Interop.Word.Find> объекта.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Использование свойств объекта Find
 Следующий код задает свойства <xref:Microsoft.Office.Interop.Word.Find> объекта для поиска текста в текущем выделенном фрагменте. Обратите внимание, что условия поиска, например поиск вперед, перенос по словам и текст для поиска, являются свойствами <xref:Microsoft.Office.Interop.Word.Find> объекта.

 Установка каждого свойства <xref:Microsoft.Office.Interop.Word.Find> объекта не полезна при написании кода C#, поскольку необходимо указать те же свойства, что и параметры в <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> методе. Поэтому этот пример содержит только Visual Basic код.

### <a name="to-set-search-options-using-a-find-object"></a>Задание параметров поиска с помощью объекта Find

1. Задайте свойства <xref:Microsoft.Office.Interop.Word.Find> объекта для поиска в прямом направлении по выделенному тексту. 

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet76":::

## <a name="use-execute-method-arguments"></a>Использование аргументов метода Execute
 В следующем коде <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метод <xref:Microsoft.Office.Interop.Word.Find> объекта используется для поиска текста в текущем выделенном фрагменте. Обратите внимание, что условия поиска, например поиск вперед, перенос по словам и текст для поиска, передаются как параметры <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метода.

### <a name="to-set-search-options-using-execute-method-arguments"></a>Задание параметров поиска с помощью аргументов метода Execute

1. Передайте критерии поиска в качестве параметров <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метода, чтобы выполнить поиск вперед по выделенному тексту. 

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet77":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet77":::

## <a name="see-also"></a>См. также статью
- [Руководство. Программный поиск и замена текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Пошаговое руководство. Программный перебор найденных элементов в документах](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Как программным способом восстановить выделенные элементы после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md)
