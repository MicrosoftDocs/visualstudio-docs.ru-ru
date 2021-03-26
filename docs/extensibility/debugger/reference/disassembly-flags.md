---
description: Задает флаги для дизассемблированного кода.
title: DISASSEMBLY_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28335176a70213f61bfbb77bf6f91cc6155902e7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096204"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Задает флаги для дизассемблированного кода.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>Поля
`DF_DOCUMENTCHANGE`\
Указывает, что эта инструкция находится в другом документе, отличном от предыдущего.

`DF_DISABLED`\
Указывает, что эта инструкция не будет выполнена.

`DF_INSTRUCTION_ACTIVE`\
Указывает, что эта инструкция является одной из следующих инструкций для выполнения (может быть несколько).

`DF_DATA`\
Указывает, что эта инструкция фактически является данными (а не кодом).

`DF_HASSOURCE`\
Указывает, что эта инструкция имеет источник. Некоторые инструкции, такие как профилирование или код сборки мусора, не имеют соответствующего источника.

`DF_DOCUMENT_CHECKSUM`\
Указывает, что `bstrDocumentUrl` поле содержит данные контрольной суммы после URL-адреса документа. Сведения о том, как хранятся данные контрольной суммы, см. в разделе "Примечания" для структуры [дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md) .

## <a name="remarks"></a>Remarks
Используется в качестве `dwFlags` члена структуры [дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md) .

Эти флаги можно сочетать с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
