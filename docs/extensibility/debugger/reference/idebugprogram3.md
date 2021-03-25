---
description: Этот интерфейс представляет программу, выполняемую в процессе, и расширяет Execute, предоставляя сведения о потоке.
title: IDebugProgram3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 339aff9bdd41a27f48ef1a7ef1e01d9529835403
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084341"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Этот интерфейс представляет программу, выполняемую в процессе, и расширяет [EXECUTE](../../../extensibility/debugger/reference/idebugprogram2-execute.md) , предоставляя сведения о потоке.

## <a name="syntax"></a>Синтаксис

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) и поставщик пользовательского порта реализуют этот интерфейс для представления программы в процессе. Диспетчер отладки сеансов (SDM) также реализует этот интерфейс для предоставления сведений для [присоединения](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Событие [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) возвращает этот интерфейс для новой программы. Этот интерфейс также используется в качестве параметра для многих методов в нескольких интерфейсах.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgram3` .

|Метод|Описание|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Выполняет программу. Поток возвращается, чтобы предоставить сведения отладчика о том, какой поток пользователь просматривает при выполнении.|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Remarks
 Программа — это контейнер потоков, выполняющийся в определенной архитектуре среды выполнения, в то время как процесс состоит из одной или нескольких программ.

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Вперед](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
