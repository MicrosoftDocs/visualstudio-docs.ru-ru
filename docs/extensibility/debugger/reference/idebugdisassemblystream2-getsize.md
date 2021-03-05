---
description: Возвращает размер в инструкциях этого потока дизассемблированного кода.
title: 'IDebugDisassemblyStream2:: DataSize | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94207c8e14306049068e838971aa778290de2ba6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154370"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Возвращает размер в инструкциях этого потока дизассемблированного кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSize( 
   UINT64* pnSize
);
```

```csharp
int GetSize( 
   out ulong pnSize
);
```

## <a name="parameters"></a>Параметры
`pnSize`\
заполняет Возвращает размер в инструкциях.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Значение, возвращаемое этим методом, можно использовать для выделения массива структур [дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md) , которые затем передаются в метод [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
