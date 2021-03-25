---
title: Присоединение к программе | Документация Майкрософт
description: Узнайте, как Visual Studio реализует отладчик, подключенный к программе после регистрации программы с соответствующим портом.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d880edbea79f56cbd2c90905b0bc2f712dba59b1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055275"
---
# <a name="attach-to-the-program"></a>Присоединение к программе
После регистрации программ с соответствующим портом необходимо подключить отладчик к программе, которую необходимо отладить.

## <a name="choose-how-to-attach"></a>Выберите способ присоединения
 Существует три способа, с помощью которых диспетчер отладки сеансов (SDM) пытается присоединиться к отлаживаемой программе.

1. Для программ, запускаемых модулем отладки с помощью метода [лаунчсуспендед](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (например, типов интерпретируемых языков), модель SDM получает интерфейс [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) из объекта [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , связанного с программой, к которой присоединена программа. Если SDM может получить `IDebugProgramNodeAttach2` интерфейс, то SDM вызывает метод [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . `IDebugProgramNodeAttach2::OnAttach`Метод возвращает `S_OK` значение, указывающее, что он не был подключен к программе и что другие попытки могут быть выполнены для присоединения к программе.

2. Если SDM может получить интерфейс [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) из программы, присоединенной к, то модель SDM вызывает метод [attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) . Этот подход типичен для программ, которые были запущены удаленно поставщиком порта.

3. Если программа не может быть присоединена с `IDebugProgramNodeAttach2::OnAttach` помощью `IDebugProgramEx2::Attach` методов или, то модель SDM загружает модуль отладки (если он еще не загружен), вызывая `CoCreateInstance` функцию, а затем вызывает метод [attach](../../extensibility/debugger/reference/idebugengine2-attach.md) . Этот подход типичен для программ, запускаемых локально поставщиком портов.

    Поставщик настраиваемого порта также может вызывать `IDebugEngine2::Attach` метод в реализации метода в пользовательском поставщике порта `IDebugProgramEx2::Attach` . Как правило, в этом случае настраиваемый поставщик портов запускает модуль отладки на удаленном компьютере.

   Вложение достигается, когда диспетчер отладки сеансов (SDM) вызывает метод [attach](../../extensibility/debugger/reference/idebugengine2-attach.md) .

   При запуске DE в том же процессе, что и приложение для отладки, необходимо реализовать следующие методы [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  После `IDebugEngine2::Attach` вызова метода выполните следующие действия в реализации `IDebugEngine2::Attach` метода:

1. Отправка объекта события [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) в SDM. Дополнительные сведения см. в разделе [Отправка событий](../../extensibility/debugger/sending-events.md).

2. Вызовите метод [жетпрограмид](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) объекта [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , переданного в `IDebugEngine2::Attach` метод.

     Он возвращает `GUID` , который используется для распознавания программы. `GUID`Должен храниться в объекте, который представляет локальную программу, в de, а также должен возвращаться при `IDebugProgram2::GetProgramId` вызове метода в `IDebugProgram2` интерфейсе.

    > [!NOTE]
    > Если реализуется `IDebugProgramNodeAttach2` интерфейс, программа `GUID` передается в `IDebugProgramNodeAttach2::OnAttach` метод. `GUID`Используется для программы, `GUID` возвращаемой `IDebugProgram2::GetProgramId` методом.

3. Отправьте объект события [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , чтобы уведомить SDM о том, что локальный `IDebugProgram2` объект был создан для представления программы в de. Дополнительные сведения см. в разделе [Отправка событий](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Это не тот же `IDebugProgram2` объект, который был передан в `IDebugEngine2::Attach` метод. Ранее переданный `IDebugProgram2` объект распознается только портом и является отдельным объектом.

## <a name="see-also"></a>См. также
- [Вложение на основе запуска](../../extensibility/debugger/launch-based-attachment.md)
- [Отправка событий](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
