---
description: Позволяет узлу программы получать уведомления о попытке присоединения к связанной программе.
title: IDebugProgramNodeAttach2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aa623097224afc4f3a6b93d6b98ece0e14149ca5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171738"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Позволяет узлу программы получать уведомления о попытке присоединения к связанной программе.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется в том же классе, который реализует интерфейс [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , чтобы получить уведомление об операции присоединения и предоставить возможность отменить операцию присоединения.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Получите этот интерфейс, вызвав `QueryInterface` метод в объекте [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . Метод [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) должен вызываться перед методом [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) , чтобы дать узлу программы возможность прерывать процесс присоединения.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Присоединяется к связанной программе или откладывает процесс присоединения к методу [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .|

## <a name="remarks"></a>Комментарии
 Этот интерфейс является предпочтительным альтернативой нерекомендуемому методу [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) . Все модули отладки всегда загружаются с помощью `CoCreateInstance` функции, то есть они создаются за пределами адресного пространства отлаживаемой программы.

 Если предыдущая реализация `IDebugProgramNode2::Attach_V7` метода была просто настраивается `GUID` для отлаживаемой программы, необходимо реализовать только метод [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

 Если предыдущая реализация `IDebugProgramNode2::Attach_V7` метода использовала предоставленный интерфейс обратного вызова, то эта функциональность должна быть перемещена в реализацию метода [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) , а интерфейс не должен `IDebugProgramNodeAttach2` быть реализован.

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
