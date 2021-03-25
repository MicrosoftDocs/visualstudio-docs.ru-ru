---
description: Этот интерфейс указывает сообщение об ошибке, которое будет сообщено пользователю.
title: IDebugErrorEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d531180ca2fad9a6605837105c4ec5d626584a19
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054235"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
Этот интерфейс указывает сообщение об ошибке, которое будет сообщено пользователю.

## <a name="syntax"></a>Синтаксис

```
IDebugErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс, чтобы сообщать об ошибках в виде сообщений, доступных для чтения человеком. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. Модель SDM использует [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейсу.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Параметр DE создает и отправляет этот объект события для сообщения об ошибке. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|`GetErrorMessage`|Возвращает ошибку как удобочитаемую строку.|

## <a name="remarks"></a>Remarks
 Если модуль отладки обнаруживает ошибку, он может использовать этот интерфейс для передачи сообщения пользователю в Visual Studio.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
