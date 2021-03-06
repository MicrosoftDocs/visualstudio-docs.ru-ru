---
description: Этот интерфейс представляет коллекцию объектов, реализующих интерфейс Идебугаддресс.
title: Иенумдебугаддрессес | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea9e4115c1664e1dcd05041f7ece056b5de01dae
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222644"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Этот интерфейс представляет коллекцию объектов, реализующих интерфейс [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="syntax"></a>Синтаксис

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиком символов для предоставления наборов объектов, реализующих интерфейс [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) . Обратите внимание, что это не стандартное перечисление COM из-за наличия метода [NOCOUNT](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс возвращается [жетаддрессесфромконтекст](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) и [жетаддрессесфромпоситион](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Извлекает из перечисления следующий набор объектов [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .|
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Пропускает указанное число записей.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Сбрасывает перечисление до первой записи.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Извлекает копию текущего перечисления.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Возвращает количество записей в перечислении.|

## <a name="remarks"></a>Комментарии
 Этот интерфейс обычно используется модулем отладки для определения подходящего адреса, который будет предоставлен средству оценки выражений.

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
