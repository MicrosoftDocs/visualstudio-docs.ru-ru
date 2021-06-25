---
title: Вычисление выражений (пакет SDK для отладки Visual Studio) | Документация Майкрософт
description: В режиме приостановки выполнения среда IDE вычисляет выражения, содержащие переменные программы. Узнайте, как модуль отладки анализирует и оценивает выражение.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf213c30ef26490b44579d83c68b2640360584a7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904517"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Вычисление выражений (пакет SDK для отладки Visual Studio)
В режиме приостановки выполнения среда IDE должна оценивать простые выражения, включающие в себя несколько переменных программы. Чтобы выполнить оценку, модуль отладки (DE) должен проанализировать и оценить выражение, введенное в одно из окон интегрированной среды разработки.

 Выражения создаются с помощью метода [IDebugExpressionContext2::P арсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) и представляются результирующим интерфейсом [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .

 Интерфейс **IDebugExpression2** реализуется методом de и вызывает его метод **еваласинк** для возврата интерфейса [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) в интегрированную среду разработки для отображения результатов вычисления выражений в интегрированной среде разработки. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) возвращает структуру, которая используется для помещения значения выражения в окно " **Контрольные значения** " или в окно " **локальные** ".

 Пакет отладки или диспетчер отладки сеансов (SDM) вызывает [IDebugExpression2:: евалуатеасинк](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) или [евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , чтобы получить интерфейс [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , представляющий результат вычисления. `IDebugProperty2` содержит методы, возвращающие имя, тип и значение выражения. Эти сведения отображаются в различных окнах отладчика.

## <a name="using-expression-evaluation"></a>Использование вычисления выражений
 Чтобы использовать вычисление выражений, необходимо реализовать метод [IDebugExpressionContext2::P арсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) и все методы интерфейса [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , как показано в следующей таблице.

|Метод|Описание|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Асинхронно вычисляет выражение.|
|[Прерывание](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Завершает вычисление асинхронного выражения.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Синхронно вычисляет выражение.|

 Синхронная и асинхронная Оценка требует реализации метода [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Для вычисления асинхронного выражения требуется реализация [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>См. также
- [Контроль выполнения и оценка состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
