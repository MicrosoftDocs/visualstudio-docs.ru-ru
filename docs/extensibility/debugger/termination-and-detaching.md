---
title: Завершение и отсоединение | Документация Майкрософт
description: Нормальное завершение означает, что отлаживаемая программа выполняется до завершения без точек останова, исключений, ошибок времени выполнения или бесконечного цикла.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8662809b50dbfec3046af1d0d6b6fa151c3a33e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057836"
---
# <a name="termination-and-detaching"></a>Завершение и отсоединение
В следующем разделе описывается нормальное завершение работы.

## <a name="discussion"></a>Разговор
 После продолжения работы интерфейса [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) или [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) в случае отсутствия точек останова, исключений, ошибок времени выполнения или бесконечных циклов в приложении для отладки выполняется отладка программы до ее завершения. Этот процесс является нормальным завершением работы.

 Чтобы реализовать нормальное завершение, необходимо отправить [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) . Для нормального завершения требуется выполнение метода [IDebugProgramDestroyEvent2:: жетекситкоде](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>См. также
- [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
