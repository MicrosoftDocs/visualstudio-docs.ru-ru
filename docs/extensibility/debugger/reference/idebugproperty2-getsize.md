---
description: Возвращает размер значения свойства в байтах.
title: 'IDebugProperty2:: DataSize | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd6342efd1d9bcb2d2ac063438ee741df3c61325
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166818"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
Возвращает размер значения свойства в байтах.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>Параметры
`pdwSize`\
заполняет Возвращает размер значения свойства в байтах.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Возвращает значение `S_GETSIZE_NO_SIZE` , если свойство не имеет размера.

## <a name="see-also"></a>См. также раздел
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
