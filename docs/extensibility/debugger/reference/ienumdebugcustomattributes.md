---
description: Перечисляет пользовательские атрибуты.
title: Иенумдебугкустоматтрибутес | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8decd8d244ad4b55d2bba7381e247535faad9b22
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081078"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Перечисляет пользовательские атрибуты.

## <a name="syntax"></a>Синтаксис

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик символов реализует этот интерфейс для поддержки настраиваемых атрибутов (через интерфейс [идебугкустоматтрибуте](../../../extensibility/debugger/reference/idebugcustomattribute.md) ).

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugCustomAttributes` .

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Извлекает указанное число настраиваемых атрибутов в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Пропускает указанное число настраиваемых атрибутов в последовательности перечисления.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Возвращает число настраиваемых атрибутов в перечислителе.|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
