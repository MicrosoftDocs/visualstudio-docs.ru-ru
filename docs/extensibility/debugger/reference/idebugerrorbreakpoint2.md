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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c2ceedbf0fad2141f978420909d31be2260818c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065935"
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

## <a name="see-also"></a>См. также
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [Вперед](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
