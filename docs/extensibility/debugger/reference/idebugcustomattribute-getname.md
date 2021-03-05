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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 313408639b0a93faef0c63c0add92dc1ca2e947b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163061"
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

## <a name="remarks"></a>Комментарии
 Имя, возвращаемое этим методом, соответствует имени класса, используемого для объявления атрибута. Это может не совпадать с именем самого класса настраиваемого атрибута, так как C# позволяет удалять суффикс "Attribute" из имени настраиваемого атрибута при его использовании в объявлении.

## <a name="see-also"></a>См. также раздел
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
