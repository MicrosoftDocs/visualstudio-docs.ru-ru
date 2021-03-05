---
description: Этот интерфейс используется модулем отладки (DE) для отправки событий отладки в Диспетчер отладки сеансов (SDM).
title: IDebugEventCallback2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb33bcbdff14b0f95aab5d8f300473c13d4c342f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152914"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Этот интерфейс используется модулем отладки (DE) для отправки событий отладки в Диспетчер отладки сеансов (SDM).

## <a name="syntax"></a>Синтаксис

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] реализует этот интерфейс для получения событий от модуля отладки.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Модуль отладки обычно получает этот интерфейс, когда SDM вызывает [Присоединение](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md)или [лаунчсуспендед](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Модуль отладки отправляет события в SDM, вызывая [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEventCallback2` .

|Метод|Описание|
|------------|-----------------|
|[Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Отправляет уведомление о событиях отладки в SDM.|

## <a name="remarks"></a>Комментарии
 Хотя [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) и [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) указывают, что они принимают `IDebugEventCallback2` интерфейс, это не так, а указатель интерфейса всегда будет иметь значение null. Вместо этого модуль отладки должен использовать интерфейс, `IDebugEventCallback2` полученный в вызове для [присоединения](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [присоединения](../../../extensibility/debugger/reference/idebugengine2-attach.md)или [лаунчсуспендед](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Если пакет реализует [идебужевенткаллбакк](../../../extensibility/debugger/reference/idebugeventcallback2.md) в управляемом коде, настоятельно рекомендуется <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> вызывать его для различных интерфейсов, передаваемых в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
