---
description: Этот интерфейс представляет сведения, описывающие связанную точку останова.
title: IDebugBreakpointResolution2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 31543b574006609cb22e6cf505771840678a97fa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143328"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Этот интерфейс представляет сведения, описывающие связанную точку останова.

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс в рамках поддержки точек останова. Этот интерфейс предоставляет описание привязанной точки останова, которую диспетчер отладки сеанса использует, когда пользователь просматривает свойства точки останова.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов [жетбреакпоинтресолутион](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugBreakpointResolution2` .

|Метод|Описание|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Возвращает тип точки останова, представленной этим разрешением.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешении точки останова, описывающие эту точку останова.|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
