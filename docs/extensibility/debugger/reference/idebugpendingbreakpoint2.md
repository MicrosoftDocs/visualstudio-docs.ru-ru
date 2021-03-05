---
description: Этот интерфейс представляет точку останова, готовую к привязке к расположению кода.
title: IDebugPendingBreakpoint2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05e66a0066abca5fb657960f2042b738a10e59ca
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169734"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Этот интерфейс представляет точку останова, готовую к привязке к расположению кода.

## <a name="syntax"></a>Синтаксис

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс в рамках поддержки точек останова.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов [креатепендингбреакпоинт](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) создает отложенную точку останова из интерфейса [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) . Вызов [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) создает `IDebugBreakpoint2` интерфейс, представляющий связанную точку останова в программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugPendingBreakpoint2` .

|Метод|Описание|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Определяет, может ли отложенная точка останова быть привязана к расположению кода.|
|[Выполняется](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Привязывает эту отложенную точку останова к одному или нескольким расположениям кода.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Возвращает состояние этой ожидающей точки останова.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Получает запрос точки останова, который использовался для создания этой ожидающей точки останова.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Переключает виртуализированное состояние этой ожидающей точки останова.|
|[Разрешить](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Переключает включенное состояние ожидающей точки останова.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Задает или изменяет условие, связанное с этой ожидающей точкой останова.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Задает или изменяет число проходов, связанных с этой ожидающей точкой останова.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Перечисляет все точки останова, привязанные к этой ожидающей точке останова.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Перечисляет все точки останова, которые привели к возникновению этой ожидающей точки останова.|
|[Удаление](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Удаляет данную отложенную точку останова и все точки останова, привязанные к ней.|

## <a name="remarks"></a>Комментарии
 `IDebugPendingBreakpoint2` можно рассматривать как поставщик всех необходимых сведений, необходимых для привязки точки останова к коду, который может быть применен к одной или нескольким программам.

 Ожидающая точка останова может привести к созданию более чем одной привязанной точки останова. Например, точка останова в шаблоне в стиле C++ может создать привязанную точку останова для каждого уникального экземпляра этого шаблона.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
