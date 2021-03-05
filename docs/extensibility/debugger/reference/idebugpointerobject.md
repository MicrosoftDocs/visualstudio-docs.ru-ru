---
description: Этот интерфейс представляет объект указателя.
title: Идебугпоинтеробжект | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e5275116ae16c03c4784cda7f227c46f57681120
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169617"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс представляет объект указателя.

## <a name="syntax"></a>Синтаксис

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений реализует этот интерфейс для представления объекта указателя.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Интерфейс [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) может получить этот интерфейс с помощью [QueryInterface](/cpp/atl/queryinterface) , если объект `IDebugObject` представляет указатель.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованным от [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md), `IDebugPointerObject` интерфейс предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Возвращает объект, на который указывает интерфейс.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Возвращает значение, на которое интерфейс указывает последовательность последовательных байтов.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Задает значение, на которое интерфейс указывает последовательность последовательных байтов.|

## <a name="remarks"></a>Комментарии
 Средство оценки выражений использует этот интерфейс для представления указателя в дереве синтаксического анализа.

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
