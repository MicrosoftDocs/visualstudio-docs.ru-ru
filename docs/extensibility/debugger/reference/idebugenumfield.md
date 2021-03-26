---
description: Этот интерфейс представляет тип перечисления.
title: Идебуженумфиелд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 18671f8f719dc797709677a14417eaa0a54aaea2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092531"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Этот интерфейс представляет тип перечисления.

## <a name="syntax"></a>Синтаксис

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик символов реализует этот интерфейс для представления перечисления.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из интерфейса [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , если метод [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает `FIELD_TYPE_ENUM` .

## <a name="methods-in-vtable-order"></a>Методы в порядке VTable
 Помимо методов в `IDebugField` `IDebugContainerField` интерфейсах и, этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Возвращает [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , описывающий имя для этого типа перечисления.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Возвращает имя константы перечисления, связанной с заданным значением.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Возвращает значение, связанное с заданным именем константы перечисления|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Возвращает значение, связанное с заданным именем константы перечисления, но без учета регистра.|

## <a name="remarks"></a>Remarks
 Это базовый символ, фактически привязанный к расположению с [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Выполняется](../../../extensibility/debugger/reference/idebugbinder-bind.md)
