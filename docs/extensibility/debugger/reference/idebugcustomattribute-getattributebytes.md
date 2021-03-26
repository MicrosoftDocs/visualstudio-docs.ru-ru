---
description: Возвращает сведения об атрибуте в виде большого двоичного объекта в байтах.
title: 'Идебугкустоматтрибуте:: Жетаттрибутебитес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84d6e807e3be6d0fbdaa94834fbc8cad37f8e4d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088085"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Возвращает сведения об атрибуте в виде большого двоичного объекта в байтах.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>Параметры
`ppBlob`\
[вход, выход] Массив, который заполняется байтами атрибута.

`pdwLen`\
[вход, выход] Указывает максимальное число байтов, возвращаемых в `ppBlob` массиве, и возвращает число байтов, фактически записанных в массив.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Установите `ppBlob` для параметра значение null, чтобы получить количество доступных атрибутов в байтах. Затем выделите массив и передайте этот массив в `ppBlob` параметр.

 Байты атрибутов представляют необработанные данные настраиваемого атрибута.

## <a name="see-also"></a>См. также
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
