---
description: Этот интерфейс представляет символ или тип, который является контейнером для других символов или типов.
title: Идебугконтаинерфиелд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb3a50db80dc2acb075d1c6ec1fe585000468285
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077906"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Этот интерфейс представляет символ или тип, который является контейнером для других символов или типов.

## <a name="syntax"></a>Синтаксис

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик символов реализует этот интерфейс для того же объекта, который реализует интерфейс [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) . Этот интерфейс также является базовым классом для всех интерфейсов, представляющих контейнеры.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Многие методы на многих интерфейсах возвращают этот интерфейс. Поскольку это базовый класс для всех контейнеров, более специализированные интерфейсы могут быть получены из этого интерфейса с помощью [QueryInterface](/cpp/atl/queryinterface). К таким интерфейсам относятся [идебугаррайфиелд](../../../extensibility/debugger/reference/idebugarrayfield.md), [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md), [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md)и [идебугпропертифиелд](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам в интерфейсе [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Создает перечислитель для полей контейнера.|

## <a name="remarks"></a>Remarks
 Массивы (контейнеры для переменных), классы (контейнеры для методов и переменных) и методы (контейнеры для параметров и локальных переменных) являются примерами контейнеров.

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
