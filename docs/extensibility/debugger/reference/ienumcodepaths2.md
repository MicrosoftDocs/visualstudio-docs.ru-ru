---
description: Этот интерфейс представляет список путей кода.
title: IEnumCodePaths2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e8ff8b4532ab67a969c8270eeb83bdf715e0b1c0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091738"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Этот интерфейс представляет список путей кода.

## <a name="syntax"></a>Синтаксис

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления списка путей кода.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Чтобы получить этот интерфейс, вызовите [енумкодепасс](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) .

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumCodePaths2` .

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Извлекает указанное число ветвей кода в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Пропускает указанное число ветвей кода в последовательности перечисления.|
|[Сброс](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Клонировать](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Возвращает число ветвей кода в перечислителе.|

## <a name="remarks"></a>Remarks
 Путь к коду представляет точку ветвления или вызов функции в программе. Список путей к коду представляет путь, по которому был выполнен код.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
