---
description: Возвращает адрес отладки, следующий за заданным адресом отладки в методе.
title: 'Идебугсимболпровидер:: Жетнекстаддресс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc269dcfc472c2f8bb3e5a9ed9a91ecd25292870
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075579"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Возвращает адрес отладки, следующий за заданным адресом отладки в методе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>Параметры
`pAddress`\
окне Заданный адрес отладки.

`fStatementOnly`\
окне Если значение — TRUE, адреса отладки ограничиваются одной инструкцией.

`ppAddress`\
заполняет Возвращает следующий адрес отладки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает допустимый `HRESULT` , обычно S_OK.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
