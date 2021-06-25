---
title: Потоки | Документация Майкрософт
description: В этой статье описывается определение и роль потока в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc745a4361c0935896048bbf72a4084f007ecf7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905739"
---
# <a name="threads"></a>Потоки
В архитектуре отладчика *поток*:

- Является основной единицей вычислений. Поток последовательно выполняет свои инструкции в контексте одного стека вызовов, перемещая из одного контекста кода в следующий.

- Может идентифицировать себя и программу, в которой он выполняется. Потоки могут быть именованы, приостановлены и возобновлены. Поток также может перечислить связанные с ними фреймы стека, а при некоторых условиях можно переместить в другой кадр стека. При наличии контекста кадра стека поток может вернуть связанный логический поток, если он есть. Поток имеет свойства, такие как число приостановок, которые могут отображаться в окне **потоки** интегрированной среды разработки.

- Представляется интерфейсом [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , обычно созданным модулем отладки (de) или виртуальной машиной, как следствие выполнения программы.

## <a name="see-also"></a>См. также
- [Programs](../../extensibility/debugger/programs.md)
- [Кадры стека](../../extensibility/debugger/stack-frames.md)
- [Модуль отладки](../../extensibility/debugger/debug-engine.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)
