---
description: Этот интерфейс представляет тип переменной.
title: Идебугдинамикфиелд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf1d72bfa38e6af0419e696b267699d10340cc68
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094085"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Этот интерфейс представляет тип переменной.

## <a name="syntax"></a>Синтаксис

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиками символов в качестве базового класса для любого типа, который можно определить во время выполнения. Это только для управляемого кода.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс представляет базовый класс, из которого могут быть производными более специализированные интерфейсы.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 Этот интерфейс не предоставляет никаких методов, кроме тех, которые унаследованы от `IDebugField` .

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
