---
description: Возвращает поле, к которому присоединен настраиваемый атрибут.
title: 'Идебугкустоматтрибуте:: Жетпарентфиелд | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4af4569b64a41fc84a09c7e8f2ce0a8f6b42e86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154513"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Возвращает поле, к которому присоединен настраиваемый атрибут.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Параметры
`ppField`\
заполняет Возвращает объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий поле, к которому присоединен настраиваемый атрибут.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Вызовите метод [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md) для возвращенного объекта [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , чтобы определить, какой тип поля является родительским.

## <a name="see-also"></a>См. также раздел
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
