---
description: Этот интерфейс представляет исходный документ.
title: IDebugDocument2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96bf5821cb463b8a99f7376cb99b81ab8cae2206
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167351"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Этот интерфейс представляет исходный документ.

## <a name="syntax"></a>Синтаксис

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] обычно реализует этот интерфейс. Механизм отладки (DE) также может реализовать этот интерфейс, когда ему необходимо предоставить исходный код, а источник не существует на диске.  В таких случаях метод DE также реализует интерфейсы [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) и [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) , а также некоторые дополнительные методы в интерфейсах [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) и [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Методы в `IDebugDocumentContext2` `IDebugDisassemblyStream2` `IDebugDocumentPosition2` интерфейсах,, и `IDebugActivateDocumentEvent2` возвращают этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugDocument2` .

|Метод|Описание|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Возвращает имя документа в одной из нескольких форм.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Возвращает идентификатор класса документа.|

## <a name="remarks"></a>Комментарии
 Этот интерфейс реализуется только в том случае, если параметр DE предоставляет исходный код. Например, при отладке скрипта на HTML-странице Программа DE предоставляет исходный код, поскольку источник загружается или создается динамически и не существует в качестве файла на диске. При отладке традиционных языков, таких как C++, этот интерфейс не требуется реализовывать.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
