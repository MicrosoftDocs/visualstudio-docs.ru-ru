---
description: Этот интерфейс отправляется модулем отладки (DE) в Диспетчер отладки сеансов (SDM) после пошагового завершения или над функцией.
title: IDebugReturnValueEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReturnValueEvent2
helpviewer_keywords:
- IDebugReturnValueEvent2
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 17eafb8f974c193fd4796cd246bf7e0a1abe929a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075709"
---
# <a name="idebugreturnvalueevent2"></a>IDebugReturnValueEvent2
Этот интерфейс отправляется модулем отладки (DE) в Диспетчер отладки сеансов (SDM) после пошагового завершения или над функцией.

## <a name="syntax"></a>Синтаксис

```
IDebugReturnValueEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс, чтобы сообщить возвращаемое значение из функции, которая была повышена или выше. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. Модель SDM использует [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейсу.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Параметр DE создает и отправляет этот объект события, чтобы сообщить возвращаемое значение функции. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показан метод `IDebugReturnValueEvent2` .

|Метод|Описание|
|------------|-----------------|
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|Возвращает значение, возвращаемое при пошаговом выполнении функции.|

## <a name="remarks"></a>Remarks
 Значение, возвращаемое функцией, можно получить путем вызова [жетретурнвалуе](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md). Возвращаемое значение отображается в окне **видимые** .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
