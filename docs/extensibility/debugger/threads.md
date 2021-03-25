---
title: Потоки | Документация Майкрософт
description: В этой статье описывается определение и роль потока в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 168d29b8306ec58233f426b48c3ab0adfacb2bd5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057849"
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
