---
description: Привязывает эту отложенную точку останова к одному или нескольким расположениям кода.
title: 'IDebugPendingBreakpoint2:: BIND | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Bind
helpviewer_keywords:
- Bind method
- IDebugPendingBreakpoint2::Bind method
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a99319aa4269a1f17032a30ea8df02b4f08836a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084536"
---
# <a name="idebugpendingbreakpoint2bind"></a>IDebugPendingBreakpoint2::Bind
Привязывает эту отложенную точку останова к одному или нескольким расположениям кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Bind( 
   void 
);
```

```csharp
int Bind();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает значение `E_BP_DELETED` , если точка останова была удалена.

## <a name="remarks"></a>Remarks
 При вызове этого метода модуль отладки (DE) должен попытаться привязать эту отложенную точку останова ко всем расположениям кода, которые совпадают.

 После возврата из этого метода вызывающему объекту необходимо подождать события, указывающие на то, что ожидающая точка останова имеет привязку или находится в ошибке, прежде чем предположить, что вызовы методов [енумбаундбреакпоинтс](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) или [енумеррорбреакпоинтс](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)будут перечислять все привязанные точки останова, соответственно.

## <a name="see-also"></a>См. также
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
