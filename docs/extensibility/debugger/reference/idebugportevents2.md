---
description: Этот интерфейс уведомляет прослушиватель (как правило, диспетчер отладки сеанса [SDM] или модуль отладки) о создании и уничтожении процессов и программ на определенном порте.
title: IDebugPortEvents2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8e1ccbb2726fb0f90fae2d31a4b07daad9bae91
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065389"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Этот интерфейс уведомляет прослушиватель (как правило, диспетчер отладки сеанса [SDM] или модуль отладки) о создании и уничтожении процессов и программ на определенном порте. Эти сведения можно использовать для представления процессов и программ, выполняемых на порту в режиме реального времени.

## <a name="syntax"></a>Синтаксис

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio обычно реализует этот интерфейс для получения уведомлений о создании и уничтожении программ. Модуль отладки также может реализовать этот интерфейс для прослушивания таких событий порта.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Для [](../../../extensibility/debugger/reference/idebugport2.md) интерфейса можно запрашивать все интерфейсы IDebugPort2 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> . Затем <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> метод для `IDebugPortEvents2` вызывается в <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейсе для получения <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейса. Наконец, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> метод в <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейсе вызывается для отправки событий с помощью метода [события](../../../extensibility/debugger/reference/idebugportevents2-event.md) .

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показан метод `IDebugPortEvents2` .

|Метод|Описание|
|------------|-----------------|
|[Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Отправляет события, описывающие создание и уничтожение процессов и программ в порте.|

## <a name="remarks"></a>Remarks
 `IDebugPortEvents2` также используется SDM для отладки программ, выполняемых в процессе, который уже отлаживается.

 События порта передаются в SDM с помощью этого интерфейса.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
