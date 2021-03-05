---
description: Возвращает порт от поставщика порта.
title: 'IDebugPortSupplier2:: Port | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0fa191b70e44684577845ab4a48c6c4f82844bce
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145434"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
Возвращает порт от поставщика порта.

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
окне Глобальный уникальный идентификатор (GUID) порта.

`ppPort`\
заполняет Возвращает объект [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , представляющий порт.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает `E_PORTSUPPLIER_NO_PORT` , если порт с указанным идентификатором не существует.

## <a name="see-also"></a>См. также раздел
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
