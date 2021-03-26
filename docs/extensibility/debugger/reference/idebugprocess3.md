---
description: Этот интерфейс представляет выполняющийся процесс и его программы.
title: IDebugProcess3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d08169b196e01b5e2a7effdfe54829d17a970ef3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076515"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Этот интерфейс представляет выполняющийся процесс и его программы. Этот интерфейс существует в качестве замены для нескольких методов в интерфейсе [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Он обеспечивает управление всеми программами в процессе.

> [!NOTE]
> Методы [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [EXECUTE](../../../extensibility/debugger/reference/idebugprogram2-execute.md)и [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) являются устаревшими и больше не должны использоваться. Вместо этого используйте соответствующие методы в `IDebugProcess3` интерфейсе.

## <a name="syntax"></a>Синтаксис

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиком пользовательского порта для управления программами как группой. Когда программы управляются как группа, можно управлять их выполнением и устанавливать язык для средства оценки выражений. Этот интерфейс должен быть реализован поставщиком порта.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс вызывается главным образом диспетчером отладки сеансов (SDM) для взаимодействия с группой программ, идентифицированных в этом процессе.

 Чтобы получить этот интерфейс, вызовите [QueryInterface](/cpp/atl/queryinterface) в интерфейсе [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) .

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованным от [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Продолжение выполнения или пошаговое выполнение процесса.|
|[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Начинает выполнение процесса.|
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Шаги передают одну инструкцию или инструкцию в процессе.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Возвращает причину, по которой процесс был запущен для отладки.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Задает язык размещения, чтобы модуль отладки мог загрузить соответствующий вычислитель выражений.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Извлекает язык, заданный в настоящее время для этого процесса.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Отключает функцию "изменить и продолжить" (ENC) для этого процесса.<br /><br /> Пользовательский поставщик портов не реализует этот метод (он должен всегда возвращать `E_NOTIMPL` ).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Получите состояние ENC для этого процесса.<br /><br /> Пользовательский поставщик портов не реализует этот метод (он должен всегда возвращать `E_NOTIMPL` ).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Извлекает массив уникальных идентификаторов для доступных модулей отладки.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
