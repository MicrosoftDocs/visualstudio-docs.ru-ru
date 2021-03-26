---
description: Представляет определение поля для универсального типа управляемого кода.
title: Идебугженерикфиелддефинитион | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0c9b2a4b9dbdbf5d1b5faefb8dfbf498f873ec01
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063361"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Представляет определение поля для универсального типа управляемого кода.

## <a name="syntax"></a>Синтаксис

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Конструирует экземпляр поля по заданному массиву аргументов типа.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Получает параметры типа с учетом количества параметров.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Извлекает количество параметров типа, связанных с универсальным полем.|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
