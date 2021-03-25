---
description: Этот интерфейс перечисляет список модулей.
title: IEnumDebugModules2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96a35f11346b769a4329b1212a8202e5e5ded006
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058174"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Этот интерфейс перечисляет список модулей.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления списка модулей, загруженных для программы.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Visual Studio вызывает [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugModules2` .

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Извлекает указанное число модулей в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Пропускает указанное число модулей в последовательности перечисления.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Возвращает число модулей.|

## <a name="remarks"></a>Remarks
 Visual Studio использует этот интерфейс в основном для обновления окна " **модули** ".

 В целях отладки в Visual Studio программа — это логическая последовательность инструкций кода, которая может пересекать границы модуля, поэтому требуется список модулей для одного интерфейса [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Первый модуль в списке обычно содержит начальную точку входа для связанной программы.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
