---
description: Эта структура задает различные виды информации о типе поля.
title: TYPE_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e6b37fbc4d2d812bfa10d8f05455050bb5a239d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223424"
---
# <a name="type_info"></a>TYPE_INFO
Эта структура задает различные виды информации о типе поля.

## <a name="syntax"></a>Синтаксис

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>Члены
 `dwKind`\
 Значение из перечисления [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) , определяющее способ интерпретации объединения.

 `type.typeMeta`\
 [Только C++] Содержит структуру [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) , если `dwKind` имеет значение `TYPE_KIND_METADATA` .

 `type.typePdb`\
 [Только C++] Содержит структуру [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) , если `dwKind` имеет значение `TYPE_KIND_PDB` .

 `type.typeBuilt`\
 [Только C++] Содержит структуру [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) , если `dwKind` имеет значение `TYPE_KIND_BUILT` .

 `type.unused`\
 Неиспользуемое заполнение.

 `type`\
 Имя объединения.

 `unionmember`\
 [Только C#] Маршалирует его в соответствующий тип структуры, основанный на `dwKind` .

## <a name="remarks"></a>Комментарии
 Эта структура передается в метод [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) , где она заполнена. Степень интерпретации содержимого структуры основана на `dwKind` поле.

> [!NOTE]
> [Только C++] Если `dwKind` `TYPE_KIND_BUILT` значение равно, необходимо освободить базовый объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) при уничтожении `TYPE_INFO` структуры. Это выполняется с помощью вызова метода `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 [Только C#] В следующей таблице показано, как интерпретировать `unionmember` элемент для каждого типа. В примере показано, как это делается для одного типа.

|`dwKind`|`unionmember` интерпретируется как|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Пример
 В этом примере показано, как интерпретировать `unionmember` член `TYPE_INFO` структуры в C#. В этом примере показано, как интерпретируется только один тип (), но другие обрабатываются `TYPE_KIND_METADATA` точно так же.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
            }
        }
    }
}
```

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
