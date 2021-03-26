---
description: Указывает, какие сведения следует получить о поле дизассемблирования.
title: DISASSEMBLY_STREAM_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9241331e4e66c4a34a3afb29b54cf2ce6aab0e0f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096191"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Указывает, какие сведения следует получить о поле дизассемблирования.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>Поля
`DSF_ADDRESS`\
Инициализируйте или используйте `bstrAddress` поле.

`DSF_ADDRESSOFFSET`\
Инициализируйте или используйте `bstrAddressOffset` поле.

`DSF_CODEBYTES`\
Инициализируйте или используйте `bstrCodeBytes` поле.

`DSF_OPCODE`\
Инициализируйте или используйте `bstrOpCode` поле.

`DSF_OPERANDS`\
Инициализируйте или используйте `bstrOperands` поле.

`DSF_SYMBOL`\
Инициализируйте или используйте `bstrSymbol` поле.

`DSF_CODELOCATIONID`\
Инициализируйте или используйте `uCodeLocationId` поле.

`DSF_POSITION`\
Инициализируйте или используйте `posBeg` `posEnd` поля и.

`DSF_DOCUMENTURL`\
Инициализируйте или используйте `bstrDocumentUrl` поле.

`DSF_BYTEOFFSET`\
Инициализируйте или используйте `dwByteOffset` поле.

`DSF_FLAGS`\
Инициализируйте или используйте `dwFlags` поле ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)).

`DSF_OPERANDS_SYMBOLS`\
Включите в поле имена символов `bstrOperands` .

`DSF_ALL`\
Задает все поля для потока дизассемблированного кода.

## <a name="remarks"></a>Remarks
Передается в качестве параметра методу [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) , чтобы указать, какие поля структуры [дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md) должны быть инициализированы.

Используется для `dwFields` элемента `DisassemblyData` структуры, чтобы указать, какие поля используются и допустимы при возврате структуры.

Эти значения можно объединить с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
