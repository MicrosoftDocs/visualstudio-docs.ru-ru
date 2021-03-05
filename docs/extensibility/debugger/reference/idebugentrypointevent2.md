---
description: Модуль отладки (DE) отправляет этот интерфейс в Диспетчер отладки сеансов (SDM), когда программа собирается выполнить первую инструкцию пользовательского кода.
title: IDebugEntryPointEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da733292407c93327374a4c6fa54c558d3202caa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153395"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Модуль отладки (DE) отправляет этот интерфейс в Диспетчер отладки сеансов (SDM), когда программа собирается выполнить первую инструкцию пользовательского кода.

## <a name="syntax"></a>Синтаксис

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс в рамках обычных операций. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. Модель SDM использует [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейсу.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Параметр DE создает и отправляет этот объект события при загрузке отлаживаемой программы и готовности выполнить первую инструкцию пользовательского кода. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.

## <a name="remarks"></a>Комментарии
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) отправляется, когда программа собирается выполнить самую первую инструкцию. Например, `IDebugEntryPoint2` отправляется, когда программа собирается выполнить `main` функцию пользователя.

 Когда отсылается `IDebugEntryPointEvent2` , текущее расположение кода должно находиться в первой инструкции пользовательского кода, например `main` .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
