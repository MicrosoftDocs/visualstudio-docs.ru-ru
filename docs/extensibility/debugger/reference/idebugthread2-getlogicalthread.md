---
description: Отладчики не реализуют этот метод.
title: 'IDebugThread2:: Жетлогикалсреад | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3fe053a15ca6c89167b4b4cbf9bdffc8d7c334e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070977"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Отладчики не реализуют этот метод.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

## <a name="parameters"></a>Параметры
`pStackFrame`\
окне Объект [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , представляющий кадр стека.

`ppLogicalThread`\
заполняет Возвращает `IDebugLogicalThread2` интерфейс, представляющий связанный логический поток. Реализация модуля отладки должна установить значение null.

## <a name="return-value"></a>Возвращаемое значение
 Реализации модуля отладки всегда возвращают `E_NOTIMPL` .

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
