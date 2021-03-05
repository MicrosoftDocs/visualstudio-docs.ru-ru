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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7cfc3ba650ff8277bb6cb85f5d1530d202bd426
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163087"
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

## <a name="remarks"></a>Комментарии
 Установите `ppBlob` для параметра значение null, чтобы получить количество доступных атрибутов в байтах. Затем выделите массив и передайте этот массив в `ppBlob` параметр.

 Байты атрибутов представляют необработанные данные настраиваемого атрибута.

## <a name="see-also"></a>См. также раздел
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
