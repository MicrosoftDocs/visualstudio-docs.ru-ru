---
title: Руководство. открытие редакторов Project-Specific | Документация Майкрософт
description: Узнайте, как реализовать метод Опенитем с помощью редактора для конкретного проекта, чтобы проект мог открыть файл, привязанный к редактору для этого проекта.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8fa68ff628212a207f860a3f9e6eca960481ee9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069885"
---
# <a name="how-to-open-project-specific-editors"></a>Пошаговое руководство. открытие редакторов, зависящих от проекта
Если файл элемента, открываемый проектом, внутренне привязан к конкретному редактору для этого проекта, проект должен открыть файл с помощью редактора, зависящего от проекта. Не удается делегировать файл механизму IDE для выбора редактора. Например, вместо стандартного редактора точечных рисунков можно использовать этот параметр редактора для конкретного проекта, чтобы указать конкретный редактор растровых изображений, который распознает сведения в файле, который уникален для вашего проекта.

 Интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод, когда он определяет, что файл должен быть открыт конкретным проектом. Дополнительные сведения см. [в разделе Отображение файлов с помощью команды открыть файл](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Используйте следующие рекомендации для реализации метода, `OpenItem` чтобы проект открывал файл с помощью специального редактора.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Реализация метода Опенитем с помощью редактора для конкретного проекта

1. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> метод ( `RDT_EditLock` ), чтобы определить, открыт ли файл (объект данных документа).

    > [!NOTE]
    > Дополнительные сведения о данных документа и объектах представления документов см. [в разделе данные документа и представление документа в пользовательских редакторах](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Если файл уже открыт, переsurfaceйте его, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> метод и указав значение IDO_ActivateIfOpen для `grfIDO` параметра.

     Если файл открыт, а документ принадлежит проекту, отличному от вызывающего проекта, пользователю будет выдано предупреждение о том, что редактор открывается из другого проекта. Затем отображается окно файла.

3. Если текстовый буфер (объект данных документа) уже открыт и вы хотите вложить в него другое представление, вы несете ответственность за подключение этого представления. Для создания экземпляра представления (объекта представления документа) из проекта рекомендуется использовать следующий подход:

    1. Вызовите `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> службу, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> интерфейс.

    2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> метод, чтобы создать экземпляр класса представления документов.

4. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> метод, указав объект представления документа.

     Этот метод разсайтов объект представления документа в окне документа.

5. Выполните соответствующие вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> методов или.

     На этом этапе представление должно быть полностью инициализировано и готово к открытию.

6. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод, чтобы показать и открыть представление.

## <a name="see-also"></a>См. также
- [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)
- [Руководство. Открытие стандартных редакторов](../extensibility/how-to-open-standard-editors.md)
- [Руководство. открытие редакторов для открытых документов](../extensibility/how-to-open-editors-for-open-documents.md)
