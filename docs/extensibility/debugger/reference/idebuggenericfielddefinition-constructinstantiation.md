---
description: Конструирует экземпляр поля по заданному массиву аргументов типа.
title: 'Идебугженерикфиелддефинитион:: Конструктинстантиатион | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4565077357678725a6601ac14c48cfce21ec9101
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063439"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Конструирует экземпляр поля по заданному массиву аргументов типа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>Параметры
`cArgs`\
окне Число аргументов в `ppArgs` массиве.

`ppArgs`\
окне Массив, содержащий аргументы типа. Аргументы типа должны быть закрытыми типами (не универсальными или полностью созданными универсальными классами).

`ppConstructedField`\
заполняет Возвращает интерфейс [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий новое поле.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Ограничения не проверяются.

## <a name="see-also"></a>См. также
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
