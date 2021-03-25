---
description: Объект, представляющий данные, которые будет использовать действие.
title: m_stateObject поле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2128073f47c76244a18e18005a431f9317686c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054794"
---
# <a name="m_stateobject-field"></a>m_stateObject поле
Объект, представляющий данные, которые будет использовать действие.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как вы не можете получить доступ к этому внутреннему элементу из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Remarks
 Это `state` параметр в <xref:System.Threading.Tasks.Task.%23ctor%2A> конструкторе. Это также резервное поле для <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> Свойства.

## <a name="see-also"></a>См. также
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
