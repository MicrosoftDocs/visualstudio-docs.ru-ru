---
description: Этот интерфейс представляет поток, выполняющийся в программе.
title: IDebugThread2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8b09aa546e4711b1c11623a3596ba0e385b2a14
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164426"
---
# <a name="idebugthread2"></a>IDebugThread2
Этот интерфейс представляет поток, выполняющийся в программе.

## <a name="syntax"></a>Синтаксис

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления потока выполнения в одной программе.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите метод [Thread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) , чтобы получить этот интерфейс, представляющий текущий активный поток.

 Этот интерфейс также используется при создании запроса точки останова (см. [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Этот интерфейс также возвращается при разрешении привязанного или ошибочного точки останова (см. [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) и [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugThread2` .

|Метод|Описание|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Извлекает список кадров стека для этого потока.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Возвращает имя потока.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Задает имя потока.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Возвращает программу, в которой выполняется поток.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Определяет, может ли следующий оператор быть задан для данного кадра стека и контекста кода.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Задает следующий оператор для заданного кадра стека и контекста кода.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Возвращает идентификатор системного потока.|
|[Приостановить](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Приостанавливает поток.|
|[Возобновить](../../../extensibility/debugger/reference/idebugthread2-resume.md);|Возобновляет поток.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Возвращает свойства, описывающие поток.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Возвращает логический поток, связанный с данным физическим потоком.|

## <a name="remarks"></a>Комментарии
 Поскольку один физический поток может работать в нескольких программах, несколько `IDebugThread2` из них могут представлять один и тот же физический поток.

 При возникновении точки останова или исключения событие отправляется путем вызова [события](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Одним из аргументов этого метода является `IDebugThread2` интерфейс, представляющий текущий поток. [Енумфрамеинфо](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) используется для получения интерфейса [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) для текущего кадра стека.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
