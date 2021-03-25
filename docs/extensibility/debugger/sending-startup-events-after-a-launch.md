---
title: Отправка событий запуска после запуска | Документация Майкрософт
description: Сведения о серии событий запуска, которые модуль отладки отправляет в сеанс отладки после присоединения модуля отладки к программе.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 227d863df1e3318d2df6be6a24aaf05b5033e92d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070404"
---
# <a name="send-startup-events-after-a-launch"></a>Отправка событий запуска после запуска
После присоединения отладчика (DE) к программе отправляет в сеанс отладки ряд событий запуска.

 События запуска, отправляемые обратно в сеанс отладки, включают:

- Событие создания подсистемы.

- Событие создания программы.

- Создание потоков и события загрузки модулей.

- Событие завершения загрузки, отправленное при загрузке и готовности к выполнению кода, но до выполнения любого кода.

  > [!NOTE]
  > Когда это событие продолжает возобновлению, инициализируются глобальные переменные и запускаются подпрограммы запуска.

- Возможно, другие события создания потоков и загрузки модулей.

- Событие точки входа, которое сигнализирует, что программа достигла своей основной точки входа, например **Main** или `WinMain` . Это событие обычно не отправляется, если DE подключается к уже запущенной программе.

  Программным способом метод DE сначала отправляет диспетчеру отладки сеанса (SDM) интерфейс [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , представляющий событие создания подсистемы, за которым следует [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), представляющий событие создания программы.

  За этими событиями обычно следуют одно или несколько событий создания потока [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) и события загрузки модуля [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .

  Когда код загружается и готов к запуску, но перед выполнением любого кода, отсылает событие [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Load. Наконец, если программа еще не запущена, функция DE отправляет событие точки входа [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , предупреждая о том, что программа достигла основной точки входа и готова к отладке.

## <a name="see-also"></a>См. также
- [Управление выполнением](../../extensibility/debugger/control-of-execution.md)
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
