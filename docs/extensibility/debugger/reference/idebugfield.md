---
description: Этот интерфейс представляет поле, то есть описание символа или типа.
title: Идебугфиелд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 175f9a329a93587873db7c76b53757ba715ace67
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151848"
---
# <a name="idebugfield"></a>IDebugField
Этот интерфейс представляет поле, то есть описание символа или типа.

## <a name="syntax"></a>Синтаксис

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик символов реализует этот интерфейс в качестве базового класса для всех полей.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс является базовым классом для всех полей. В зависимости от возвращаемого значения [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md)этот интерфейс может возвращать более специализированные интерфейсы с помощью [QueryInterface](/cpp/atl/queryinterface). Кроме того, многие интерфейсы возвращают `IDebugField` объекты из различных методов.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugField` .

|Метод|Описание|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Возвращает воспроизводимую информацию о символе или типе.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Возвращает тип поля.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Возвращает тип поля.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Возвращает контейнер поля.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Возвращает адрес поля.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Возвращает размер поля в байтах.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Получает расширенные сведения о поле.|
|[Равно](../../../extensibility/debugger/reference/idebugfield-equal.md)|Сравнивает два поля.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Получает независимые от типа сведения о символе или типе.|

## <a name="remarks"></a>Комментарии
 Тип эквивалентен языку C `typedef` .

 В следующем примере языка C++ `weather` — это тип класса, а `sunny` `stormy` — символы:

```cpp
class weather;
weather sunny;
weather stormy;
```

 , Представляет ли поле символ или тип, можно определить путем вызова метода [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md) и проверки результата [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) . Если `FIELD_KIND_TYPE` задан бит, то поле является типом, а если `FIELD_KIND_SYMBOL` бит задан, то это символ.

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
