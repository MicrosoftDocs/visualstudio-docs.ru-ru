---
title: Кадры стека | Документация Майкрософт
description: В этой статье описывается определение и роль кадра стека в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97adb5d453e147c45ae1f268a20a2d3091286508
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960732"
---
# <a name="stack-frames"></a>Кадры стека
В архитектуре отладчика *кадр стека*:

- — Это абстракция стека, который предоставляет контекст выполнения потока. Поток всегда выполняется внутри функции. Кадр стека содержит локальные переменные функции и ее аргументы. Для отладки в Visual Studio язык или окружение, для которых выполняется отладка, должны поддерживать кадры стека.

- Может одновременно идентифицировать и описать себя, а также может возвращать связанный поток. Кадр стека также может возвращать контекст кода, который представляет текущий указатель инструкции, а также связанную документацию и контекст оценки выражения.

- Имеет свойства, описывающие имя, тип и значение локальных переменных и аргументов, которые отображаются в различных окнах отладки интегрированной среды разработки.

- Представляется интерфейсом [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , обычно созданным модулем отладки (de) или виртуальной машиной, как следствие выполнения потока.

## <a name="see-also"></a>См. также раздел
- [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [Модуль отладки](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
