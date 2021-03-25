---
description: Этот метод отправляет события, которые обозначают создание и уничтожение процессов и программ на порте.
title: 'IDebugPortEvents2:: Event | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 314c31c426300c31f90813e2b73b150678578437
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058343"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Этот метод отправляет события, которые обозначают создание и уничтожение процессов и программ на порте.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>Параметры
`pMachine`\
окне Объект [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , представляющий сервер отладки (по одному для каждого экземпляра [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ), в котором произошло событие.

`pPort`\
окне Объект [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , представляющий порт, в котором произошло событие.

`pProcess`\
окне Объект [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий процесс, в котором произошло событие.

`pProgram`\
окне Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, в которой произошло событие.

`pEvent`\
окне Объект [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , определяющий событие. Возможны следующие события.

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
окне Идентификатор GUID события. Так как событие приводится к [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) перед вызовом этого метода, этот идентификатор упрощает определение того, какое событие отправляется.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
