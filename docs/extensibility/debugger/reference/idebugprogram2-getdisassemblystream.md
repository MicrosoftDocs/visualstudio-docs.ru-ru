---
description: Возвращает поток дизассемблированного кода для этой программы или части программы.
title: 'IDebugProgram2:: Жетдисассемблистреам | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e000ada618c21af865743bfb2bd9fd6b60a80a4b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159930"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Возвращает поток дизассемблированного кода для этой программы или части программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

## <a name="parameters"></a>Параметры
`dwScope`\
окне Задает значение из перечисления [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) , определяющего область потока дизассемблированного кода.

`pCodeContext`\
окне Объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , представляющий позицию, с которой начинается поток дизассемблирования.

`ppDisassemblyStream`\
заполняет Возвращает объект [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) , представляющий поток дизассемблированного кода.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает `E_DISASM_NOTSUPPORTED` , если дизассемблирование не поддерживается для этой конкретной архитектуры.

## <a name="remarks"></a>Комментарии
 Если `dwScopes` параметр имеет `DSS_HUGE` флаг [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) наборе перечисления, предполагается, что дизассемблирование будет возвращено большое количество инструкций дизассемблирования, например для всего файла или модуля. Если `DSS_HUGE` флаг не установлен, то Дизассемблированный код должен быть ограничен небольшим регионом, как правило, для одной функции.

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
