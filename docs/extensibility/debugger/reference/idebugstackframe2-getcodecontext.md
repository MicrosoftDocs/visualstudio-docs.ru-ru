---
description: Получает контекст кода для этого кадра стека.
title: 'IDebugStackFrame2:: Жеткодеконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetCodeContext
helpviewer_keywords:
- IDebugStackFrame2::GetCodeContext
ms.assetid: 93d66159-a41d-49ef-982f-91bb4d073b74
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f01bf82a7ab7aafb6e43e343dfa1af89ea9cefe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142535"
---
# <a name="idebugstackframe2getcodecontext"></a>IDebugStackFrame2::GetCodeContext
Получает контекст кода для этого кадра стека.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCodeContext ( 
   IDebugCodeContext2** ppCodeCxt
);
```

```csharp
int GetCodeContext ( 
   out IDebugCodeContext2 ppCodeCxt
);
```

## <a name="parameters"></a>Параметры
`ppCodeCxt`\
заполняет Возвращает объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , представляющий текущий указатель инструкции в этом кадре стека.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
