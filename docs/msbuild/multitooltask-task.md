---
title: Задача MultiToolTask | Документация Майкрософт
description: Предоставление таблицы, в которой приводятся обязательные и необязательные параметры задачи MultiToolTask MSBuild.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.multitooltask
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), MultiToolTask task
- MultiToolTask task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d76aa3762b254ee35ada1e4e81fe857f509a4e5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048977"
---
# <a name="multitooltask-task"></a>Задача MultiToolTask

Нет описания.

## <a name="parameters"></a>Параметры

В представленной ниже таблице приводятся параметры задачи **MultiToolTask**.

|Параметр|Описание|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Необязательный параметр типа **string[]** .|
|**SemaphoreProcCount**|Необязательный параметр типа **string**.|
|**SchedulerFunction**|Необязательный параметр типа **string**.|
|**SchedulerVerbose**|Необязательный параметр типа **bool**.|
|**Sources**|Обязательный параметр **ITaskItem[]** .|
|**TaskAssemblyName**|Необязательный параметр типа **string**.|
|**TaskName**|Обязательный параметр **string**.|
|**TrackerLogDirectory**|Обязательный параметр **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
