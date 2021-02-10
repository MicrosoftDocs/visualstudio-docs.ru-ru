---
title: 'Идебугсимболпровидер:: Жеткласстипебинаме | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetClassTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetClassTypeByName method
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f6843eee8e6de7ec3e8cfd52362ee4463dea7da4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956429"
---
# <a name="idebugsymbolprovidergetclasstypebyname"></a>IDebugSymbolProvider::GetClassTypeByName
Этот метод получает тип поля класса, представляющий полное имя класса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetClassTypeByName( 
   LPCOLESTR          pszClassName,
   NAME_MATCH         nameMatch,
   IDebugClassField** ppField
);
```

```csharp
int GetClassTypeByName(
   string               pszClassName,
   NAME_MATCH           nameMatch,
   out IDebugClassField ppField
);
```

## <a name="parameters"></a>Параметры
`pszClassName`\
окне Имя класса.

`nameMatch`\
окне Выбирает тип соответствия, например с учетом регистра. Значение из перечисления [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) .

`ppField`\
заполняет Возвращает тип класса, представленный интерфейсом [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
