---
description: Этот интерфейс предоставляет доступ к типам, псевдонимам и пользовательским службам визуализатора.
title: IDebugBinder3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29d8b642a66a75dd561b0a87cd5fa083e841139c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085160"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс предоставляет доступ к типам, псевдонимам и пользовательским службам визуализатора.

## <a name="syntax"></a>Синтаксис

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки реализует этот интерфейс для поддержки псевдонимов, пользовательских служб визуализатора и доступа к сведениям о типе объекта.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Интерфейс [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md) получает этот интерфейс с помощью [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 В дополнение к методам, предоставляемым интерфейсом [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md) , этот интерфейс реализует следующее:

|Метод|Описание|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Извлекает объект памяти, представляющий память, к которой привязан этот объект.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Извлекает исключение, связанное с этим объектом (если имеется),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Получает псевдоним с заданным именем.|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Извлекает массив всех псевдонимов для данного объекта,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Возвращает число типов аргументов, связанных с этим объектом.|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Извлекает список типов аргументов, связанных с этим объектом,|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Получает интерфейс для службы визуализатора,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Преобразует расположение объекта или адрес 64-разрядной памяти в контекст памяти.|

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
