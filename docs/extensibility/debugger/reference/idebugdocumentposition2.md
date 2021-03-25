---
description: Этот интерфейс представляет абстрактное расположение в исходном файле.
title: IDebugDocumentPosition2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b7c4c8e469dff76e2af631c4943305b0e3ee8e7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066403"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Этот интерфейс представляет абстрактное расположение в исходном файле.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio обычно реализует этот интерфейс. Модуль отладки (DE) также реализует этот интерфейс, если он должен предоставить собственный исходный код (как, когда метод DE реализует интерфейс [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) ).

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс передается в качестве аргумента в [енумкодеконтекстс](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Он также предоставляется как часть объединения [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (в частности, структуры [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) ), которая в свою очередь является частью структуры [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , которая используется при создании ожидающей точки останова.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugDocumentPosition2` .

|Метод|Описание|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Возвращает имя файла исходного кода, содержащего эту точку документа.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Возвращает содержащий документ.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Определяет, содержится ли эта позицией в данном документе.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Возвращает диапазон для этой должности документа.|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
