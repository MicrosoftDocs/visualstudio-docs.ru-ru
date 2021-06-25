---
title: Управление программой | Документация Майкрософт
description: Сведения о подпрограммах в отладке Visual Studio, происходящих на уровне программы, таких как выполнение, выполнение шагов, продолжение и приостановка и возобновление потоков.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b2946309c72fbdddf2794c1da1e773e9a529368
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900720"
---
# <a name="program-control"></a>Управление программой
В отладке Visual Studio все следующие пошаговые и продолжающиеся подпрограммы выполняются на уровне программы:

- Задание следующего оператора, то есть перевод компьютера в следующую инструкцию для выполнения в определенной среде кадров

- Выполнение, то есть продолжение выхода из режима пошагового выполнения

- Шаг с заходом в следующую инструкцию

- Продолжение текущего режима пошагового выполнения

- Приостановка потоков, содержащихся в программе

- Возобновление потоков, содержащихся в программе

> [!NOTE]
> Просмотр стека вызовов реализуется на уровне потока. Чтобы перечислить сведения о кадрах при просмотре стека вызовов для потока, необходимо реализовать все методы интерфейса [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .

## <a name="methods-of-program-control"></a>Методы управления программой
 В следующей таблице показаны методы [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , которые должны быть реализованы для минимально функционального модуля отладки (de) и управления выполнением.

|Метод|Описание|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Возобновляет выполнение всех потоков, содержащихся в программе, из остановленного состояния. Требуется для управления выполнением.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Возобновляет выполнение всех потоков, содержащихся в программе, из остановленного состояния. Требуется для управления выполнением.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг в заданном потоке. Возобновляет выполнение всех остальных потоков, содержащихся в программе. Требуется для управления выполнением.|

 Для многопоточных программ также необходимо реализовать метод [IDebugProgram2:: EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) и все методы интерфейса [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) .

## <a name="see-also"></a>См. также
- [Контроль выполнения и оценка состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
