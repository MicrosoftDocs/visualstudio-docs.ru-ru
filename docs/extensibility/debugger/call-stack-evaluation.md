---
title: Вычисление стека вызовов | Документация Майкрософт
description: Узнайте о методе Енумфрамеинфо и о том, как его реализовать для просмотра кадров стека вызовов в режиме приостановки выполнения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c7e7180301965e43e6757340019c3506fe1a5e1f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055093"
---
# <a name="call-stack-evaluation"></a>Оценка стека вызовов
Чтобы просмотреть кадры стека стека вызовов в режиме приостановки выполнения, необходимо реализовать метод [енумфрамеинфо](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .

## <a name="methods-for-evaluation"></a>Методы для оценки
 Для простого модуля отладки (DE) может существовать только один кадр стека. Чтобы изучить кадр стека в режиме приостановки выполнения, необходимо реализовать следующие методы [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).

|Метод|Описание|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Возвращает контекст кода для кадра стека. Контекст кода представляет текущий указатель инструкции в кадре стека.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Возвращает контекст документа для кадра стека. Контекст документа представляет текущее расположение в исходном коде для кадра стека. Требуется для просмотра исходного кода при остановке в программе.|

 Для этих методов требуется реализация нескольких интерфейсов и методов, связанных с контекстом. Поэтому необходимо реализовать метод [жетдокументконтекст](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) и следующие методы [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Метод|Описание|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Возвращает диапазон инструкций File в контексте документа.|

 Чтобы перечислить контексты кода, необходимо реализовать все методы [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>См. также
- [Контроль выполнения и оценка состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
