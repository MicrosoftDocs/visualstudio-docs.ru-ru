---
description: Задача успешно завершена.
title: TASK_STATE_RAN_TO_COMPLETION поле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f87eca3ec0d10413593e870fc2cf8fa4dc946e3a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075397"
---
# <a name="task_state_ran_to_completion-field"></a>TASK_STATE_RAN_TO_COMPLETION поле
Задача успешно завершена.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как вы не можете получить доступ к этому внутреннему элементу из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)
```

## <a name="remarks"></a>Remarks
 Если поле [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) содержит это значение, <xref:System.Threading.Tasks.Task.Status%2A> свойство возвращает <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>См. также
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
