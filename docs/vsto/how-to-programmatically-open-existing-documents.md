---
title: Руководство. Программное открытие существующих документов
description: Узнайте, как использовать метод Open для открытия существующего документа Microsoft Word, заданного с помощью полного пути и имени файла.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0153413a357a122b4bb5a1f1cbfb44079f78e128
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827309"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Руководство. Программное открытие существующих документов
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>Метод открывает существующий Microsoft Office документ Word, указанный в полном пути и имени файла. Этот метод возвращает объект <xref:Microsoft.Office.Interop.Word.Document> , представляющий открытый документ.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Открытие документа

- Вызовите <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> метод <xref:Microsoft.Office.Interop.Word.Documents> коллекции и укажите путь к документу.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet5":::

## <a name="to-open-a-document-as-read-only"></a>Открытие документа только для чтения

- Вызовите <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> метод, укажите путь к документу и задайте для аргумента *ReadOnly* в вызове метода **значение true** .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet6":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера кода требуется следующее.

- Документ с именем *NewDocument.doc* должен существовать в каталоге с именем *Test* на диске C.

## <a name="see-also"></a>См. также статью
- [Руководство. Программное создание новых документов](../vsto/how-to-programmatically-create-new-documents.md)
- [Руководство. программное закрытие документов](../vsto/how-to-programmatically-close-documents.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
