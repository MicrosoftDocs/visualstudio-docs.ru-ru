---
title: Контекст вычисления выражения | Документация Майкрософт
description: Сведения о контексте оценки выражений, который представляет контекст для оценки выражения и существует при остановке программы в точке останова.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73eeafb95c7e4d52f69109c5eb7c06eb48bd8d88
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901218"
---
# <a name="expression-evaluation-context"></a>Контекст вычисления выражения
При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладке **контекст вычисления выражения**:

- Представляет контекст для вычисления выражения. Как правило, контекст оценки соответствует лексической области, в которой оцениваются переменные, параметры, функции и методы. Например, контекст вычисления выражения, связанный с кадром стека, предоставит контекст для оценки локальных переменных, параметров метода и членов класса (если применимо).

- Существует, когда программа остановлена в точке останова. Само выражение представляет собой структуру данных, представляющую проанализированное выражение, готовое к привязке и вычислению в заданном контексте.

     Более подробно выражения создаются с помощью метода [парсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . При вычислении выражения создается печатная строка, содержащая имя и тип переменной или аргумента и его значение. Эта строка отображается в окно контрольных значений или в окне "Локальные" интегрированной среды разработки.

     При наличии `BSTR` интерфейса и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) механизм отладки (de) может создать интерфейс [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) путем синтаксического анализа выражения. При наличии `IDebugExpression2` интерфейса de может получить значение посредством синхронной или асинхронной оценки выражений. Это значение вместе с именем и типом переменной или аргумента отправляется в интегрированную среду разработки для вывода.

## <a name="see-also"></a>См. также
- [Интерфейсы оценки выражений](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
