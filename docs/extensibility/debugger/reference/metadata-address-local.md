---
description: Эта структура представляет адрес локальной переменной в области (обычно это функция или метод).
title: METADATA_ADDRESS_LOCAL | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fba3b02fde05655413f5826fa2a32645b5dc95f
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222410"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

Эта структура представляет адрес локальной переменной в области (обычно это функция или метод).

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagMETADATA_ADDRESS_LOCAL {
    _mdToken  tokMethod;
    IUnknown* pLocal;
    DWORD     dwIndex;
} METADATA_ADDRESS_LOCAL;
```

```csharp
public struct METADATA_ADDRESS_LOCAL {
    public int    tokMethod;
    public object pLocal;
    public uint   dwIndex;
}
```

## <a name="members"></a>Члены

`tokMethod`\
Идентификатор метода или функции, частью которой является локальная переменная.

[C++] `_mdToken` — `typedef` для 32-разрядного `int` .

`pLocal`\
Токен, адрес которого представляет эта структура.

`dwIndex`\
Может быть индексом этой локальной переменной в методе или функции или другим значением (зависящим от языка).

## <a name="remarks"></a>Комментарии

Эта структура является частью объединения в структуре [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , если `dwKind` поле `DEBUG_ADDRESS_UNION` структуры имеет `ADDRESS_KIND_LOCAL` значение (Value из перечисления [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

> [!WARNING]
> [Только C++] Если значение не равно `pLocal` null, необходимо вызвать `Release` для указателя токена ( `addr` является полем в структуре [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) ):
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Требования

Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел

- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
