---
description: Список дочерних задач, зарегистрированных в этой задаче.
title: m_children поле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5aaf29d76a7bbd81a416c86360f315bc5c09b76c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158873"
---
# <a name="m_children-field"></a>m_children поле
Список дочерних задач, зарегистрированных в этой задаче.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как вы не можете получить доступ к этому внутреннему элементу из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Remarks
 Во время выполнения задачи только тот поток, который выполняет задачу, должен получить доступ к этому массиву.

 Если задача завершена, другие потоки могут получить доступ к этому полю, если они не добавляют ничего в него или не удаляют что-либо из него.

## <a name="see-also"></a>См. также раздел
- [Класс Континжентпропертиес](../../extensibility/debugger/contingentproperties-class-internal-members.md)
