---
title: Руководство. Удаление расширений управляемого кода из документов
description: Программно удалите сборку настройки из документа или книги, которая является частью настройки уровня документа для Microsoft Word или Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 129b1bda44abf7283efe1996f1898491025ee9d9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825450"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Руководство. Удаление расширений управляемого кода из документов
  Сборку настройки можно программным образом удалить из документа или книги, которая является частью настройки уровня документа для Microsoft Office Word или Microsoft Office Excel. Пользователи могут открывать документы и просматривать содержимое, но любой настраиваемый пользовательский интерфейс (UI), добавляемый в документы, не будет отображаться, и код не будет выполняться.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Сборку настройки можно удалить с помощью одного из `RemoveCustomization` методов, предоставляемых [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Используемый метод зависит от того, требуется ли удалить настройку во время выполнения (т. е. путем запуска кода в настройке во время открытия документа Word или книги Excel) или удалить настройку из закрытого документа или документа, расположенного на сервере, на котором не установлен Microsoft Office.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Удаление сборки настройки во время выполнения

1. В коде настройки вызовите <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> метод (для Word) или <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> метод (для Excel). Этот метод следует вызывать только после того, как настройка больше не нужна.

     Место вызова этого метода в коде зависит от того, как используется настройка. Например, если клиенты используют функции настройки до тех пор, пока они не будут готовы отправить документ другим клиентам, которым требуется только сам документ (а не Настройка), можно предоставить некоторый пользовательский интерфейс, вызывающий, `RemoveCustomization` когда пользователь щелкнет его. Кроме того, если ваша Настройка заполняет документ данными при первом открытии, но настройка не предоставляет другие функции, доступ к которым осуществляется напрямую клиентами, можно вызвать Ремовекустомизатион, как только ваша Настройка завершит инициализацию документа.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Удаление сборки настройки из закрытого документа или документа на сервере

1. В проекте, который не требует Microsoft Office, например консольное приложение или проект Windows Forms, добавьте ссылку на сборку *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* .

2. Добавьте следующий оператор **Imports** или **using** в начало файла кода.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet1":::

3. Вызовите статический <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса и укажите путь к документу решения для параметра.

     В следующем примере кода предполагается, что вы удаляете настройку из документа с именем *WordDocument1.docx* , который находится на рабочем столе.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet2":::

4. Выполните сборку проекта и запустите приложение на компьютере, на котором нужно удалить настройку. На компьютере должна быть установлена среда выполнения средств Visual Studio 2010 для Office.

## <a name="see-also"></a>См. также статью
- [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Как присоединить расширения управляемого кода к документам](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
