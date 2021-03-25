---
description: Извлекает указанный порт.
title: 'IDebugCoreServer2:: Port | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 98737df16eda5d72f51f3b1f72c8bd7e0a2d3b6e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077815"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Извлекает указанный порт.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Параметры
`guidPort`\
окне Идентификатор GUID порта, который требуется получить.

`ppPort`\
заполняет Возвращает объект [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , представляющий нужный порт.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает, `E_PORTSUPPLIER_NO_PORT` Если порт с указанным идентификатором отсутствует.

## <a name="see-also"></a>См. также
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
