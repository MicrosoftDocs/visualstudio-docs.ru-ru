---
title: Процессы | Документация Майкрософт
description: В этой статье описывается определение и роль процесса в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3cadf314b189c72320da3f54488af8560cf3fd8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901257"
---
# <a name="processes"></a>Процессы
*Процесс* в архитектуре отладчика:

- — Это контейнер для набора программ. Он тесно аналогичен процессу Windows, который является контейнером для набора потоков.

- Может идентифицировать себя по имени, идентификатору или физическому идентификатору.

- Может перечислить все выполняющиеся программы (и их потоки).

- Может описывать себя, порт, в котором он выполняется, и компьютер, на котором он находится.

- Может создать одну или несколько программ, завершить любую из создаваемых программ или вызвать прекращение работы программы.

- Представляется интерфейсом [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , который создается при запуске процесса. Процесс запускается либо диспетчером отладки сеансов (SDM), либо [лаунчсуспендед](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Пакет отладки может подключить к процессу модуль отладки (DE), вызвав [attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Это означает, что компонент de подключается ко всем возможным программам, выполняемым в процессе, который он может обработать. Например, если среда CLR отключится к процессу, она будет присоединена только к программам, выполняющим управляемый код.

## <a name="see-also"></a>См. также
- [Programs](../../extensibility/debugger/programs.md)
- [Потоки](../../extensibility/debugger/threads.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [Пакет отладки](../../extensibility/debugger/debug-package.md)
- [Модуль отладки](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
