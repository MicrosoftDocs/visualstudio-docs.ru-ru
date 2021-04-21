---
title: Как присоединить расширения управляемого кода к документам
description: Узнайте, как присоединить сборку настройки к существующему документу Microsoft Office Word или Microsoft Office книге Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 60fc27345ef148fd47fdcee15924917ce63f8d68
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825502"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Как присоединить расширения управляемого кода к документам
  Сборку настройки можно прикрепить к существующему Microsoft Office документу Word или Microsoft Office книге Excel. Документ или книга могут иметь любой формат файла, поддерживаемый Microsoft Office проектами и инструментами разработки в Visual Studio. Дополнительные сведения см. в разделе [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Чтобы присоединить настройки к документу Word или Excel, используйте <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса. Поскольку <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класс предназначен для запуска на компьютере, на котором не установлен Microsoft Office, этот метод можно использовать в решениях, которые не связаны напрямую с разработкой Microsoft Office (например, консоль или приложение Windows Forms).

> [!NOTE]
> Настройка не сможет загрузиться, если код будет задавать элементы управления, отсутствующие в указанном документе.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Присоединение расширений управляемого кода к документу

1. В проекте, который не требует Microsoft Office, например консольное приложение или проект Windows Forms, добавьте ссылку на сборки *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* и *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* .

2. Добавьте следующие инструкции **Imports** или **using** в начало файла кода.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet4":::

3. Вызовите статический <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> метод.

     В следующем примере кода используется <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> перегрузка. Эта перегрузка принимает полный путь к документу и объект <xref:System.Uri> , указывающий расположение манифеста развертывания для настройки, которую необходимо присоединить к документу. В этом примере предполагается, что документ Word с именем **WordDocument1.docx** находится на рабочем столе, а манифест развертывания находится в папке с именем **Publish** , которая также находится на рабочем столе.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet3":::

4. Выполните сборку проекта и запустите приложение на компьютере, на котором нужно присоединить настройки. На компьютере должна быть установлена среда выполнения средств Visual Studio 2010 для Office.

## <a name="see-also"></a>См. также статью
- [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Руководство. Удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Манифесты приложений и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
