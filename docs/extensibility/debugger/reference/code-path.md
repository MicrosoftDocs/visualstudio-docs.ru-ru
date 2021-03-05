---
description: Описывает метод или вызов функции.
title: CODE_PATH | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ecdbbfdbcffbb8b1aa6246e2e99ef6eabfa1f19
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170963"
---
# <a name="code_path"></a>CODE_PATH
Описывает метод или вызов функции.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagCODE_PATH { 
    BSTR                bstrName;
    IDebugCodeContext2* pCode;
} CODE_PATH;
```

```csharp
public struct CODE_PATH {
    public string            bstrName;
    public IDebugCodeContext pCode;
}
```

## <a name="members"></a>Члены
`bstrName`\
Имя пути кода.

`pCode`\
Объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , определяющий место в коде для пошагового перехода в функцию.

## <a name="remarks"></a>Комментарии
Эта структура используется для реализации пошагового выполнения функции. [Енумкодепасс](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) возвращает все вызовы из текущего расположения в отлаживаемой программе. Эта структура представляет один такой вызов.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
