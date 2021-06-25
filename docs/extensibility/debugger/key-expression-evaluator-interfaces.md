---
title: Интерфейсы интерфейса средства оценки ключевых выражений | Документация Майкрософт
description: Узнайте о интерфейсах, с которыми следует ознакомиться при написании средства оценки выражений, а также в контексте оценки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: abfa4018e763bbbac5ff788f401d0ceb76eb97a1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901270"
---
# <a name="key-expression-evaluator-interfaces"></a>Интерфейсы средства оценки ключевых выражений
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 При написании оценщика выражений (EE) вместе с контекстом оценки необходимо ознакомиться со следующими интерфейсами.

## <a name="interface-descriptions"></a>Описания интерфейсов

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Содержит единственный метод,- [Address](../../extensibility/debugger/reference/idebugaddress-getaddress.md), который получает структуру данных, представляющую текущую точку выполнения. Эта структура данных является одним из трех аргументов, которые модуль отладки (DE) передает методу [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) для вычисления выражения. Этот интерфейс обычно реализуется поставщиком символов.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Имеет метод [BIND](../../extensibility/debugger/reference/idebugbinder-bind.md) , который получает область памяти, содержащую текущее значение символа. При наличии как содержащего метода, представленного объектом [идебугобжект](../../extensibility/debugger/reference/idebugobject.md) , так и самого символа, представленного объектом [идебугфиелд](../../extensibility/debugger/reference/idebugfield.md) , `IDebugBinder::Bind` возвращает значение символа. `IDebugBinder` обычно реализуется методом DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Представляет простой тип данных. Для более сложных типов, таких как массивы и методы, используйте производные интерфейсы [идебугаррайфиелд](../../extensibility/debugger/reference/idebugarrayfield.md) и [идебугмесодфиелд](../../extensibility/debugger/reference/idebugmethodfield.md) соответственно. [Идебугконтаинерфиелд](../../extensibility/debugger/reference/idebugcontainerfield.md) — это еще один важный производный интерфейс, который представляет символы, содержащие другие символы, такие как методы или классы. `IDebugField`Интерфейс (и его производные) обычно реализуется поставщиком символов.

     `IDebugField`Объект можно использовать для поиска имени и типа символа и, вместе с объектом [идебугбиндер](../../extensibility/debugger/reference/idebugbinder.md) , можно использовать для поиска его значения.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Представляет фактические биты значения символа времени выполнения. [BIND](../../extensibility/debugger/reference/idebugbinder-bind.md) принимает объект [идебугфиелд](../../extensibility/debugger/reference/idebugfield.md) , который представляет символ, и возвращает объект [идебугобжект](../../extensibility/debugger/reference/idebugobject.md) . Метод [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) возвращает значение символа в буфере памяти. Обычно DE реализует этот интерфейс для представления значения свойства в памяти.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Этот интерфейс представляет сам средство оценки выражений. Ключевой метод — это [синтаксический анализ](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), который возвращает интерфейс [идебугпарседекспрессион](../../extensibility/debugger/reference/idebugparsedexpression.md) .

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Этот интерфейс представляет проанализированное выражение, готовое для оценки. Ключевым методом является [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , который возвращает IDebugProperty2, представляющий значение и тип выражения.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Этот интерфейс представляет значение и его тип и является результатом вычисления выражения.

## <a name="see-also"></a>См. также
- [Контекст оценки](../../extensibility/debugger/evaluation-context.md)
