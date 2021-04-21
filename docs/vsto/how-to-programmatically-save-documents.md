---
title: Руководство. Программное сохранение документов
description: Узнайте, как можно использовать Visual Studio для программного сохранения документа без изменения имени документа или с новым именем.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 97f56ce0bd44eac71430a099b4fda9a7eddc7958
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107829012"
---
# <a name="how-to-programmatically-save-documents"></a>Руководство. Программное сохранение документов

Существует несколько способов сохранения Microsoft Office документов Word. Документ можно сохранить, не изменяя имя документа, или можно сохранить документ с новым именем.

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Сохранение документа без изменения имени

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Сохранение документа, связанного с настройкой на уровне документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.Save%2A> класса <xref:Microsoft.Office.Tools.Word.Document> . Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet7":::

### <a name="to-save-the-active-document"></a>Чтобы сохранить активный документ

1. Вызовите <xref:Microsoft.Office.Interop.Word._Document.Save%2A> метод для активного документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet8":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet8":::

   Если вы не уверены, что документ, который нужно сохранить, является активным документом, его можно указать по имени.

### <a name="to-save-a-document-specified-by-name"></a>Сохранение документа, указанного по имени

1. Используйте имя документа в качестве аргумента для <xref:Microsoft.Office.Interop.Word.Documents> коллекции. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet9":::

## <a name="save-a-document-with-a-new-name"></a>Сохранение документа с новым именем

Используйте `SaveAs` метод, чтобы сохранить документ с новым именем. Этот метод <xref:Microsoft.Office.Tools.Word.Document> ведущего элемента можно использовать в проекте Word уровня документа или в собственном <xref:Microsoft.Office.Interop.Word.Document> объекте любого проекта Word. Для этого метода требуется указать новое имя файла, но другие аргументы являются необязательными.

> [!NOTE]
> Если диалоговое окно **SaveAs** отображается внутри <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> обработчика событий `ThisDocument` и для параметра *Cancel* задано значение **false**, приложение может неожиданно завершить работу. Если для параметра *Cancel* задано **значение true**, появится сообщение об ошибке, указывающее, что автосохранение отключено.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Сохранение документа, связанного с настройкой на уровне документа, с новым именем

1. Вызовите `SaveAs` метод `ThisDocument` класса в проекте, используя полный путь и имя файла. Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` .

    > [!NOTE]
    > `SaveAs`Метод создает исключение, если целевой каталог не существует или при сохранении файла возникли другие проблемы. Рекомендуется использовать `try...catch` блок вокруг `SaveAs` метода или внутри вызывающего метода.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet10":::

### <a name="to-save-a-native-document-with-a-new-name"></a>Сохранение собственного документа с новым именем

1. Вызовите <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> метод объекта <xref:Microsoft.Office.Interop.Word.Document> , который необходимо сохранить, используя полный путь и имя файла. Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения.

     В следующем примере кода активный документ сохраняется с новым именем. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.

    > [!NOTE]
    > <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>Метод создает исключение, если целевой каталог не существует или при сохранении файла возникли другие проблемы. Рекомендуется использовать метод **try... блок catch** вокруг <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> метода или внутри вызывающего метода.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet10":::

## <a name="compile-the-code"></a>Компиляция кода

Для этого примера кода требуется следующее.

- Чтобы сохранить документ по имени, документ с именем *NewDocument.doc* должен существовать в каталоге с именем *Test* на диске C.

- Чтобы сохранить документ с новым именем, на диске C должен существовать каталог с именем *Test* .

## <a name="see-also"></a>См. также статью

- [Руководство. программное закрытие документов](../vsto/how-to-programmatically-close-documents.md)
- [Руководство. Программное открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)
- [Ведущий элемент документа](../vsto/document-host-item.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
