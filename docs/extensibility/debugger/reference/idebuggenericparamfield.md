---
description: Представляет параметр для универсального типа управляемого кода.
title: Идебугженерикпарамфиелд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2dc01aaf3485e89ac32b4a4fd86c7491a1f96853
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091933"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Представляет параметр для универсального типа управляемого кода.

## <a name="syntax"></a>Синтаксис

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Используется для поддержки универсальных шаблонов.

## <a name="methods"></a>Методы
 В дополнение к методам в интерфейсе [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Возвращает число ограничений, связанных с этим универсальным параметром.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Извлекает ограничения, связанные с этим универсальным параметром.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Получает флаги для этого универсального параметра.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Получает индекс этого универсального параметра.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Возвращает имя этого универсального параметра.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Возвращает владельца типа или метода этого универсального параметра.|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
