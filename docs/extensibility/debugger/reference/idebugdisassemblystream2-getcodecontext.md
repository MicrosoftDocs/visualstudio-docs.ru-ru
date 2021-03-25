---
description: Возвращает объект контекста кода, соответствующий указанному идентификатору расположения кода.
title: 'IDebugDisassemblyStream2:: Жеткодеконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c532c68435d1eaabdb03f8acae571ac4b71a5a7b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067079"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
Возвращает объект контекста кода, соответствующий указанному идентификатору расположения кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCodeContext( 
   UINT64               uCodeLocationId,
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   ulong                  uCodeLocationId,
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Параметры
`uCodeLocationId`\
окне Указывает идентификатор расположения кода. Описание идентификатора расположения кода см. в разделе "Примечания" для метода [жеткоделокатионид](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) .

`ppCodeContext`\
заполняет Возвращает объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , представляющий связанный контекст кода.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Идентификатор расположения кода может быть возвращен из вызова метода [жеткуррентлокатион](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) и может присутствовать в структуре [дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md) .

 Чтобы преобразовать контекст кода в идентификатор расположения кода, вызовите метод [жеткоделокатионид](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) .

## <a name="see-also"></a>См. также
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
