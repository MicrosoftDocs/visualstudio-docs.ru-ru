---
title: Управление выполнением и оценка состояния | Документация Майкрософт
description: Узнайте, как в Visual Studio Отладка основывается на событиях, передаваемых между компонентами отладчика.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 598332ec1e9e1cb270360822ca32792b9a53f5c1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096958"
---
# <a name="execution-control-and-state-evaluation"></a>Контроль выполнения и оценка состояния
Отладка приложения требует реализации таких функций управления выполнением, как шаг с заходом в функции, остановка в точках останова и продолжение выполнения. Visual Studio Debugging управляет выполнением событий, передаваемых между компонентами отладчика.

## <a name="in-this-section"></a>Содержание раздела
 [Управление программой](../../extensibility/debugger/program-control.md) Список следующих подпрограмм, происходящих на уровне программы: Установка следующего оператора, выполнение, выполнение шагов, продолжение, приостановка и возобновление.

 [Методы, связанные с точкой останова](../../extensibility/debugger/breakpoint-related-methods.md) Определяет связанные и ожидающие типы точек останова, которые поддерживает Visual Studio.

 [Оценка стека вызовов](../../extensibility/debugger/call-stack-evaluation.md) Обсуждается реализация методов, позволяющих просматривать кадры стека стека вызовов в режиме приостановки выполнения.

 [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Описывает, как подсистема отладки (DE), вычисление выражений (EE) и диспетчер отладки сеансов участвуют в анализе и вычислении выражения, указанного в одной из окон интегрированной среды разработки.

 [События элемента управления](../../extensibility/debugger/control-events.md) Описывает интерфейс, используемый для отправки событий во время управляемого выполнения программы.
