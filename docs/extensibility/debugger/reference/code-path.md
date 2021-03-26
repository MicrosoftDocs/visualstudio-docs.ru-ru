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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b3e061fa0a9d6eb508e3085832007712cb6e434
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096516"
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

## <a name="members"></a>Участники
`bstrName`\
Имя пути кода.

`pCode`\
Объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , определяющий место в коде для пошагового перехода в функцию.

## <a name="remarks"></a>Remarks
Эта структура используется для реализации пошагового выполнения функции. [Енумкодепасс](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) возвращает все вызовы из текущего расположения в отлаживаемой программе. Эта структура представляет один такой вызов.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
