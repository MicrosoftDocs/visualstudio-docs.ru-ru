---
description: Этот интерфейс представляет собой расположение в адресном пространстве компьютера, на котором выполняется отлаживаемая программа.
title: IDebugMemoryContext2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5a967c992fc55065c50dbbe173495e7c1199df59
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058486"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Этот интерфейс представляет собой расположение в адресном пространстве компьютера, на котором выполняется отлаживаемая программа.

## <a name="syntax"></a>Синтаксис

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления адреса в памяти.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов [жетмемориконтекст](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) или [жетмемориконтекст](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) возвращает этот интерфейс. Кроме того, вызовы [Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) и [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) возвращают новые копии этого интерфейса после применения соответствующей арифметической операции.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugMemoryContext2` .

|Метод|Описание|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Возвращает отображаемое пользователем имя для этого контекста.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Возвращает сведения, описывающие этот контекст.|
|[Добавление](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Добавляет указанное значение в адрес текущего контекста для создания нового контекста.|
|[Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Вычитает указанное значение из адреса текущего контекста, чтобы создать новый контекст.|
|[Сравнить](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Сравнивает два контекста способом, указанным в параметре Compare flags.|

## <a name="remarks"></a>Remarks
 Окно **памяти** Visual Studio вызывает [жетмемориконтекст](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) , чтобы получить `IDebugMemoryContext2` интерфейс, содержащий вычисленное выражение, используемое для адреса памяти. Затем этот контекст передается в [реадат](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) и [вритеат](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) , чтобы указать адрес для чтения или записи.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
