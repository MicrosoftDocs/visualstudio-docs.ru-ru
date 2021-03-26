---
title: IDebugExpressionContext2 | Документация Майкрософт
description: Этот интерфейс представляет контекст для вычисления выражения
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6d8745207f1ab075aedd43815e7a97a4f0721bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092297"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Этот интерфейс представляет контекст для вычисления выражения.

## <a name="syntax"></a>Синтаксис

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления контекста, в котором можно вычислить выражение.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов [жетекспрессионконтекст](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) возвращает этот интерфейс. Этот интерфейс доступен только в том случае, если отлаживаемая программа приостановлена и доступен кадр стека.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugExpressionContext2` .

|Метод|Описание|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Возвращает имя контекста вычисления.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Анализирует текстовое выражение на предмет оценки.|

## <a name="remarks"></a>Remarks
 Контекст оценки можно рассматривать как область для выполнения вычисления выражений.

 При остановке программы Диспетчер отладки сеансов (SDM) получает кадр стека от DE к вызову [енумфрамеинфо](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Затем SDM вызывает [жетекспрессионконтекст](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения `IDebugExpressionContext2` интерфейса. За этим следует вызов [парсетекст](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания интерфейса [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) , который представляет проанализированное выражение, готовое к оценке.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
