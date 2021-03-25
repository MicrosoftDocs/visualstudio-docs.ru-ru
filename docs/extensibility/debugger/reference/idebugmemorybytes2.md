---
description: Этот интерфейс представляет байты памяти.
title: IDebugMemoryBytes2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b18b4575780966d9ad34fa6c5638a89274d52c3c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058642"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Этот интерфейс представляет байты памяти.

## <a name="syntax"></a>Синтаксис

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления байтов в памяти.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
- [Жетмеморибитес](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) возвращает этот интерфейс для предоставления доступа к системной памяти. [Жетмеморибитес](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) и [жетмеморибитес](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) возвращают этот интерфейс для предоставления доступа к байтам объекта.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugMemoryBytes2` .

|Метод|Описание|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Считывает последовательность байтов, начиная с заданного расположения.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Записывает `dwCount` байты, начиная с `pStartContext` .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Возвращает размер (в байтах) памяти, представленной этим интерфейсом.|

## <a name="remarks"></a>Remarks
 Для свойств интерфейс [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий массив, предоставляет `IDebugMemoryBytes2` интерфейс для доступа к значениям в этом массиве.

 **Представление памяти** Visual Studio вызывает [жетмеморибитес](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) для получения `IDebugMemoryBytes2` интерфейса для доступа к системной памяти. Адрес, к которому осуществляется доступ, получается путем синтаксического анализа выражения, указанного в качестве адреса в представлении памяти, и последующей оценки проанализированного выражения с помощью [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для получения `IDebugProperty2` интерфейса. Вызов [жетмемориконтекст](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) возвращает [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , описывающий адрес памяти. Этот контекст памяти затем передается в [реадат](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) и [вритеат](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
