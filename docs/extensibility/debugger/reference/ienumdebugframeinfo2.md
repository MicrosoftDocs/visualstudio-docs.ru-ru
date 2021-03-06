---
description: Этот интерфейс перечисляет структуры ФРАМЕИНФО.
title: IEnumDebugFrameInfo2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a0351e1eb964506074c13dd68e9eb132ee5b578
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091673"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Этот интерфейс перечисляет структуры [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) .

## <a name="syntax"></a>Синтаксис

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс, чтобы предоставить список структур, описывающих текущий стек вызовов.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Visual Studio вызывает [енумфрамеинфо](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) для получения этого интерфейса всякий раз, когда в отлаживаемой программе происходит точка останова, исключение или остановка.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugFrameInfo2` .

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Извлекает указанное число структур [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Пропускает указанное число структур [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) в последовательности перечисления.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Возвращает число структур [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) в перечислителе.|

## <a name="remarks"></a>Remarks
 Visual Studio получает этот интерфейс в качестве первого шага для обработки точки останова, исключения или созданной пользователем паузы в отлаживаемой программе. Список структур [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) представляет текущий стек вызовов с текущим вызовом функции в начале списка и самым старым вызовом функции в конце списка. Каждый `FRAMEINFO` представляет кадр стека, контекст, в котором выражения могут оцениваться, и локальные переменные, которые были просмотрены.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
