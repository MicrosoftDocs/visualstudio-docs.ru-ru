---
description: Модуль отладки (DE) отправляет этот интерфейс в Диспетчер отладки сеансов (SDM) при создании экземпляра DE.
title: IDebugEngineCreateEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6155324150b963a5fd26ccecc1244e0792f448bc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153655"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
Модуль отладки (DE) отправляет этот интерфейс в Диспетчер отладки сеансов (SDM) при создании экземпляра DE.

## <a name="syntax"></a>Синтаксис

```
IDebugEngineCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс в рамках обычных операций. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс (модель SDM использует `QueryInterface` для доступа к `IDebugEvent2` интерфейсу метод).

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Параметр DE создает и отправляет этот объект события при создании экземпляра DE. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEngineCreateEvent2` .

|Метод|Описание|
|------------|-----------------|
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|Извлекает объект, представляющий только что созданный модуль отладки (DE).|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
