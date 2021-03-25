---
description: Отправляется из модуля отладки (DE) в Диспетчер отладки сеансов (SDM) при изменении имени программы.
title: IDebugProgramNameChangedEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 60fbc8aac3fd621a8f19074682bd82fbe957ed3b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053702"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Отправляется из модуля отладки (DE) в Диспетчер отладки сеансов (SDM) при изменении имени программы.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс для сообщения об изменении имени программы. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. Модель SDM использует [QueryInterface](/cpp/atl/queryinterface) для доступа к интерфейсу **IDebugEvent2** .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Параметр DE создает и отправляет этот объект события для сообщения об изменении имени программы. Метод DE отправляет это событие с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе. Поставщик пользовательского порта отправляет это событие с помощью интерфейса I.

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
