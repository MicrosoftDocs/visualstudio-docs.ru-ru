---
description: Возвращает тип класса настраиваемого атрибута.
title: 'Идебугкустоматтрибуте:: Жетаттрибутетипефиелд | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0d0cfdfcdb49c934d9f4c0288f66a52e3e48f49
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088098"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
Возвращает тип класса настраиваемого атрибута.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAttributeTypeField( 
   IDebugClassField** ppCAType
);
```

```csharp
int GetAttributeTypeField(
   out IDebugClassField ppCAType
);
```

## <a name="parameters"></a>Параметры
`ppCAType`\
заполняет Возвращает объект [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , представляющий класс, для которого настраиваемый атрибут является экземпляром.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Настраиваемый атрибут всегда является классом. Этот метод предоставляет доступ к объекту [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , который описывает этот класс.

## <a name="see-also"></a>См. также
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
