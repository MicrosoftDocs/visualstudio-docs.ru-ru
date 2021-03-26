---
title: Подключение после запуска | Документация Майкрософт
description: Когда программа запускается, сеанс отладки готов к подключению модуля отладки к программе. Выберите подход к проектированию для взаимодействия с модулем отладки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9010d2619b76c2932ca1a8a5aed8db6c6a5cf075
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055327"
---
# <a name="attach-after-a-launch"></a>Присоединить после запуска
После запуска программы сеанс отладки готов к присоединению модуля отладки (DE) к уже созданной программе.

## <a name="design-decisions"></a>Решения по проектированию
 Так как обмен данными в рамках общего адресного пространства упрощается, необходимо выбрать один из двух подходов к проектированию: настроить обмен данными между сеансом отладки и DE. Или установите связь между DE и программой. Выберите один из следующих:

- Если есть смысл настроить обмен данными между сеансом отладки и DE, сеанс отладки совместно создает сообщение DE и запрашивает отключение к программе. Эта схема оставляет сеанс отладки и размещается в одном адресном пространстве, а среда выполнения и программа — вместе друг с другом.

- Если есть смысл настроить обмен данными между DE и программой, среда выполнения совместно создает значение DE. Эта схема оставляет SDM в одном адресном пространстве и в среде выполнения, а также вместе с другими программами. Такая схема типична для DE, которая реализована с помощью интерпретатора для выполнения сценариев языков.

    > [!NOTE]
    > То, как DE присоединяется к программе, зависит от реализации. Связь между DE и программой также зависит от реализации.

## <a name="implementation"></a>Реализация
 Программным способом, когда диспетчер отладки сеансов (SDM) сначала получает объект [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , представляющий запускаемую программу, он вызывает метод [attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) , передавая ему объект [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , который позже используется для передачи событий отладки в SDM. `IDebugProgram2::Attach`Затем метод вызывает метод [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Дополнительные сведения о том, как SDM получает `IDebugProgram2` интерфейс, см. [в разделе уведомление порта](../../extensibility/debugger/notifying-the-port.md).

 Если ваш DE должен выполняться в том же адресном пространстве, что и программа, которую вы выполняете отладку: поскольку DE обычно является частью интерпретатора, выполняющего сценарий, `IDebugProgramNodeAttach2::OnAttach` метод возвращает `S_FALSE` . `S_FALSE`Возвращаемое значение указывает, что он завершил процесс присоединения.

 Однако если в адресном пространстве SDM выполняются следующие действия: `IDebugProgramNodeAttach2::OnAttach` метод возвращает значение `S_OK` , или интерфейс [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) не реализован вообще в объекте [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , связанном с отлаживаемой программой. В этом случае метод [attach](../../extensibility/debugger/reference/idebugengine2-attach.md) вызывается в конечном итоге для завершения операции присоединения.

 В последнем случае необходимо вызвать метод [жетпрограмид](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) для `IDebugProgram2` объекта, переданного в `IDebugEngine2::Attach` метод, сохранить `GUID` в локальном объекте Program и вернуть его `GUID` при `IDebugProgram2::GetProgramId` последующем вызове метода для этого объекта. `GUID`Используется для однозначной идентификации программы в различных компонентах отладки.

 В случае `IDebugProgramNodeAttach2::OnAttach` возврата метода объект, `S_FALSE` `GUID` используемый для программы, передается в этот метод, и это `IDebugProgramNodeAttach2::OnAttach` метод, который задает для `GUID` локального объекта программы.

 Теперь программа DE подключена к программе и готова к отправке любых событий запуска.

## <a name="see-also"></a>См. также
- [Прямое подключение к программе](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Уведомление порта](../../extensibility/debugger/notifying-the-port.md)
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
