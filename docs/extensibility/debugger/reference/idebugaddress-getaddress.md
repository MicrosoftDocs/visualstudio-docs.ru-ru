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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52c52d12d8c357f4dbadeef673a3dc4474713ce9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145447"
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

## <a name="remarks"></a>Комментарии
 Структура [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) передается в этот метод, который затем заполняет его соответствующими данными. Способ интерпретации этой информации зависит от типа возвращаемой информации и самого обработчика символов. Дополнительные сведения см. в разделе [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .

## <a name="see-also"></a>См. также раздел
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
