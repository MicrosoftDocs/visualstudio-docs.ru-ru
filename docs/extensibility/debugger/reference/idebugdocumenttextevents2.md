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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: edf7cd483b39fb1fb5dc182a08bbbca8295b2359
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094098"
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

## <a name="remarks"></a>Remarks
 Только модули отладки, которые предоставляют собственные документы, используют `IDebugDocumentTextEvent2` интерфейс. Примером этого может быть Подсистема отладки сценариев. В процессе интерпретации скриптов можно создать новый исходный код, который отсутствует в любом файле диска и известен только параметру DE.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
