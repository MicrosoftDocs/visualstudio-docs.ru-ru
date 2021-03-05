---
description: Описывает кадр стека.
title: ФРАМЕИНФО | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8830e3917198cda10d9e4e0fb8919b1b56e84e9e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144095"
---
# <a name="frameinfo"></a>FRAMEINFO
Описывает кадр стека.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>Члены
`m_dwValidFields`\
Сочетание флагов из перечисления [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) , которое указывает, какие поля заполняются.

`m_bstrFuncName`\
Имя функции, связанной с кадром стека.

`m_bstrReturnType`\
Возвращаемый тип, связанный с кадром стека.

`m_bstrArgs`\
Аргументы функции, связанной с кадром стека.

`m_bstrLanguage`\
Язык, на котором реализована функция.

`m_bstrModule`\
Имя модуля, связанного с кадром стека.

`m_addrMin`\
Минимальный физический адрес стека.

`m_addrMAX`\
Максимальный физический адрес стека.

`m_pFrame`\
Объект [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , представляющий этот кадр стека.

`m_pModule`\
Объект [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , представляющий модуль, содержащий этот кадр стека.

`m_fHasDebugInfo`\
Ненулевое значение ( `TRUE` ), если отладочная информация существует в данном кадре.

`m_fStaleCode`\
Ненулевое значение ( `TRUE` ), если кадр стека связан с кодом, который больше не является допустимым.

`m_fAnnotatedFrame`\
Ненулевое значение ( `TRUE` ), если кадр стека снабжен заметками диспетчером отладки сеансов (SDM).

## <a name="remarks"></a>Комментарии
Эта структура передается в метод " [info](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) ", который должен быть заполнен. Эта структура также содержится в списке, который содержится в интерфейсе [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) , который, в свою очередь, возвращается из вызова метода [енумфрамеинфо](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
