---
title: 'IDebugProgramNode2:: Attach_V7 | Документация Майкрософт'
description: Этот метод интерфейса является старым, устаревшим методом присоединения, который использовался до Visual Studio 2005.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c949bba45457917e4dd00bdc05bc300f3a38eb7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053598"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Не рекомендуется. НЕ ИСПОЛЬЗУЙТЕ.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>Параметры

`pMDMProgram`\
окне Интерфейс [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, к которой нужно присоединиться.

`pCallback`\
окне Интерфейс [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , который будет использоваться для отправки событий отладки в SDM.

`dwReason`\
окне Значение из перечисления [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) , указывающее причину присоединения.

## <a name="return-value"></a>Возвращаемое значение

Реализация всегда должна возвращать `E_NOTIMPL` .

## <a name="remarks"></a>Remarks

> [!WARNING]
> Начиная с Visual Studio 2005 этот метод больше не используется и всегда должен возвращать `E_NOTIMPL` . См. интерфейс [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) для альтернативного подхода, если узлу программы нужно указать, что он не может быть присоединен к, или если узел программы просто настраивает программу `GUID` . В противном случае реализуйте метод [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="prior-to-visual-studio-2005"></a>До Visual Studio 2005

Этот метод необходимо реализовать только в том случае, если в адресном пространстве программы выполняется отладка. В противном случае этот метод должен возвращать значение `S_FALSE` .

При вызове этого метода метод DE должен отправить объект события [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) , если он еще не был отправлен для этого экземпляра интерфейса [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , а также объекты событий [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) и [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) . Затем объект события [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) отправляется, если `dwReason` параметр имеет значение `ATTACH_REASON_LAUNCH` .

Параметр DE должен вызывать метод [жетпрограмид](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) для объекта [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , предоставленного объектом события [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , и должен хранить идентификатор GUID этой программы в данных экземпляра для `IDebugProgram2` объекта, реализованного методом de.

## <a name="see-also"></a>См. также

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
