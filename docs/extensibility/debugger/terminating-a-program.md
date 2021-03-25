---
title: Завершение работы программы | Документация Майкрософт
description: В этой статье описывается, как интегрированная среда разработки использует модуль отладки для завершения одной программы с одним потоком.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: db67e0a391f40fc17a80e616e10aa46a600337a4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057862"
---
# <a name="terminating-a-program"></a>Завершение программы
В следующем разделе описывается завершение одной программы с одним потоком.

## <a name="termination-process"></a>Процесс завершения

1. Параметр DE отправляет [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) с допустимым [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).

2. Параметр DE отправляет [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) с допустимым [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).

   Интегрированная среда разработки переходит в режим конструктора. Модуль отладки или среда выполнения вызывает [IDebugPortNotify2:: ремовепрограмноде](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) для удаления программы из порта.

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
