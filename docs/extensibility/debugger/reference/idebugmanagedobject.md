---
description: Этот интерфейс позволяет средству оценки выражений (EE) вызывать свойства или методы для экземпляров класса значений (например, System. Decimal) и устанавливать их значения без вызова функции Evaluate для отлаживаемой программы.
title: Идебугманажедобжект | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7cb90893ab39a95dd3bd8046d8ba61a32064ccf7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165230"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс позволяет средству оценки выражений (EE) вызывать свойства или методы для экземпляров класса значений (например, `System.Decimal` ) и устанавливать их значения без вызова функции [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) для отлаживаемой программы.

## <a name="syntax"></a>Синтаксис

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений реализует этот интерфейс для представления объекта управляемого кода, например переменной.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Чтобы получить этот интерфейс, вызовите [жетманажеддебугобжект](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) для [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющего экземпляр класса значения.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованным от [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md), `IDebugManagedObject` интерфейс предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Возвращает интерфейс, представляющий объект управляемого кода и из которого можно получить любой соответствующий интерфейс управляемого кода.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Присваивает этому объекту значение указанного объекта управляемого кода.|

## <a name="remarks"></a>Комментарии
 Средство оценки выражений использует этот интерфейс для хранения объекта управляемого кода в дереве синтаксического анализа.

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Вычислить](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
