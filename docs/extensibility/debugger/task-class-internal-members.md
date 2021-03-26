---
title: Класс Task-внутренние элементы | Документация Майкрософт
description: Сведения о внутренних членах класса System. Threading. Tasks. Task, которые помогают реализовать пользовательский отладчик.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bfa57329b3f321d2703683639644783be60d651f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079375"
---
# <a name="task-class---internal-members"></a>Класс Task — внутренние элементы
В этой статье описываются внутренние члены <xref:System.Threading.Tasks.Task?displayProperty=fullName> класса, помогающие реализовать пользовательский отладчик. Общие сведения об этом классе см <xref:System.Threading.Tasks.Task> . в справочной статье.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как вы не можете получить доступ к этим внутренним членам из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.class public auto ansi System.Threading.Tasks.Task
       extends System.Object
       implements System.Threading.IThreadPoolWorkItem,
                  System.IAsyncResult,
                  System.IDisposable,
                  System.Threading.ICancelableOperation
```

## <a name="members"></a>Участники

### <a name="methods"></a>Методы

|Имя|Описание|
|----------|-----------------|
|[Метод SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Задает или очищает бит состояния TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|
|[Метод NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Метод-заполнитель, используемый отладчиком в качестве цели точки останова.|

### <a name="fields"></a>Поля

|name|Описание|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Делегат, представляющий код для выполнения в <xref:System.Threading.Tasks.Task> объекте.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Хранит дополнительные свойства <xref:System.Threading.Tasks.Task> объекта.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Резервное поле для <xref:System.Threading.Tasks.Task?displayProperty=fullName> родительского свойства.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Хранит сведения о текущем состоянии <xref:System.Threading.Tasks.Task> объекта.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Объект, представляющий данные, которые будут использоваться действием.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Резервное поле для <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> Свойства.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Следующий доступный идентификатор для <xref:System.Threading.Tasks.Task> объекта.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Указывает, что задача была отменена до достижения состояния выполнения или что задача подтвердила ее отмену и завершилась без исключения.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Указывает, что задача запущена.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Указывает, что задача завершена из-за необработанного исключения.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Указывает, что выполнение задачи успешно завершено.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Указывает, что задача завершила выполнение своего делегата и неявно ожидает завершения присоединенных дочерних задач.|

## <a name="remarks"></a>Remarks
 Следующие внутренние методы полезны для обработчика отладчика, так как они помечают вход на <xref:System.Threading.Tasks.Task> выполнение кода:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>См. также
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Внутренние модули параллельного расширения для платформа .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
