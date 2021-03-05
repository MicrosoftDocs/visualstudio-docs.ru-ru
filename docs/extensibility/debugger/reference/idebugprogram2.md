---
description: Этот интерфейс представляет программу, выполняемую в процессе.
title: IDebugProgram2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b4854150d6581d80804b4c29246bf6db016b5acb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159917"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Этот интерфейс представляет программу, выполняемую в процессе.

## <a name="syntax"></a>Синтаксис

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) и поставщик пользовательского порта реализуют этот интерфейс для представления программы в процессе. Диспетчер отладки сеансов (SDM) также реализует этот интерфейс для предоставления сведений для [присоединения](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Событие [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) возвращает этот интерфейс для новой программы. Этот интерфейс также используется в качестве параметра для многих методов в нескольких интерфейсах.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgram2` .

|Метод|Описание|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Перечисляет потоки, выполняющиеся в этой программе.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Возвращает имя программы.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Возвращает процесс, в котором выполняется эта программа.|
|[Завершение](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Завершает программу.|
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Присоединяется к этой программе.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Определяет, может ли модуль отладки (DE) отсоединяться от программы.|
|[Отсоединить](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Отключает отладчик от этой программы.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Возвращает глобальный уникальный идентификатор для этой программы.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Возвращает свойства программы.|
|[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Продолжение выполнения этой программы из остановленного состояния. Все предыдущие состояния выполнения очищаются.|
|[Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Продолжение выполнения этой программы из остановленного состояния. Все предыдущие состояния выполнения сохраняются.|
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Запрашивает, что эта программа останавливает выполнение, в следующий раз, когда один из его потоков выполняет код.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Возвращает имя и идентификатор модуля отладки (DE), выполняющего эту программу.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Перечисляет контексты кода для заданной позицией в исходном файле.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Возвращает байты памяти для этой программы.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Возвращает поток дизассемблированного кода для этой программы или части программы.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Перечисляет модули, которые программа загрузила и выполняет.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Возвращает обновление изменения и продолжения (ENC) для этой программы.<br /><br /> Пользовательский модуль отладки не реализует этот метод (он должен всегда возвращать `E_NOTIMPL` ).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Перечисляет пути кода этой программы.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Записывает дамп в файл.|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Комментарии
 Программа — это контейнер потоков, выполняющийся в определенной архитектуре среды выполнения, в то время как процесс состоит из одной или нескольких программ.

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Вперед](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
