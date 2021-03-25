---
title: Как открыть стандартные редакторы | Документация Майкрософт
description: Узнайте, как реализовать метод Опенитем с помощью стандартного редактора. Интегрированная среда разработки определяет стандартный редактор для назначенного типа файлов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1b0de198e96ff268a0744a4a97a4a160c585af9c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069911"
---
# <a name="how-to-open-standard-editors"></a>Руководство. Открытие стандартных редакторов
При открытии стандартного редактора среда IDE определяет стандартный редактор для назначенного типа файлов вместо того, чтобы указывать для файла редактор, зависящий от проекта.

 Выполните следующую процедуру, чтобы реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод. Откроется файл проекта в стандартном редакторе.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Реализация метода Опенитем с помощью стандартного редактора

1. Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> ( `RDT_EditLock` ), чтобы определить, открыт ли уже файл объекта данных документа.

2. Если файл уже открыт, переsurfaceйте его, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> метод, указав значение `IDO_ActivateIfOpen` для `grfIDO` параметра.

     Если файл открыт и владельцем документа является другой проект, отличный от проекта вызывающего проекта, то проект получит предупреждение о том, что открываемый редактор находится в другом проекте. Затем отображается окно файла.

3. Если документ не открыт или не находится в выполняемой таблице документов, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод ( `OSE_ChooseBestStdEditor` ), чтобы открыть стандартный редактор для файла.

     При вызове метода интегрированная среда разработки выполняет следующие задачи:

    1. Интегрированная среда разработки просматривает подраздел редакторы/{Гуидедитортипе}/Extensions в реестре, чтобы определить, какой редактор может открыть файл и имеет наивысший приоритет для этого.

    2. После того, как интегрированная среда разработки определила, какой редактор может открыть файл, интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . Реализация этого метода в редакторе возвращает сведения, необходимые для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> и открытия нового документа интегрированной средой разработки.

    3. Наконец, интегрированная среда разработки загружает документ с помощью обычного интерфейса сохраняемости, такого как <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .

    4. Если в интегрированной среде разработки ранее было определено, что иерархия или элемент иерархии доступны, интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> метод в проекте, чтобы получить указатель контекста уровня проекта <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> для обратной передачи с <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> вызовом метода.

4. <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> Если вы хотите разрешить редактору получить контекст из проекта, возвращается указатель на интегрированную среду разработки.

     Выполнение этого шага позволяет проекту предлагать дополнительные службы для редактора.

     Если представление документа или объект представления документа успешно размещается в рамке окна, объект инициализируется с данными путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> .

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)
- [Пошаговое руководство. открытие редакторов, зависящих от проекта](../extensibility/how-to-open-project-specific-editors.md)
- [Руководство. открытие редакторов для открытых документов](../extensibility/how-to-open-editors-for-open-documents.md)
- [Отображение файлов с помощью команды "открыть файл"](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
