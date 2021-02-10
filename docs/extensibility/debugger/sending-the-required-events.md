---
title: Отправка необходимых событий | Документация Майкрософт
description: Сведения о упорядоченных событиях, которые необходимы при создании модуля отладки и присоединении его к программе в отладке Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a056f3a7d986ca9abcf82edd3a77aac013665976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960823"
---
# <a name="send-the-required-events"></a>Отправка необходимых событий
Используйте эту процедуру для отправки необходимых событий.

## <a name="process-for-sending-required-events"></a>Процесс отправки необходимых событий
 Следующие события являются обязательными в этом порядке при создании модуля отладки (DE) и присоединении его к программе:

1. Отправка объекта события [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) в Диспетчер отладки сеансов (SDM) при инициализации de для отладки одной или нескольких программ в процессе.

2. Когда отлаживаемая программа прикрепляется к, отправляет объект события [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) в SDM. Это событие может быть остановлено в зависимости от структуры подсистемы.

3. Если программа подключена к при запуске процесса, отправьте объект события [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) в SDM, чтобы уведомить IDE о новом потоке. Это событие может быть остановлено в зависимости от структуры подсистемы.

4. Отправка объекта события [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) в SDM при завершении загрузки отлаживаемой программы или при завершении присоединения к программе. Это событие должно быть событием остановки.

5. Если приложение для отладки запускается, отправляет объект события [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) в SDM, когда первая инструкция кода в архитектуре времени выполнения собирается для выполнения. Это событие всегда является остановкой. При пошаговом выполнении сеанса отладки среда IDE останавливается на этом событии.

> [!NOTE]
> Во многих языках используются глобальные инициализаторы или внешние, предварительно скомпилированные функции (из библиотеки CRT или _Main) в начале своего кода. Если язык отлаживаемой программы содержит один из этих типов элементов перед начальной точкой входа, этот код выполняется, а событие точки входа отправляется при достижении точки входа пользователя, такой как **Main** или `WinMain` .

## <a name="see-also"></a>См. также раздел
- [Включение отладки программы](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
