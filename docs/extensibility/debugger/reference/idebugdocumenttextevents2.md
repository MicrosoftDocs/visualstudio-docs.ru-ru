---
description: Этот интерфейс используется для уведомления Visual Studio об изменениях в исходном документе, предоставляемых модулем отладки.
title: IDebugDocumentTextEvents2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bcbe6e44923172c3eac4da605848e972216837cc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154188"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Этот интерфейс используется для уведомления Visual Studio об изменениях в исходном документе, предоставляемых модулем отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс для поддержки внесения изменений в исходный код. Этот интерфейс обычно реализуется для того же объекта, который реализует интерфейс [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Получает этот интерфейс посредством вызова <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> метода. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>Интерфейс получается из вызова <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> метода. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>Интерфейс получается путем вызова метода [QueryInterface](/cpp/atl/queryinterface) в интерфейсе [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugDocumentTextEvents2` .

|Метод|Описание|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Указывает, что весь документ был уничтожен.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Уведомляет пакет отладки, что текст вставлен в документ.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Уведомляет пакет отладки, что текст был удален из документа.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Уведомляет пакет отладки, что текст был заменен в документе.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Уведомляет пакет отладки, что в документе были обновлены текстовые атрибуты.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Уведомляет получателя о том, что атрибуты документа были обновлены.|

## <a name="remarks"></a>Комментарии
 Только модули отладки, которые предоставляют собственные документы, используют `IDebugDocumentTextEvent2` интерфейс. Примером этого может быть Подсистема отладки сценариев. В процессе интерпретации скриптов можно создать новый исходный код, который отсутствует в любом файле диска и известен только параметру DE.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
