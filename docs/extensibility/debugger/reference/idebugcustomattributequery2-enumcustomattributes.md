---
description: Возвращает перечислитель для всех настраиваемых атрибутов, прикрепленных к этому полю.
title: 'IDebugCustomAttributeQuery2:: EnumCustomAttributes | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5bcd11f3058de191a3b0a77f0316afb6140769fc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077646"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Возвращает перечислитель для всех настраиваемых атрибутов, прикрепленных к этому полю.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
заполняет Возвращает объект [иенумдебугкустоматтрибутес](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) , представляющий список настраиваемых атрибутов. в противном случае возвращает значение null, если нет настраиваемых атрибутов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK или S_FALSE, если в этом поле нет настраиваемых атрибутов. В противном случае возвращает код ошибки;

## <a name="remarks"></a>Remarks
 Поле может иметь несколько настраиваемых атрибутов.

## <a name="see-also"></a>См. также
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
