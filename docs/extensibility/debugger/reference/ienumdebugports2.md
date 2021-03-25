---
description: Этот интерфейс перечисляет порты компьютера или поставщика порта.
title: IEnumDebugPorts2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 66598460a48c960b78cb89315fff6bd7ac9a845e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064596"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Этот интерфейс перечисляет порты компьютера или поставщика порта.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский поставщик портов реализует этот интерфейс для представления списка портов, созданных поставщиком. Visual Studio реализует этот интерфейс для поддержки собственного поставщика порта.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [енумпортс](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) , чтобы получить этот интерфейс, представляющий список портов, созданных поставщиком порта. Вызовите [енумперсистедпортс](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) , чтобы получить этот интерфейс, представляющий список портов, сохраненных на диске.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugPorts2` .

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Извлекает указанное число портов в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Пропускает указанное число портов в последовательности перечисления.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Возвращает количество портов в перечислителе.|

## <a name="remarks"></a>Remarks
 Visual Studio использует этот интерфейс для заполнения списка портов, используемых для присоединения к процессам.

 Модуль отладки обычно не использует этот интерфейс.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
