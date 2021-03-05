---
description: Разрешает (или запрещает) вычисление выражений в заданном потоке, даже если программа остановлена.
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94e049b4595c85e628b69a3613ae88ac27b013c7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153434"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Разрешает (или запрещает) вычисление выражений в заданном потоке, даже если программа остановлена.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WatchForExpressionEvaluationOnThread( 
   IDebugProgram2*       pOriginatingProgram,
   DWORD                 dwTid,
   DWORD                 dwEvalFlags,
   IDebugEventCallback2* pExprCallback,
   BOOL                  fWatch
);
```

```csharp
int WatchForExpressionEvaluationOnThread( 
   IDebugProgram2       pOriginatingProgram,
   uint                  dwTid,
   uint                  dwEvalFlags,
   IDebugEventCallback2 pExprCallback,
   int                   fWatch
);
```

## <a name="parameters"></a>Параметры
`pOriginatingProgram`\
окне Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, которая вычисляет выражение.

`dwTid`\
окне Задает идентификатор потока.

`dwEvalFlags`\
окне Сочетание флагов из перечисления [евалфлагс](../../../extensibility/debugger/reference/evalflags.md) , определяющее способ выполнения вычисления.

`pExprCallback`\
окне Объект [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , который будет использоваться для отправки событий отладки, происходящих во время вычисления выражения.

`fWatch`\
окне Если ненулевое значение ( `TRUE` ), разрешает вычисление выражений в потоке, определенном `dwTid` ; в противном случае ноль ( `FALSE` ) запрещает вычисление выражений в этом потоке.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Если диспетчер отладки сеансов (SDM) запрашивает программу, определяемую `pOriginatingProgram` параметром, для вычисления выражения уведомляет все другие присоединенные программы, вызывая этот метод.

 Вычисление выражений в одной программе может привести к тому, что код будет выполняться в другой из-за вычисления функции или оценки любых `IDispatch` свойств. Поэтому этот метод позволяет выполнять и завершать вычисление выражений, даже если поток может быть остановлен в этой программе.

## <a name="see-also"></a>См. также раздел
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
