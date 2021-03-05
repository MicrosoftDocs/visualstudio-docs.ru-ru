---
description: Возвращает имя поставщика порта.
title: 'IDebugPortSupplier2:: Жетпортсупплиернаме | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPortSupplierName
helpviewer_keywords:
- IDebugPortSupplier2::GetPortSupplierName
ms.assetid: e4c368ab-640d-4b5b-9f74-810dc9364d8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 780dd6c3974f407c753131183e4ac6e9562ed5dd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145420"
---
# <a name="idebugportsupplier2getportsuppliername"></a>IDebugPortSupplier2::GetPortSupplierName
Возвращает имя поставщика порта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPortSupplierName( 
   BSTR* pbstrName
);
```

```csharp
int GetPortSupplierName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Параметры
`pbstrName`\
заполняет Возвращает имя поставщика порта.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
