---
description: Возвращает идентификатор расположения кода, представляющий текущее расположение кода.
title: 'IDebugDisassemblyStream2:: Жеткуррентлокатион | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
ms.assetid: 512302f1-12b1-4107-8a6e-c5bc878ce1c3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 851c7a22b69c60baac52ec3597f0b1f6df64cfa2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067040"
---
# <a name="idebugdisassemblystream2getcurrentlocation"></a>IDebugDisassemblyStream2::GetCurrentLocation
Возвращает идентификатор расположения кода, представляющий текущее расположение кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCurrentLocation( 
   UINT64* puCodeLocationId
);
```

```csharp
int GetCurrentLocation( 
   out ulong puCodeLocationId
);
```

## <a name="parameters"></a>Параметры
`puCodeLocationId`\
заполняет Возвращает идентификатор расположения кода. Описание идентификатора расположения кода см. в разделе "Примечания" для метода [жеткоделокатионид](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Идентификатор расположения кода можно преобразовать в контекст кода, вызвав метод [жеткодеконтекст](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .

## <a name="see-also"></a>См. также
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
