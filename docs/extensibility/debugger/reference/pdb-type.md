---
description: Эта структура задает сведения о типе поля, взятого из символа PDB.
title: PDB_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ced96c1241c64abc764a052046e5ecab1a986bdc
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222137"
---
# <a name="pdb_type"></a>PDB_TYPE

Эта структура задает сведения о типе поля, взятого из символа PDB.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>Члены

`ulAppDomainID`\
Идентификатор приложения, от которого получен символ. Используется для уникальной идентификации экземпляра приложения.

`guidModule`\
Идентификатор GUID модуля, содержащего это поле.

`symid`\
ИДЕНТИФИКАТОР символа, соответствующего этому полю.

## <a name="remarks"></a>Комментарии

Эта структура отображается как часть объединения в структуре [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) , если `dwKind` поле `TYPE_INFO` структуры имеет `TYPE_KIND_PDB` значение (Value из перечисления [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

## <a name="requirements"></a>Требования

Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел

- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
