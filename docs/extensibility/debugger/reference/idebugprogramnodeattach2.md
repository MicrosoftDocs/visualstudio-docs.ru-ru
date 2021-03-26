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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a1de6c7480e1ce4dcc0723614741a05dcc961a6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071471"
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

## <a name="remarks"></a>Remarks
 Этот интерфейс является предпочтительным альтернативой нерекомендуемому методу [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) . Все модули отладки всегда загружаются с помощью `CoCreateInstance` функции, то есть они создаются за пределами адресного пространства отлаживаемой программы.

 Если предыдущая реализация `IDebugProgramNode2::Attach_V7` метода была просто настраивается `GUID` для отлаживаемой программы, необходимо реализовать только метод [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

 Если предыдущая реализация `IDebugProgramNode2::Attach_V7` метода использовала предоставленный интерфейс обратного вызова, то эта функциональность должна быть перемещена в реализацию метода [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) , а интерфейс не должен `IDebugProgramNodeAttach2` быть реализован.

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
