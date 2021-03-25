---
description: Считывает последовательность байтов, начиная с заданного расположения.
title: 'IDebugMemoryBytes2:: Реадат | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1fdcdf46f7f57f3ee6035bf9af8be5a7e99739f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076827"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Считывает последовательность байтов, начиная с заданного расположения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>Параметры
`pStartContext`\
окне Объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , указывающий, с чего следует начать чтение байтов.

`dwCount`\
окне Число байтов для чтения. Также указывает длину `rgbMemory` массива.

`rgbMemory`\
[вход, выход] Массив заполняется фактически считанными байтами.

`pdwRead`\
заполняет Возвращает число фактически считанных непрерывных байтов.

`pdwUnreadable`\
[вход, выход] Возвращает число нечитаемых байтов. Может иметь значение null, если клиент неинтересен в количестве нечитаемых байтов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Если запрашиваются 100 байт и первые 50 доступны для чтения, следующие 20 становятся нечитаемыми, а оставшиеся 30 читаются, этот метод возвращает:

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 В этом случае, поскольку `*pdwRead + *pdwUnreadable < dwCount` вызывающий объект должен выполнить дополнительный вызов для чтения оставшихся 30 байт первоначально запрошенного 100, а объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , переданный в `pStartContext` параметре, должен иметь расширение 70.

## <a name="see-also"></a>См. также
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
