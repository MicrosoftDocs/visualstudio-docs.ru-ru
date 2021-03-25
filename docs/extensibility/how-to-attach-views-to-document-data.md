---
title: Как присоединить представления к данным документа | Документация Майкрософт
description: Вы можете присоединить новое представление документа к существующему объекту данных документа. Используйте эту процедуру, чтобы определить, можно ли присоединить представление.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8a034fc1c7cded7de4ead38cfba5d3410341c95d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057420"
---
# <a name="how-to-attach-views-to-document-data"></a>Как присоединить представления к данным документа
Если у вас есть новое представление документа, вы можете присоединить его к существующему объекту данных документа.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Определение возможности присоединения представления к существующему объекту данных документа

1. Реализуйте расширение <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. В реализации `IVsEditorFactory::CreateEditorInstance` метод вызывается `QueryInterface` для существующего объекта данных документа, когда интегрированная среда разработки вызывает вашу `CreateEditorInstance` реализацию.

    Вызов `QueryInterface` позволяет исследовать существующий объект данных документа, указанный в `punkDocDataExisting` параметре.

    Однако конкретные интерфейсы, которые необходимо запросить, зависят от редактора, открывающего документ, как описано в шаге 4.

3. Если не найти соответствующие интерфейсы для существующего объекта данных документа, то необходимо вернуть код ошибки в редактор, указывающий, что объект данных документа несовместим с вашим редактором.

    В реализации интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> диалоговое окно сообщения уведомляет о том, что документ открыт в другом редакторе, и спрашивает, нужно ли его закрыть.

4. Если закрыть этот документ, Visual Studio вызовет фабрику редактора еще раз. При этом вызове `DocDataExisting` параметр РАВЕН null. После этого реализация фабрики редактора может открыть объект данных документа в собственном редакторе.

   > [!NOTE]
   > Чтобы определить, можно ли работать с существующим объектом данных документа, можно также использовать закрытые знания реализации интерфейса путем приведения указателя к фактическому [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] классу реализации закрытой. Например, все стандартные редакторы реализуют `IVsPersistFileFormat` , которые наследуют от <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . Таким же, можно вызвать метод `QueryInterface` для <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> , и если идентификатор класса для существующего объекта данных документа соответствует идентификатору класса вашей реализации, то можно работать с объектом данных документа.

## <a name="robust-programming"></a>Отказоустойчивость
 Когда Visual Studio вызывает реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метода, он передает указатель на существующий объект данных документа в `punkDocDataExisting` параметре, если он существует. Изучите объект данных документа, возвращенный в `punkDocDataExisting` , чтобы определить, подходит ли объект данных документа для редактора, как описано в шаге 4 процедуры, описанной в этом разделе. Если это уместно, Фабрика редактора должна предоставить второе представление для данных, как описано в статье [Поддержка нескольких представлений документов](../extensibility/supporting-multiple-document-views.md). В противном случае он должен отобразить соответствующее сообщение об ошибке.

## <a name="see-also"></a>См. также
- [Поддержка нескольких представлений документов](../extensibility/supporting-multiple-document-views.md)
- [Данные документа и представление документа в пользовательских редакторах](../extensibility/document-data-and-document-view-in-custom-editors.md)
