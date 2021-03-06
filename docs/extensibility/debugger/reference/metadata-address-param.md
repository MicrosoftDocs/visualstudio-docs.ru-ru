---
description: Эта структура представляет параметр метода или функции.
title: METADATA_ADDRESS_PARAM | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_PARAM
helpviewer_keywords:
- METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3317981def12a72cf98dad850d5509bd3e64520a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222384"
---
# <a name="metadata_address_param"></a>METADATA_ADDRESS_PARAM
Эта структура представляет параметр метода или функции.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagMETADATA_ADDRESS_PARAM {
   _mdToken tokMethod;
   _mdToken tokParam;
   DWORD    dwIndex;
} METADATA_ADDRESS_PARAM;
```

```csharp
public struct METADATA_ADDRESS_PARAM {
   public int  tokMethod;
   public int  tokParam;
   public uint dwIndex;
}
```

## <a name="members"></a>Члены
 `tokMethod`\
 Идентификатор метода, частью которого является параметр.

 `tokParam`\
 Идентификатор параметра.

 `dwIndex`\
 Индекс параметра в списке параметров.

## <a name="remarks"></a>Комментарии
 Эта структура является частью объединения в структуре [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , если `dwKind` поле `DEBUG_ADDRESS_UNION` структуры имеет `ADDRESS_KIND_PARAM` значение (Value из перечисления [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
