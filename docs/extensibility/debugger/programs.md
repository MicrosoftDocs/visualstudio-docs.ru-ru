---
title: Программы | Документация Майкрософт
description: В этой статье описывается определение и роль программы в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 07b23fbafd9342b555e2578c4bc0401371e30785
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901283"
---
# <a name="programs"></a>Programs
В архитектуре отладчика *Программа*:

- — Это контейнер для набора потоков и набора модулей. Программа не имеет единого аналога в операционной системе Windows.

     Программа — это разновидность подпроцесса. Например, при отладке веб-сайта сценарий может рассматриваться как программа. Хотя скрипт выполняется в процессе обработчика скриптов, независимо от других скриптов, он также имеет собственный набор потоков. Модуль отладки (DE) подключается к программе, а не к процессу или потоку.

- Может идентифицировать себя и процесс, в котором он выполняется. Программа может быть присоединена к, отсоединена от и описывать ее, если она была создана. Программа может также выполнять, останавливаться, продолжать работу и завершаться.

- Может перечислить все его потоки. Программа может также предоставить собственный поток дизассемблирования и перечислить все контексты кода заданной позицией документа.

- Представляется интерфейсом [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , созданным перед присоединением программы или в рамках процесса присоединения в зависимости от реализации. Когда порт перечисляет программы процесса, каждая программа создается в соответствии с соответствующим интерфейсом [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , переданным в качестве аргумента в [аддпрограмноде](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Хотя модули отладки также создают `IDebugProgram2` интерфейсы для представления программ, эти программы не создаются в соответствии с узлом программы. `IDebugProgramNode2`Интерфейсы, созданные методом de, используются для фактической отладки, а созданные портом используются только для обнаружения выполняющихся в процессе программ.

## <a name="see-also"></a>См. также
- [Процессы](../../extensibility/debugger/processes.md)
- [Узлы программы](../../extensibility/debugger/program-nodes.md)
- [Модули](../../extensibility/debugger/modules.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [Модуль отладки](../../extensibility/debugger/debug-engine.md)
- [Расположение документа](../../extensibility/debugger/document-position.md)
- [Контекст кода](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
