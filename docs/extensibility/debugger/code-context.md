---
title: Контекст кода | Документация Майкрософт
description: Сведения о контексте кода в отладке Visual Studio, описывающем место в коде, которое существует, когда программа остановлена в точке останова.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c668cd1fa80efe24fa596cc4e9f311e2db519246
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055041"
---
# <a name="code-context"></a>Контекст кода
При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладке — **контекст кода**:

- Предоставляет абстракцию места в коде, известное модулю отладки (DE). В настоящее время для большинства архитектур времени выполнения контекст кода можно рассматривать как адрес в потоке инструкций программы. Для нетрадиционных языков, где код может не быть представлен инструкциями, контекст кода может быть представлен другими средствами.

- Описывает текущую точку в потоке выполнения отлаживаемой программы.

- Существует только в том случае, если программа остановлена в точке останова.

- Имеет связанный контекст документа.

- Реализуется с помощью интерфейса [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .

## <a name="see-also"></a>См. также
- [Контекст документа](../../extensibility/debugger/document-context.md)
- [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
