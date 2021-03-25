---
title: Присоединение и отсоединение к программе | Документация Майкрософт
description: Узнайте, как отправить правильную последовательность методов и событий с соответствующими атрибутами для подключения отладчика.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fb51cb3e6c16916e3778dde06fb2ac274608ed70
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055314"
---
# <a name="attaching-and-detaching-to-a-program"></a>Присоединение и отсоединение программы
Для подключения отладчика необходимо отправить правильную последовательность методов и событий с соответствующими атрибутами.

## <a name="sequence-of-methods-and-events"></a>Последовательность методов и событий

1. Диспетчер отладки сеансов (SDM) вызывает метод [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

    В зависимости от модели процесса модуля отладки (DE) `IDebugProgramNodeAttach2::OnAttach` метод возвращает один из следующих методов, который определяет, что происходит дальше.

    Если `S_FALSE` возвращается, подсистема отладки успешно прикрепляется к программе. В противном случае вызывается метод [attach](../../extensibility/debugger/reference/idebugengine2-attach.md) для завершения процесса присоединения.

    Если `S_OK` возвращается, de загружается в том же процессе, что и модель SDM. Модель SDM выполняет следующие задачи:

   1. Вызывает [жетенгинеинфо](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) для получения сведений о подсистеме de.

   2. Совместно создает значение DE.

   3. Вызывает [attach](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. Параметр DE отправляет [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) в SDM с `EVENT_SYNC` атрибутом.

3. Параметр DE отправляет [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) в SDM с `EVENT_SYNC` атрибутом.

4. Параметр DE отправляет [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) в SDM с `EVENT_SYNC_STOP` атрибутом.

   Отсоединение от программы — это простой двухэтапный процесс, описанный ниже.

5. Модель SDM вызывает [отсоединение](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. Параметр DE отправляет [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
