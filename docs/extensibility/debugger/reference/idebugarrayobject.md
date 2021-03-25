---
description: Этот интерфейс представляет объект массива.
title: Идебугаррайобжект | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e27f40a3f8a54c9cda285ba30bdcbc53472aab59
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078114"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс представляет объект массива.

## <a name="syntax"></a>Синтаксис

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений реализует этот интерфейс для представления массива.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Интерфейс [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) может получить этот интерфейс с помощью [QueryInterface](/cpp/atl/queryinterface) , если объект представляет массив.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов `IDebugObject` интерфейса, в интерфейсе реализуются следующие методы `IDebugArrayObject` .

|Метод|Описание|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Возвращает число элементов в массиве.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Возвращает элемент массива.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Возвращает все элементы массива.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Возвращает ранг массива.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Возвращает размеры массива.|

## <a name="remarks"></a>Remarks
 Средство оценки выражений использует этот интерфейс для представления массивов в дереве синтаксического анализа.

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
