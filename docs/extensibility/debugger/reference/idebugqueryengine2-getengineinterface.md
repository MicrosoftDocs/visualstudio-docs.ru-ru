---
description: Возвращает интерфейс пользовательского модуля отладки (DE).
title: 'IDebugQueryEngine2:: Жетенгинеинтерфаце | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbf727de01c8cbf34d645aff4e0a64aeb476ebbd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167845"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Возвращает интерфейс пользовательского модуля отладки (DE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Параметры
`ppUnk`\
заполняет Возвращает `IUnknown` объект, представляющий модуль отладки (de), который может быть запрошен для любого другого допустимого интерфейса, связанного с методом de (например, [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) или [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Полученный интерфейс следует использовать с осторожностью, поскольку вызов через интерфейсы, полученные из этого метода, обходит обработку диспетчера отладки сеанса и может привести к неправильному состоянию SDM или формированию ошибок во время отладки.

## <a name="see-also"></a>См. также раздел
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
