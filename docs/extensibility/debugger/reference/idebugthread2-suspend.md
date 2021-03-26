---
description: Приостанавливает поток.
title: 'IDebugThread2:: Suspend | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 902418aeb18c149b0732e972a34ed89b56bb22ce
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081143"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Приостанавливает поток.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Параметры
`pdwSuspendCount`\
заполняет Возвращает счетчик приостановок после операции приостановки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Каждый вызов этого метода увеличивает значение счетчика приостановки выше 0. Это число приостановок отображается в окне отладки **потоков** .

 Для каждого вызова этого метода должен быть последующий вызов метода [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) .

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Возобновить](../../../extensibility/debugger/reference/idebugthread2-resume.md);
