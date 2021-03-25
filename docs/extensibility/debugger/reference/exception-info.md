---
description: Описывает исключение или ошибку времени выполнения, вызванную отлаживаемой программой.
title: EXCEPTION_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ec97b56cc7fca8c2185d7180a8d34e87b084b11
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059474"
---
# <a name="exception_info"></a>EXCEPTION_INFO
Описывает исключение или ошибку времени выполнения, вызванную отлаживаемой программой.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagEXCEPTION_INFO {
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    BSTR            bstrExceptionName;
    DWORD           dwCode;
    EXCEPTION_STATE dwState;
    GUID            guidType;
} EXCEPTION_INFO;
```

```csharp
public struct EXCEPTION_INFO {
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public string         bstrExceptionName;
    public uint           dwCode;
    public uint           dwState;
    public Guid           guidType;
};
```

## <a name="members"></a>Участники
`pProgram`\
Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, в которой возникло исключение.

`bstrProgramName`\
Имя программы, в которой возникло исключение.

`bstrExceptionName`\
Имя исключения.

`dwCode`\
Идентификационный код для исключения или ошибки времени выполнения.

`dwState`\
Значение из перечисления [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) , определяющее состояние исключения.

`guidType`\
Идентификатор языка GUID: `guidLang` или `guidEng` .

## <a name="remarks"></a>Remarks
Эта структура передается в качестве параметра методам [сетексцептион](../../../extensibility/debugger/reference/idebugengine2-setexception.md) и [ремовесетексцептион](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) . Эта структура также передается в метод [except](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) , который должен быть заполнен.

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
