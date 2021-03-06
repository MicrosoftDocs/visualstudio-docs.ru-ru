---
description: Этот интерфейс представляет коллекцию объектов, реализующих интерфейс Идебугобжект.
title: Иенумдебугобжектс | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eece06d64a4eeefefe4e132295f20e40a032434b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224633"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс представляет коллекцию объектов, реализующих интерфейс [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) .

## <a name="syntax"></a>Синтаксис

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений реализует этот интерфейс для предоставления наборов объектов, реализующих интерфейс [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) . Обратите внимание, что это не стандартное перечисление COM из-за наличия метода [NOCOUNT](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
- Функция " [элементы](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) " возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Извлекает из перечисления следующий набор объектов [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) .|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Пропускает указанное число записей.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Сбрасывает перечисление до первой записи.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Извлекает копию текущего перечисления.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Возвращает количество записей в перечислении.|

## <a name="remarks"></a>Комментарии
 Этот интерфейс позволяет модулю отладки перечислять набор объектов в массиве.

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
