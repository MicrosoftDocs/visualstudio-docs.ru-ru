---
title: Определение того, какой редактор открывает файл в проекте | Документация Майкрософт
description: Сведения о разделах реестра и методах пакета SDK для Visual Studio, которые используются в Visual Studio для определения того, какой редактор открывает файл в проекте.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fb6f142ea25748f6798fb60d7c03862c51819349
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090867"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Определение того, какой редактор открывает файл в проекте
Когда пользователь открывает файл в проекте, среда проходит процесс опроса, в конечном итоге открывая соответствующий редактор или конструктор для этого файла. Начальная процедура, применяемая средой, одинакова для стандартных и пользовательских редакторов. При опросе редактора, используемого для открытия файла, среда использует разнообразные критерии, и пакет VSPackage должен координировать среду во время этого процесса.

 Например, когда пользователь выбирает команду **Открыть** в меню **файл** , а затем выбирает *filename. RTF* (или любой другой файл с расширением *. RTF* ), среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> реализацию для каждого проекта, постепенно переключаясь по всем экземплярам проекта в решении. Проекты возвращают набор флагов, которые определяют утверждения для документа по приоритету. При использовании наивысшего приоритета среда вызывает соответствующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод. Дополнительные сведения о процессе опроса см. в разделе [Добавление шаблонов проектов и элементов проектов](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Проект "Прочие файлы" заявляет все файлы, которые не затребованы другими проектами. Таким образом, пользовательские редакторы могут открывать документы до их открытия в стандартных редакторах. Если проект прочих файлов требует файл, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы открыть файл в стандартном редакторе. Среда проверяет внутренний список зарегистрированных редакторов для одного, обрабатывающего *RTF* файлы. Этот список находится в реестре в следующем разделе:

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ \<version> \едиторс \\ \<editor factory guid> \екстенсионс**

 Среда также проверяет идентификаторы классов в **HKEY_CLASSES_ROOT\CLSID** ключе для любых объектов, имеющих подраздел **DocObject**. Если расширение файла найдено, на месте в Visual Studio создается внедренная версия приложения, например Microsoft Word. Эти объекты документов должны быть составными файлами, реализующими <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> интерфейс, или объект должен реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> интерфейс.

 Если в реестре нет фабрики редактора для *RTF* -файлов, среда ищет ключ **HKEY_CLASSES_ROOT \\ . RTF** и открывает редактор, указанный там. Если расширение файла не найдено в **HKEY_CLASSES_ROOT**, среда использует текстовый редактор Visual Studio Core для открытия файла, если это текстовый файл.

 Если основной текстовый редактор завершается ошибкой, что происходит, если файл не является текстовым, среда использует двоичный редактор для файла.

 Если среда находит редактор для расширения *RTF* в своем реестре, он загружает пакет VSPackage, реализующий эту фабрику редактора. Среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> метод для нового пакета VSPackage. Пакет VSPackage вызывает `QueryService` для `SID_SVsRegistorEditor` , используя <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> метод для регистрации фабрики редактора в среде.

 Теперь среда проверяет внутренний список зарегистрированных редакторов, чтобы найти только что зарегистрированную фабрику редактора для *RTF* файлов. Среда вызывает реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метода, передавая имя файла и тип представления для создания.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
