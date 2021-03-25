---
description: Этот интерфейс перечисляет потоки, выполняющиеся в текущем сеансе отладки.
title: IEnumDebugThreads2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97cb6f4d0425fb75ebaa9375e53e3ba6d5075e00
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082651"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Этот интерфейс перечисляет потоки, выполняющиеся в текущем сеансе отладки.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления списка потоков в программе.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) , чтобы получить этот интерфейс, представляющий список всех потоков во всех программах, выполняющихся в процессе. Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) , чтобы получить этот интерфейс, представляющий список потоков, выполняющихся в программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugThreads2` .

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Извлекает указанное число потоков в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Пропускает указанное число потоков в последовательности перечисления.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Возвращает число потоков в перечислителе.|

## <a name="remarks"></a>Remarks
 Visual Studio обычно получает этот интерфейс для обновления окна **потоков** , а также для получения первого потока списка для вызова [EXECUTE](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)и [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
