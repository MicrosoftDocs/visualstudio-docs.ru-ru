---
description: Возвращает имя настраиваемого атрибута.
title: 'Идебугкустоматтрибуте:: Name | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7be47a763d4809d6e62b65660c39187d2d130065
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088072"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Возвращает имя настраиваемого атрибута.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Параметры
`bstrName`\
заполняет Возвращает строку, содержащую имя пользовательского атрибута.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Имя, возвращаемое этим методом, соответствует имени класса, используемого для объявления атрибута. Это может не совпадать с именем самого класса настраиваемого атрибута, так как C# позволяет удалять суффикс "Attribute" из имени настраиваемого атрибута при его использовании в объявлении.

## <a name="see-also"></a>См. также
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
