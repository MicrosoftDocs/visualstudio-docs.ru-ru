---
description: Возвращает зависящее от компьютера представление диапазона физических адресов, связанных с кадром стека.
title: 'IDebugStackFrame2:: Жетфисикалстаккранже | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 41664f0e59b0eba6ae8a98599c74bd91fe26cf2a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145928"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Возвращает зависящее от компьютера представление диапазона физических адресов, связанных с кадром стека.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>Параметры
`paddrMin`\
заполняет Возвращает самый низкий физический адрес, связанный с данным кадром стека.

`paddrMax`\
заполняет Возвращает наибольший физический адрес, связанный с этим кадром стека.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Сведения, возвращаемые этим методом, используются диспетчером отладки сеансов (SDM) для сортировки кадров стека.

 Предполагается, что стек вызовов растет, то есть новые кадры стека добавляются по меньшей мере с более низкими адресами памяти. Архитектура времени выполнения должна обеспечивать физические диапазоны стека, соответствующие этому предположении.

## <a name="see-also"></a>См. также раздел
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
