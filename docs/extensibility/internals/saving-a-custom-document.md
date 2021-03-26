---
title: Сохранение настраиваемого документа | Документация Майкрософт
description: Сведения о процессе, который выполняется для пользовательского документа для типа проекта, добавляемого в интегрированную среду разработки Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a536a5f0f2b1cac09c65079974c661e09e9139ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080922"
---
# <a name="saving-a-custom-document"></a>Сохранение настраиваемого документа
Среда обрабатывает команды **сохранить**, **Сохранить как** и **сохранить все** . Когда пользователь нажимает кнопку **сохранить**, **Сохранить как** **или сохранить все** в меню **файл** или закрывает решение, в результате чего происходит сохранение всего процесса.

 ![Сохранение в редакторе клиентов](../../extensibility/internals/media/private.gif "Личные") Сохранение, сохранение как и сохранение всей обработки команд для пользовательского редактора

 Этот процесс описан в следующих шагах.

1. Для команд **сохранить** и **Сохранить как** среда использует <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службу для определения активного окна документа и, таким образом, элементы должны быть сохранены. Когда окно активного документа будет известно, среда находит указатель иерархии и идентификатор элемента (itemID) для документа в выполняемой таблице документов. Дополнительные сведения см. в разделе [выполнение таблицы документов](../../extensibility/internals/running-document-table.md).

     Для команды сохранить все среда использует сведения из таблицы выполняемого документа для компиляции списка всех элементов для сохранения.

2. Когда решение получает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> вызов, оно проходит по набору выбранных элементов (то есть множественный выбор, предоставляемый <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службой).

3. В каждом выбранном элементе решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> метода, чтобы определить, должна ли быть включена команда меню "Сохранить". Если один или несколько элементов являются "грязными", команда "Сохранить" будет включена. Если в иерархии используется стандартный редактор, то иерархия делегирует запрос о состоянии "грязного" в редактор, вызывая <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> метод.

4. Для каждого выбранного элемента, который является "грязным", решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> метода в соответствующих иерархиях.

     В случае с пользовательским редактором связь между объектом данных документа и проектом является закрытой. Таким же, все специальные проблемы сохраняемости обрабатываются между этими двумя объектами.

    > [!NOTE]
    > Если вы реализуете собственный механизм сохраняемости, не забудьте вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> метод для экономии времени. Этот метод проверяет, является ли сохранение файла защищенным (например, если файл не доступен только для чтения).

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)
