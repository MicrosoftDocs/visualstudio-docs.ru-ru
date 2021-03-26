---
description: Этот интерфейс отправляется модулем отладки (DE) в Диспетчер отладки сеансов (SDM) после завершения асинхронного вычисления выражения.
title: IDebugExpressionEvaluationCompleteEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b30b61c0b7a9a9f3e06465a6b194c882213afb34
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092206"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Этот интерфейс отправляется модулем отладки (DE) в Диспетчер отладки сеансов (SDM) после завершения асинхронного вычисления выражения.

## <a name="syntax"></a>Синтаксис

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс для сообщения о завершении вычисления выражения, начатого вызовом [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. Модель SDM использует [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейсу.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Параметр DE создает и отправляет этот объект события, чтобы сообщить о завершении вычисления выражения. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugExpressionEvaluationCompleteEvent2` .

|Метод|Описание|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Возвращает исходное выражение.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Возвращает результат вычисления выражения.|

## <a name="remarks"></a>Remarks
 Значение DE должно отсылать это событие, независимо от успешности оценки.

 Если вычисление не прошло успешно, `DEBUG_PROPINFO_VALUE` `DEBUG_PROPINFO_ATTRIB` флаги и не будут заданы в структуре [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , возвращаемой функцией [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) создается методом de и возвращается в случае `IDebugExpressionEvaluationCompleteEvent2` сбоя вычисления).

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
