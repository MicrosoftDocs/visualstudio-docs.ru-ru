---
description: В этом разделе описываются внутренние члены класса System. Runtime. CompilerServices. AsyncTaskMethodBuilder.
title: '&lt;Структура AsyncTaskMethodBuilder TResult &gt; — внутренние элементы | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35e1ca4d19727383bdd7c957bc59fd6b6568c9f5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145655"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>&lt;Структура TResult AsyncTaskMethodBuilder &gt; — внутренние элементы
В этом разделе описываются внутренние члены <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> класса. Общие сведения об этом классе см <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> . в разделе справки.

 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Так как вы не можете получить доступ к этим внутренним членам из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Внутренние члены

|Имя|Описание|
|----------|-----------------|
|[ObjectIdForDebugger, свойство](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя в отладчике.|
|[m_task поле](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Представляет сборку с отложенной инициализацией.|

## <a name="see-also"></a>См. также раздел
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Внутренние модули параллельного расширения для платформа .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
