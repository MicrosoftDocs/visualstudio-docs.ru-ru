---
description: Извлекает конкретного поставщика порта.
title: 'IDebugCoreServer2:: Жетпортсупплиер | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPortSupplier
helpviewer_keywords:
- IDebugCoreServer2::GetPortSupplier
ms.assetid: acf181d4-ef42-4aa5-86f9-95fd5467ea31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44e2cc718cc3f8ac99563881801fa3cd0565820c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077828"
---
# <a name="idebugcoreserver2getportsupplier"></a>IDebugCoreServer2::GetPortSupplier
Извлекает конкретного поставщика порта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPortSupplier( 
   REFGUID               guidPortSupplier,
   IDebugPortSupplier2** ppPortSupplier
);
```

```csharp
int GetPortSupplier( 
   ref Guid                guidPortSupplier,
   out IDebugPortSupplier2 ppPortSupplier
);
```

## <a name="parameters"></a>Параметры
`guidPortSupplier`\
окне Идентификатор GUID получаемого поставщика порта.

`ppPortSupplier`\
заполняет Возвращает объект [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) , представляющий требуемого поставщика порта.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
