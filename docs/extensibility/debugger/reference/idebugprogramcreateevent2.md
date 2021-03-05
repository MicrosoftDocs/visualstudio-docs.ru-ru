---
description: Этот интерфейс отправляется модулем отладки (DE) в Диспетчер отладки сеансов (SDM) при присоединении программы к.
title: IDebugProgramCreateEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 535d54e0c7cdd4b175cd76c9d1fbe9ce240b5ccf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151627"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Этот интерфейс отправляется модулем отладки (DE) в Диспетчер отладки сеансов (SDM) при присоединении программы к.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик DE или пользовательский порт реализует этот интерфейс, чтобы сообщить о том, что программа была создана, как правило, в момент, когда программа подключена к. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. Модель SDM использует `QueryInterface` метод для доступа к `IDebugEvent2` интерфейсу.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Поставщик DE или пользовательский порт создает и отправляет этот объект события для сообщения о создании программы. Метод DE отправляет это событие с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе. Поставщик пользовательского порта отправляет это событие с помощью интерфейса [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .

## <a name="remarks"></a>Комментарии
 Поставщик DE или пользовательского порта публикует новый интерфейс [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , вызывая [публишпрограмноде](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
