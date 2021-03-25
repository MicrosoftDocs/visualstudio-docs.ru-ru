---
description: Список дочерних задач, зарегистрированных в этой задаче.
title: m_children поле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90394afd982f22977d3d3ed74850032bfb5634c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094696"
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

## <a name="see-also"></a>См. также
- [Класс Континжентпропертиес](../../extensibility/debugger/contingentproperties-class-internal-members.md)
