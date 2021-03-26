---
description: Задает область потока дизассемблированного кода.
title: DISASSEMBLY_STREAM_SCOPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 828d6b9afc659a09a4f1091c741e6246512de025
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096178"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Задает область потока дизассемблированного кода.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Поля
`DSS_HUGE`\
Указывает, что при разсборке контекста кода будет создаваться больше выходных данных, чем клиент, как правило, в одном вызове.

`DSS_FUNCTION`\
Указывает, что функция, содержащаяся в контексте кода, должна быть собрана. Указывает, что поток дизассемблированного кода представляет функцию, возвращаемую методом [superscope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .

`DSS_MODULE`\
При возврате `IDebugDisassemblyStream2::GetScope` методом указывает, что поток дизассемблированного кода представляет модуль.

`DSS_ALL`\
Указывает Дизассемблированный код для всего адресного пространства.

## <a name="remarks"></a>Remarks
Передается в качестве аргумента в метод [жетдисассемблистреам](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) и возвращается методом [superscope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .

Эти значения можно объединить с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
