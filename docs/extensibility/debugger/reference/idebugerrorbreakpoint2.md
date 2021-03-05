---
description: Этот интерфейс представляет точку останова в виде ошибки или предупреждения, например недопустимое расположение, недопустимое выражение или причины, по которым не была привязана точка останова (код еще не загружен и т. д.).
title: IDebugErrorBreakpoint2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91697ebad462f3d1e953aa42d74bf5a96757886a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153161"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
Этот интерфейс представляет точку останова в виде ошибки или предупреждения, например недопустимое расположение, недопустимое выражение или причины, по которым не была привязана точка останова (код еще не загружен и т. д.).

## <a name="syntax"></a>Синтаксис

```
IDebugErrorBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки реализует этот интерфейс в рамках поддержки точек останова. Этот интерфейс используется для сообщения о проблемах привязки точки останова.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов [жетеррорбреакпоинт](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) получает этот интерфейс. Этот интерфейс также может быть возвращен (как часть списка, представленного интерфейсом [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) ) путем вызова [канбинд](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) или [енумеррорбреакпоинтс](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugErrorBreakpoint2` .

|Метод|Описание|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Возвращает ожидающую точку останова, вызвавшую ошибку.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Возвращает разрешение ошибки точки останова, описывающее ошибку.|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [Вперед](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
