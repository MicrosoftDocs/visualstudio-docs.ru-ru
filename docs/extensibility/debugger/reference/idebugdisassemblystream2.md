---
description: Этот интерфейс представляет поток инструкций.
title: IDebugDisassemblyStream2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 760d77ced3cc07da2dd02c21cf3ed0200df14231
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166571"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Этот интерфейс представляет поток инструкций.

## <a name="syntax"></a>Синтаксис

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Обработчик отладки реализует этот интерфейс для поддержки дизассемблированного кода программы.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов метода [жетдисассемблистреам](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugDisassemblyStream2` .

|Метод|Описание|
|------------|-----------------|
|[Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Считывает инструкции, начиная с текущей позицией в потоке дизассемблированного кода.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Перемещает указатель чтения в потоке дизассемблирования на указанное количество инструкций относительно указанной позиции.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Возвращает идентификатор расположения кода для определенного контекста кода.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Возвращает объект контекста кода, соответствующий указанному идентификатору расположения кода.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Возвращает идентификатор расположения кода, представляющий текущее расположение кода.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Возвращает исходный документ, связанный с этим потоком дизассемблированного кода.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Возвращает область этого потока дизассемблированного кода.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Возвращает размер этого потока дизассемблированного кода.|

## <a name="remarks"></a>Комментарии
 Поток дизассемблированного кода может быть создан для представления всего адресного пространства или только функции или модуля внутри пространства. Каждая инструкция представляется структурой [дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md) , возвращаемой вызовом метода [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
