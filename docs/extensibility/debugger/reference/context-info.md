---
description: Эта структура описывает контекст памяти или контекст кода.
title: CONTEXT_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc0636334cfde4452f427285bfe21141bc7614e1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170735"
---
# <a name="context_info"></a>CONTEXT_INFO
Эта структура описывает контекст памяти или контекст кода.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Члены
`dwFields`\
Сочетание флагов из [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) перечисление, которое указывает, какие поля заполняются<strong>.</strong>

`bstrModuleUrl`\
Имя модуля, в котором находится контекст.

`bstrFunction`\
Имя функции, в которой находится контекст.

`posFunctionOffset`\
Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , определяющая смещение строки и столбца функции, связанной с контекстом кода.

`bstrAddress`\
Адрес в коде, где находится заданный контекст.

`bstrAddressOffset`\
Смещение адреса в коде, где находится заданный контекст.

`bstrAddressAbsolute`\
Абсолютный адрес в памяти, где находится заданный контекст.

## <a name="remarks"></a>Комментарии
Эта структура возвращается из вызова метода " [info](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) ".

Типичное использование этой структуры — поддержка окна отладки **памяти** .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
