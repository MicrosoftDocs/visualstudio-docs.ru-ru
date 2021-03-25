---
description: Возвращает структуру, описывающую объект и его расположение в области или контейнере.
title: 'Идебугаддресс:: @ Address | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e616ded029c22b16b81ccd5f25086b11be6ff4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094405"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Возвращает структуру, описывающую объект и его расположение в области или контейнере.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>Параметры
`pAddress`\
[вход, выход] Структура [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) , которая заполняется этим методом.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Структура [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) передается в этот метод, который затем заполняет его соответствующими данными. Способ интерпретации этой информации зависит от типа возвращаемой информации и самого обработчика символов. Дополнительные сведения см. в разделе [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .

## <a name="see-also"></a>См. также
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
