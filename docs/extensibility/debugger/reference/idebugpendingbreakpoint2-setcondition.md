---
description: Задает или изменяет условие, связанное с ожидающей точкой останова.
title: 'IDebugPendingBreakpoint2:: Сеткондитион | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3cf12bce424e523702da92b86e8894a54ce58b7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076606"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Задает или изменяет условие, связанное с ожидающей точкой останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Параметры
`bpCondition`\
окне Структура [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) , указывающая заданное условие.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Все условия, которые ранее были связаны с ожидающей точкой останова, теряются. Все точки останова, привязанные к этой ожидающей точке останова, вызываются, чтобы задать для их условия значение, указанное в `bpCondition` параметре.

## <a name="see-also"></a>См. также
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
