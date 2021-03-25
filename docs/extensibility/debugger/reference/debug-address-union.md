---
description: Описывает различные виды адресов.
title: DEBUG_ADDRESS_UNION | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71867a6a2cbaaf87b5b0a66eab5f53826fe47fdf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096438"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Описывает различные виды адресов.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Участники
`dwKind`\
Значение из перечисления [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , определяющее способ интерпретации объединения.

`addr.addrNative`\
[Только C++] Содержит структуру [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) , если имеет значение `dwKind` = ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[Только C++] Содержит структуру[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) , если имеет значение `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[Только C++] Содержит структуру[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) , если имеет значение `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[Только C++] Содержит структуру[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) , если имеет значение `dwKind` = ADDRESS_KIND_METHOD.

`addr.addrField`\
[Только C++] Содержит структуру[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) , если имеет значение `dwKind` = ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[Только C++] Содержит структуру[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) , если имеет значение `dwKind` = ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[Только C++] Содержит структуру[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) , если имеет значение `dwKind` = ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[Только C++] Содержит структуру[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) , если имеет значение `dwKind` = ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[Только C++] Содержит структуру[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) , если имеет значение `dwKind` = ADDRESS_KIND_RETVAL.

`addr.unused`\
[Только C++] заполнение.

`addr`\
[Только C++] Имя объединения.

`unionmember`\
[Только C#] Это значение должно быть упаковано в соответствующий тип структуры, основанный на `dwKind` . См. раздел Примечания для связи между `dwKind` и интерпретация объединения.

## <a name="remarks"></a>Remarks
Эта структура является частью структуры [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) и представляет один из нескольких различных типов адресов ( `DEBUG_ADDRESS` Структура заполняется вызовом метода методу method). [](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)

 [Только C#] В следующей таблице показано, как интерпретировать `unionmember` элемент для каждого типа адреса. В примере показано, как это делается для одного вида адреса.

|`dwKind`|`unionmember` интерпретируется как|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Пример
В этом примере показано, как интерпретировать один вид адреса ( `METADATA_ADDRESS_ARRAYELEM` ) `DEBUG_ADDRESS_UNION` структуры в C#. Остальные элементы могут интерпретироваться точно так же.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
            }
        }
    }
}
```

## <a name="requirements"></a>Требования
Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
