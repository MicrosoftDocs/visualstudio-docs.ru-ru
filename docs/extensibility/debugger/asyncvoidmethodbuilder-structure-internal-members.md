---
description: В этом разделе описываются внутренние члены класса System. Runtime. CompilerServices. AsyncVoidMethodBuilder.
title: Структура AsyncVoidMethodBuilder — внутренние элементы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4097bce1f7fd90c5b73a3bb450a873561d76d9c1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055340"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Структура AsyncVoidMethodBuilder — внутренние элементы
В этом разделе описываются внутренние члены <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> класса. Общие сведения об этом классе см <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> . в разделе справки.

 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Так как вы не можете получить доступ к этим внутренним членам из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Внутренние члены

|Имя|Описание|
|----------|-----------------|
|[ObjectIdForDebugger, свойство](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя в отладчике.|
|[m_objectIdForDebugger поле](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Представляет объект с отложенной инициализацией, используемый отладчиком для уникальной идентификации этого построителя.|

## <a name="see-also"></a>См. также
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Внутренние модули параллельного расширения для платформа .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
