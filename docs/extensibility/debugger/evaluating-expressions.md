---
title: Вычисление выражений | Документация Майкрософт
description: Сведения о вычислении выражений, создаваемых из строк, передаваемых из окна "автоматические", "контрольные значения", "Быстрая проверка" или "Интерпретация".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4c79d27c01035f83b506ffad4ec138c8c68f98d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097036"
---
# <a name="evaluate-expressions"></a>Вычисление выражений
Выражения создаются на основе строк, переданных из окна " **Автоматические**", " **Контрольные значения**", " **Быстрая проверка**" или " **Интерпретация** ". При вычислении выражения создается печатная строка, содержащая имя и тип переменной или аргумента и его значение. Эта строка отображается в соответствующем окне интегрированной среды разработки.

## <a name="implementation"></a>Реализация
 Выражения оцениваются при остановке программы в точке останова. Само выражение представляет собой интерфейс [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , который представляет проанализированное выражение, готовое к привязке и вычислению в данном контексте вычисления выражения. Кадр стека определяет контекст вычисления выражения, предоставляемый модулем отладки (DE) путем реализации интерфейса [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .

 При наличии пользовательской строки и интерфейса [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) механизм отладки (de) может получить интерфейс [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , передав пользовательскую строку в метод [IDebugExpressionContext2::P арсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . Возвращаемый интерфейс IDebugExpression2 содержит проанализированное выражение, готовое для оценки.

 С помощью `IDebugExpression2` интерфейса de может получить значение выражения посредством синхронной или асинхронной оценки выражений с использованием [IDebugExpression2:: Евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [IDebugExpression2:: евалуатеасинк](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Это значение вместе с именем и типом переменной или аргумента отправляется в интегрированную среду разработки для вывода. Значение, имя и тип представлены интерфейсом [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .

 Чтобы включить вычисление выражений, в DE должны быть реализованы интерфейсы [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Для синхронной и асинхронной вычислений требуется реализация метода [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .

## <a name="see-also"></a>См. также
- [Кадры стека](../../extensibility/debugger/stack-frames.md)
- [Контекст вычисления выражения](../../extensibility/debugger/expression-evaluation-context.md)
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
