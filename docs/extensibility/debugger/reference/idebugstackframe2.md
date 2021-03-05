---
description: Этот интерфейс представляет один кадр стека в стеке вызовов в определенном потоке.
title: IDebugStackFrame2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5ec53e89afb43187c641058620df53c4a61d6cc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145915"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Этот интерфейс представляет один кадр стека в стеке вызовов в определенном потоке.

## <a name="syntax"></a>Синтаксис

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления кадра стека.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [енумфрамеинфо](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) , чтобы получить интерфейс [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) . Чтобы получить структуру [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) , содержащую интерфейс, вызовите метод [Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) `IDebugStackFrame2` .

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugStackFrame2` .

|Метод|Описание|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Получает контекст кода для этого кадра стека.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Возвращает контекст документа для этого кадра стека.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Возвращает имя кадра стека.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Возвращает описание кадра стека.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Возвращает зависящее от компьютера представление диапазона физических адресов, связанных с кадром стека.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Возвращает контекст оценки для выполнения вычисления выражения в текущем контексте кадра стека и потока.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Возвращает язык, связанный с кадром стека.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Возвращает описание свойств, связанных с кадром стека.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Создает перечислитель для свойств кадра стека.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Возвращает поток, связанный с кадром стека.|

## <a name="remarks"></a>Комментарии
 Этот интерфейс получается, только если отлаживаемая программа остановлена в точке останова (вызванной точкой останова пользовательской установки или исключением). С помощью этого интерфейса можно получить контекст выражения для вычисления выражений, возвратить список регистров, а также получить и исследовать стек вызовов.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
