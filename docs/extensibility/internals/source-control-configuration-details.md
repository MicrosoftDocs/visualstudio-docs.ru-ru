---
title: Сведения о конфигурации системы управления версиями | Документация Майкрософт
description: Узнайте, как реализовать систему управления версиями для типа проекта в Visual Studio, что включает в себя настройку системы проектов или редактора для запроса разрешений.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5c93e690922057116b395bed3881627e8a37847
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069352"
---
# <a name="source-control-configuration-details"></a>Сведения о конфигурации системы управления версиями
Для реализации системы управления версиями необходимо правильно настроить систему проекта или редактор, чтобы сделать следующее:

- Запрос разрешения на переход в измененное состояние

- Запрос разрешения на сохранение файла

- Запрос разрешения на добавление, удаление или переименование файлов в проекте

## <a name="request-permission-to-transition-to-changed-state"></a>Запрос разрешения на переход в измененное состояние
 Проект или редактор должны запрашивать разрешение на переход в измененное состояние (Dirty) путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> . Каждый редактор, реализующий, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> должен вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и принимать утверждение для изменения документа из среды перед возвратом `True` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> . Проект, по сути, является редактором для файла проекта, и поэтому несет ответственность за реализацию отслеживания измененных состояний для файла проекта в качестве текстового редактора для своих файлов. Среда обрабатывает измененное состояние решения, но необходимо обработать измененное состояние любого объекта, на который ссылается решение, но не хранить, например файл проекта или его элементы. Как правило, если проект или редактор отвечает за управление сохраняемостью для элемента, то он отвечает за реализацию отслеживания измененных состояний.

 В ответ на `IVsQueryEditQuerySave2::QueryEditFiles` вызов среда может выполнять следующие действия:

- Отклоните вызов Change, в этом случае редактор или проект должны остаться в неизмененном (чистом) состоянии.

- Указывает, что необходимо перезагрузить данные документа. Для проекта среда выполнит перезагрузку данных для проекта. Редактор должен перезагрузить данные с диска с помощью своей <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> реализации. В любом случае контекст в проекте или редакторе может измениться при повторной загрузке данных.

  Это сложная и сложная задача модифицировать соответствующие `IVsQueryEditQuerySave2::QueryEditFiles` вызовы в существующую базу кода. В результате эти вызовы должны быть интегрированы во время создания проекта или редактора.

## <a name="request-permission-to-save-a-file"></a>Запрос разрешения на сохранение файла
 Прежде чем проект или редактор сохранит файл, он должен вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> . Для файлов проекта эти вызовы автоматически выполняются решением, которое знает, когда следует сохранять файл проекта. Редакторы отвечают за выполнение этих вызовов, если только в реализации редактора не `IVsPersistDocData2` используется вспомогательная функция <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> . Если редактор реализует `IVsPersistDocData2` таким образом, вызывается метод `IVsQueryEditQuerySave2::QuerySaveFile` или `IVsQueryEditQuerySave2::QuerySaveFiles` .

> [!NOTE]
> Всегда вынимайте эти вызовы с вытеснением, то есть в тот момент, когда редактор сможет получить отмену.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Запрос разрешения на добавление, удаление или переименование файлов в проекте
 Прежде чем проект сможет добавить, переименовать или удалить файл или каталог, он должен вызвать соответствующий `IVsTrackProjectDocuments2::OnQuery*` метод для запроса разрешения из среды. Если разрешение предоставлено, проект должен завершить операцию, а затем вызвать соответствующий `IVsTrackProjectDocuments2::OnAfter*` метод, чтобы уведомить среду о завершении операции. Проект должен вызывать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейса для всех файлов (например, специальных файлов), а не только для родительских файлов. Вызовы файлов являются обязательными, но вызовы каталогов являются необязательными. Если проект содержит сведения о каталоге, он должен вызвать соответствующие <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> методы, но если эти сведения отсутствуют, среда выводит сведения о каталоге.

 Проект не должен вызывать методы `IVsTrackProjectDocuments2` в проекте, открытом или закрытом. Прослушиватели, которые хотят получить эти сведения при запуске, могут ожидать <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> события и выполнить итерацию по решению, чтобы найти необходимые сведения. При завершении работы эти сведения не требуются. `IVsTrackProjectDocuments2` предоставляется из <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .

 Для каждого действия Add, Rename и Remove существует `OnQuery*` метод и `OnAfter*` метод. Вызовите `OnQuery*` метод, чтобы запросить разрешение на добавление, переименование или удаление файла или каталога. Вызовите `OnAfter*` метод после добавления, переименования или удаления файла или каталога, а также состояние проекта, отражающее новое состояние.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)
