---
description: Создает перечислитель для вложенных перечислителей этого класса.
title: 'Идебугклассфиелд:: Енумнестеденумс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2e0d908c88b82e9ed706ab919050e1f4943df0c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088566"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Создает перечислитель для вложенных перечислителей этого класса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список вложенных перечислений. Возвращает значение null, если нет вложенных перечислений.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает S_OK или возвращает S_FALSE, если нет вложенных перечислителей. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
Каждый элемент перечисления является объектом [идебуженумфиелд](../../../extensibility/debugger/reference/idebugenumfield.md) , описывающим вложенное перечисление.

Перечисление, объявленное внутри класса, считается вложенным перечислением. Например, если учитывать, что:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

`EnumNestedEnums`Метод возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , содержащий один объект [идебуженумфиелд](../../../extensibility/debugger/reference/idebugenumfield.md) , представляющий `NestedEnum` перечисление.

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
