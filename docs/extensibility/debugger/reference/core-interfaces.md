---
description: Следующие интерфейсы являются основными интерфейсами для расширения отладчика с помощью пакета VS SDK.
title: Основные интерфейсы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f24dd16656144fa155d0473d7f722487c0edd03
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170761"
---
# <a name="core-interfaces"></a>Базовые интерфейсы
Следующие интерфейсы являются основными интерфейсами для расширения отладчика с помощью [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Разговор
 Эти интерфейсы в основном используются для создания модуля отладки (DE). Они упорядочены по категориям:

- [Точки останова](#Breakpoints)

- [Контексты](#Contexts)

- [Основной сервер](#CoreServer)

- [Отладчики](#DebugEngines)

- [Документы](#Documents)

- [События](#Events)

- [Выражения](#Expressions)

- [Память](#Memory)

- [Модули](#Modules)

- [Порты](#Ports)

- [Процессы](#Processes)

- [Programs](#Programs)

- [Свойства](#Properties)

- [Кадры стека](#StackFrames)

- [Потоки](#Threads)

- [Визуализаторы типов](#TypeVisualizers)

  Ниже перечислены сущности, которые могут реализовывать интерфейсы.

- Модуль отладки (DE)

- Поставщик порта (PS)

- Средство оценки выражений (EE)

- Visual Studio (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a> Точки останова
 Эти интерфейсы связаны с реализацией и отслеживанием точек останова.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Представляет точку останова, привязанную к расположению в памяти.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Отправляется методом DE, когда точка останова привязана к расположению в памяти.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Представляет контрольную сумму документа для запроса точки останова.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Отсылается DE, когда точка останова не может быть привязана к расположению в памяти.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Отправляется методом DE при достижении точки останова.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Представляет запрос для точки останова; используется при создании ожидающей точки останова.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Представляет запрос для точки останова; используется при создании ожидающей точки останова.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Представляет сведения, используемые для привязки точки останова.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Отправляется методом DE, если точка останова не привязана к расположению в памяти.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Представляет недопустимую точку останова (возвращается `IDebugBreakpointErrorEvent2` ).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Представляет сведения о разрешении недействительной точки останова.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Представляет позицию в функции, в которой задана точка останова.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Представляет точку останова, которая должна быть привязана; используется при создании привязанной точки останова.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Представляет перечисление для набора связанных точек останова.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Представляет перечисление для набора точек останова, которые не могут быть привязаны к расположению в памяти.|

## <a name="contexts"></a><a name="Contexts"></a> Контекстах
 Эти интерфейсы представляют различные виды контекстов внутри отлаживаемой программы.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Представляет начальное расположение инструкции кода.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Расширяет интерфейс [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , чтобы обеспечить получение интерфейсов модуля и процесса.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Представляет расположение в документе.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Представляет контекст, в котором вычисляется выражение.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Представляет начальное расположение в памяти коллекции байтов.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Представляет контекст кадра стека в точке останова или исключении.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Представляет контекст кадра стека в точке останова или исключении.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Представляет перечисление для набора контекстов кода.|

## <a name="core-server"></a><a name="CoreServer"></a> Основной сервер
 Эти интерфейсы представляют компьютер, на котором выполняется отладка программы. Они реализуются с помощью, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] но их можно вызывать с помощью отладочных модулей.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Предоставляет доступ к портам и поставщикам портов, а также сведения о компьютере.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Представляет [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , поддерживающий удаленную отладку.|

## <a name="debug-engines"></a><a name="DebugEngines"></a> Отладчики
 Эти интерфейсы представляют собой модули отладки и связанные с ними события.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Представляет пользовательский модуль отладки.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Представляет пользовательский модуль отладки, который поддерживает загрузку символов, Жустмикоде и исключений.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Посылается каждым новым экземпляром DE, чтобы указать, что он готов к обработке задач отладки.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Представляет пользовательский модуль отладки, поддерживающий запуск программ.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Представляет узел программы, обрабатывающий несколько модулей отладки.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Предоставляет модели SDM способ получения интерфейса для модуля отладки из потока, программы или кадра стека.|

## <a name="documents"></a><a name="Documents"></a> Документаци
 Эти интерфейсы представляют документы (исходные файлы) и связанные с ними элементы.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Отправляется методом DE для запроса открытия документа.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Представляет поток собранных инструкций из документа.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Представляет документ, предоставленный методом DE, с указанием имени и идентификатора класса (CLSID).|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Представляет контрольную сумму для документа отладки и позволяет передавать контрольную сумму между компонентами.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Представляет контекст документа — точку в документе, соответствующую определенной инструкции и контексту кода.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Представляет общую точку в документе.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Представляет расположение в исходном файле как смещение символа.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Представляет текстовый документ, предоставленный методом DE (производным от [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), который предоставляет фактический текст.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Отсылается DE для указания изменений в исходном файле, находящиеся в памяти.|

## <a name="events"></a><a name="Events"></a> Событиях
 Эти интерфейсы представляют все события, которые передаются между DE и диспетчером отладки сеансов (SDM).

| Интерфейс | Реализовано | Описание |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Отправляется методом DE для запроса открытия документа. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Модуль отладки (DE) отправляет этот интерфейс в Диспетчер отладки сеансов (SDM) для установки сообщения в строке состояния во время загрузки символов. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Отправляется функцией DE при завершении перерыва в программе. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Отправляется методом DE при привязке точки останова. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Отправляется методом DE, если точка останова не может быть привязана. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Отправляется методом DE при достижении точки останова. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Отправляется методом DE, когда точка останова не привязана. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Отсылается DE, чтобы определить, должна ли она останавливаться в определенном месте. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Отсылается DE для указания изменений в исходном файле, находящиеся в памяти. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Посылается каждым новым экземпляром DE, чтобы указать, что он готов к обработке задач отладки. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Посылается DE, чтобы указать, что отлаживаемая программа готова выполнить первую инструкцию. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Интерфейс, используемый другими интерфейсами событий, которые могут возвращать ошибку, чтобы предоставить пользователю сообщения об ошибках. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Базовый интерфейс, от которого наследуются все другие интерфейсы событий. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Представляет интерфейс, реализованный SDM, в который отправляются события (выраженные в виде объектов, реализующих определенный интерфейс событий). |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Отправляется методом DE, когда в отлаживаемой программе возникло исключение. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Отправляется методом DE после завершения вычисления асинхронного выражения. |
| IDebugFindSymbolEvent2 | | УСТАРЕВШИЕ. НЕ ИСПОЛЬЗУЙТЕ. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Отсылается методом DE при обработке для перехваченного исключения. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Отправляется функцией DE при завершении загрузки программы. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Посылается DE, чтобы в интегрированной среде разработки отображалось информационное сообщение для пользователя. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Отправляется методом DE при загрузке или выгрузке модуля. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Сигнализирует [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательскому интерфейсу отладчика предупредить пользователя о том, что не удалось найти символы для запущенного исполняемого файла. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Посылается DE, чтобы в интегрированной среде разработки отображалась произвольная строка. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Отправляется портом для передачи событий порта любому прослушивателю. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Отправляется методом DE или Port при создании процесса. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Отправляется методом DE или Port при уничтожении процесса. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Отправляется методом DE или Port при создании программы. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Отправляется методом DE или Port при удалении программы. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Позволяет подсистеме отладки переопределять поведение пользовательского интерфейса по умолчанию [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] при завершении сеанса отладки. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Отправляется из модуля отладки (DE) в Диспетчер отладки сеансов (SDM) при изменении имени программы. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Отправляется методом DE при создании нового свойства (представленного `IDebugProperty2` интерфейсом). |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Отправляется методом DE при уничтожении свойства. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Отправляется методом DE при пошаговом выполнении или над функцией, поэтому возвращаемое значение может быть правильно отображено. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Включает модули отладки для удаленного считывания параметров метрик. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Отправляется методом DE при завершении шага с инструкцией, а также над ней или из нее. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Отсылается DE для указания на успешное или неуспешное завершение загрузки символов для модуля. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Отправляется методом DE при создании потока. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Отправляется методом DE при уничтожении потока. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Отправляется методом DE, когда поток изменил свое имя. |

## <a name="expressions"></a>Выражения <a name="Expressions"></a>
 Эти интерфейсы представляют выражения, вычисляемые в определенном контексте.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Представляет выражение для вычисления. Получено из интерфейса [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) .|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Представляет контекст, в котором вычисляется выражение. Получено из интерфейса [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) .|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Отправляется методом DE после завершения вычисления асинхронного выражения.|

## <a name="memory"></a><a name="Memory"></a> Свободной
 Эти интерфейсы представляют последовательности байтов в памяти.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Представляет последовательность байтов в памяти, которые могут быть считаны или записаны в.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Представляет расположение в памяти последовательности байтов.|

## <a name="modules"></a><a name="Modules"></a> Модули
 Эти интерфейсы представляют собой модуль, соответствующий исполняемому файлу или. DLL-файл.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Представляет отдельный исполняемый файл или библиотеку DLL.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Представляет [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , поддерживающий символы.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Отправляется методом DE при загрузке или выгрузке модуля.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Представляет сведения о исходном сервере, содержащиеся в PDB-файле.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Представляет перечисление для набора модулей, известных [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|

## <a name="ports"></a><a name="Ports"></a> Порты
 Эти интерфейсы представляют порты и поставщики портов.

| Интерфейс | Реализовано | Описание |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Представляет порт по умолчанию на локальном компьютере. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Включает модуль отладки, использующий DCOM для запроса [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса, чтобы убедиться, что брандмауэр не блокирует удаленную отладку. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Представляет порт. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Отправляется портом для передачи событий порта любому прослушивателю. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Представляет порт, который может запускать и завершать процессы. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Используется для регистрации и отмены регистрации программ с помощью порта; позволяет порту отлаживать программы, отладка которых выполняется в данный момент. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Представляет настраиваемый пользовательский интерфейс для выбора порта. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Представляет запрос для порта, из которого будет создан или расположен новый порт. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Представляет поставщика портов. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Представляет поставщика портов, которые могут сохраняться (сохранять на диск) сведения о созданных им портах. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Позволяет [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательскому интерфейсу отображать текст в разделе **сведения о транспортировке** диалогового окна **Присоединение к процессу** . |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Разрешает запрос сведений о конечном компьютере. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Представляет перечисление для набора портов. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Представляет перечисление по набору поставщиков портов. |

## <a name="processes"></a><a name="Processes"></a> Операций
 Эти интерфейсы представляют процессы, один исполняемый файл, содержащий одну или несколько программ.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Представляет процесс, выполняющийся на компьютере.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Представляет процесс, который активно поддерживает отладку (используется для замены методов Step, Continue и Execute в интерфейсе [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ).|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Отправляется методом DE или Port при создании процесса.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Отправляется методом DE или Port при уничтожении процесса.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Представляет процесс, который должен отслеживанию того, какой сеанс подключен к нему.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Представляет перечисление набора процессов в порте.|

## <a name="programs"></a><a name="Programs"></a> Приложениями
 Эти интерфейсы представляют собой программы, логические единицы выполнения, которые не обязательно соответствуют физическому исполняемому файлу или модулю.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Представляет [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , который должен работать совместно с другими программами, отладка которых выполняется в то же время.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Представляет логическую единицу выполнения.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Отправляется методом DE или Port при создании программы.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Отправляется методом DE или Port при удалении программы.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Представляет [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , который может обрабатываться несколькими ядрами отладки.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Представляет [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , который должен быть способен относиться к подключенному к нему сеансу.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Представляет [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , который может возвращать сведения о процессе, в котором он выполняется.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Представляет программу, которую можно отладить.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Позволяет узлу программы получать уведомления о попытке присоединения к связанной программе.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Предоставляет модели SDM возможность запрашивать DE о программах, управляемых этим де.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Используется DEs для регистрации программ с SDM для их отладки.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Представляет [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , который может маршалировать интерфейсы через границы потока или процесса.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Представляет перечисление набора программ.|

## <a name="properties"></a><a name="Properties"></a> Свойства
 Эти интерфейсы представляют свойства, значение, связанное с определенным контекстом, обычно результат вычисления выражения.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Представляет [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , который может отображать его значение особым образом.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Представляет значение кадра стека, документа или результата вычисления выражения.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Представляет [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , поддерживающий произвольно длинные строки.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Отправляется методом DE при создании нового свойства (представленного интерфейсом [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ).|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Отправляется методом DE при уничтожении свойства.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Представляет ссылку на свойство, которое может существовать за пределами определенного кадра стека.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Представляет перечисление по набору структур [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , описывающих переменные, регистры, параметры и выражения.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Представляет перечисление для набора структур [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .|

## <a name="stack-frames"></a><a name="StackFrames"></a> Кадры стека
 Эти интерфейсы представляют кадр стека — контекст, в котором возникла точка останова или исключение.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Представляет контекст, в котором возникла точка останова или исключение.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Представляет [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , который может выполнять обработку перехваченных исключений.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Представляет перечисление по набору структур [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) , которые указывают последовательность вызова функции, используемую для прибытия в определенный кадр стека.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Представляет перечисление для набора структур [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) , описывающих кадры стека.|

## <a name="threads"></a><a name="Threads"></a> Потоки
 Эти интерфейсы представляют потоки и связанные с ними события.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Представляет поток выполнения.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Отправляется методом DE при создании потока.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Отправляется методом DE при уничтожении потока.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Отправляется методом DE, когда поток изменил свое имя.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Представляет перечисление для набора потоков.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a> Визуализаторы типов
 Эти интерфейсы обеспечивают поддержку визуализаторов типов. Эти интерфейсы обычно реализуются средством оценки выражений.

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Представляет массив байтов, которые должны быть представлены визуализатору типов.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Предоставляет методы для получения доступа к данным, передаваемым визуализатору типа.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Представляет свойство, предоставляющее доступ к реализациям [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .|

## <a name="see-also"></a>См. также раздел
- [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Создание пользовательского модуля отладки](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
