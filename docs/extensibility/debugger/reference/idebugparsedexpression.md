---
description: Этот интерфейс представляет проанализированное выражение, готовое для оценки.
title: Идебугпарседекспрессион | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 00daeac20d621657d61aa802d79a46a3ee0e7aa7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084588"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс представляет проанализированное выражение, готовое для оценки.

## <a name="syntax"></a>Синтаксис

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений реализует этот интерфейс для представления проанализированного выражения, готового к оценке.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показан метод `IDebugParsedExpression` .

|Метод|Описание|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Вычисляет проанализированное выражение.|

## <a name="remarks"></a>Remarks
 Когда вызывающий объект готов к вычислению выражения, он вызывает [евалуатесинк](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , чтобы вернуть [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , содержащий результат вычисления. Этот подход к вычислению и анализу, который затем вычисляется, позволяет вычислять проанализированное выражение несколько раз, обходя трудоемкий процесс синтаксического анализа выражения.

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
