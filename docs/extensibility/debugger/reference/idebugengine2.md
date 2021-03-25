---
description: Этот интерфейс представляет модуль отладки (DE).
title: IDebugEngine2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6e32c4798ad1bea65a9aadcf8a0d73052acc238
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066156"
---
# <a name="idebugengine2"></a>IDebugEngine2
Этот интерфейс представляет модуль отладки (DE). Он используется для управления различными аспектами сеанса отладки, от создания точек останова до установки и удаления исключений.

## <a name="syntax"></a>Синтаксис

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется с помощью пользовательского интерфейса DE для управления отладкой программ. Этот интерфейс должен быть реализован методом DE.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс вызывается диспетчером отладки сеансов (SDM) для управления сеансом отладки, включая Управление исключениями, создание точек останова и реагирование на синхронные события, отправляемые методом DE.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEngine2` .

|Метод|Описание|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Создает перечислитель для всех отлаживаемых программ с помощью DE.|
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Присоединяет DE к программе.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Создает ожидающую точку останова в DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Указывает, как метод DE должен выполнять данное исключение.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Удаляет указанное исключение, поэтому оно больше не обрабатывается модулем отладки.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Удаляет список исключений, установленных интегрированной средой разработки для определенной архитектуры или языка среды выполнения.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Возвращает идентификатор GUID для DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Информирует о том, что указанная программа была необычным прекращена и что DE должен очистить все ссылки на программу и отправить событие уничтожения программы.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Вызывается SDM для указания на то, что было получено и обработано Синхронное событие отладки, которое ранее было отправлено DE в SDM.|
|[Pragma](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Задает языковой стандарт для DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Задает корень реестра, используемый в данный момент в параметре DE.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Задает метрику.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Запрашивает, что все программы, отладка которых выполняется, прекращают выполнение при следующем попытке запуска одного из их потоков.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
