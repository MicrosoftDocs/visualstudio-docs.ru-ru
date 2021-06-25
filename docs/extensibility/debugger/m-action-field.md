---
description: Делегат, представляющий код для выполнения в объекте System. Threading. Tasks. Task.
title: m_action поле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 838494eb612ffaa18931e42227619b22bc297b4f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901478"
---
# <a name="m_action-field"></a>m_action поле
Делегат, представляющий код для выполнения в <xref:System.Threading.Tasks.Task> объекте.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как вы не можете получить доступ к этому внутреннему элементу из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.field assembly object m_action
```

## <a name="remarks"></a>Remarks
 Это `action` параметр в <xref:System.Threading.Tasks.Task.%23ctor%2A> конструкторе.

## <a name="see-also"></a>См. также
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
