---
description: Этот интерфейс отправляется модулем отладки (DE) в Диспетчер отладки сеансов (SDM) для вывода строки.
title: IDebugOutputStringEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4576914ada9a575569ce09c120dbbd9bc11fdfa9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084653"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Этот интерфейс отправляется модулем отладки (DE) в Диспетчер отладки сеансов (SDM) для вывода строки.

## <a name="syntax"></a>Синтаксис

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс для отправки строки в окно **вывода** интегрированной среды разработки. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. Модель SDM использует [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейсу.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Параметр DE создает и отправляет этот объект события для отправки строки в окно **вывода** . Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показан метод `IDebugOutputStringEvent2` .

|Метод|Описание|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Возвращает отображаемое сообщение.|

## <a name="remarks"></a>Remarks
 Например, в неуправляемом коде строка для вывода может быть создана, когда отлаживаемая программа отправляет строку в `OutputDebugString` функцию Win32. Эта строка перехватывается методом DE и отправляется в SDM в качестве `IDebugOutputStringEvent2` события.

 Используйте [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) для отправки сообщения, требующего ответа пользователя.

 Используйте [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) для отправки сообщения об ошибке, не требующего ответа.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
