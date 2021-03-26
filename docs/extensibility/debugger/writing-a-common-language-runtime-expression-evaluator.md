---
title: Написание средства оценки выражений среды CLR | Документация Майкрософт
description: Узнайте, как написать средство оценки выражений для среды CLR, которое оценивает выражения в языке кода, который отлаживается.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 658158785d8f8a9376f5357ae2b869f6ad2e2271
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091400"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Написание вычислителя выражений среды CLR
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Средство оценки выражений (EE) является частью модуля отладки (DE), который обрабатывает синтаксис и семантику языка программирования, создавшего отлаживаемый код. Выражения должны оцениваться в контексте языка программирования. Например, в некоторых языках выражение «A + B» означает «сумму A и б». В других языках одно и то же выражение может означать "A или B". Поэтому отдельный EE должен быть написан для каждого языка программирования, который создает объектный код для отладки в интегрированной среде разработки Visual Studio.

 Некоторые аспекты пакета отладки Visual Studio должны интерпретировать код в контексте языка программирования. Например, при остановке выполнения в точке останова все выражения, вводимые пользователем в окно **контрольных значений** , должны оцениваться и отображаться. Пользователь может изменить значение локальной переменной, введя выражение в окно **контрольных значений** или в окно **Immediate** .

## <a name="in-this-section"></a>Содержание раздела
 [Среда CLR и вычисление выражений](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Объясняется, что при интеграции собственного языка программирования в интегрированную среду разработки Visual Studio написание EE с поддержкой оценки выражений в контексте собственного языка позволяет компилироваться на языке MSIL без написания модуля отладки.

 [Архитектура средства оценки выражений](../../extensibility/debugger/expression-evaluator-architecture.md) Описывает, как реализовать требуемые интерфейсы EE и вызывать интерфейсы поставщика символов среды CLR (SP) и связывателя.

 [Регистрация средства оценки выражений](../../extensibility/debugger/registering-an-expression-evaluator.md) Заметок о том, что EE должен зарегистрировать себя как фабрика класса как в среде CLR, так и в среде выполнения Visual Studio.

 [Реализация средства оценки выражений](../../extensibility/debugger/implementing-an-expression-evaluator.md) Описывает, как процесс вычисления выражения включает в себя модуль отладки (DE), поставщик символов (SP), объект связывателя и средство оценки выражений (EE).

 [Отобразить локальные переменные](../../extensibility/debugger/displaying-locals.md) Описывает, как, когда выполнение приостанавливается, пакет отладки вызывает метод DE для получения списка локальных переменных и аргументов.

 [Вычисление выражения окна контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Документируется, как пакет отладки Visual Studio вызывает метод DE для определения текущего значения каждого выражения в его списке контрольных значений.

 [Изменение значения локального](../../extensibility/debugger/changing-the-value-of-a-local.md) Объясняется, что при изменении значения локальной каждой строки в окне Локальные переменные имеется связанный объект, предоставляющий имя, тип и текущее значение локального объекта.

 [Реализация визуализаторов типов и пользовательских средств просмотра](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Описывает интерфейс, который должен быть реализован компонентом для поддержки визуализаторов типов и пользовательских средств просмотра.

## <a name="see-also"></a>См. также
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
