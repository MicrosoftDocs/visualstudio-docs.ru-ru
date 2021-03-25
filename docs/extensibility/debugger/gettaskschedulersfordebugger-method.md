---
description: Извлекает массив всех объектов System. Threading. Tasks. TaskScheduler, которые активны в данный момент.
title: Метод Жеттасксчедулерсфордебугжер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d024e44dee8e7513d862e3d299c2ed2b9e53cd5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054859"
---
# <a name="gettaskschedulersfordebugger-method"></a>Метод GetTaskSchedulersForDebugger
Извлекает массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые активны в данный момент.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как вы не можете получить доступ к этому внутреннему элементу из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Возвращаемое значение
 Массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые в настоящее время активны в данный момент <xref:System.AppDomain> .

## <a name="remarks"></a>Remarks
 Этот метод не является потокобезопасным, и его нельзя использовать параллельно с другими экземплярами <xref:System.Threading.Tasks.TaskScheduler> . Вызывайте этот метод из отладчика только в том случае, если отладчик приостановил все остальные потоки.

## <a name="see-also"></a>См. также
- [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
