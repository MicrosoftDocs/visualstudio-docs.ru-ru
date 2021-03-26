---
description: Удаляет порт.
title: 'IDebugPortSupplier2:: Ремовепорт | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::RemovePort
helpviewer_keywords:
- IDebugPortSupplier2::RemovePort
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0ff1cd6a165800f7a3acdaf69de2040d25d53b9c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071991"
---
# <a name="idebugportsupplier2removeport"></a>IDebugPortSupplier2::RemovePort
Удаляет порт.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT RemovePort( 
   IDebugPort2* pPort
);
```

```csharp
int RemovePort( 
   IDebugPort2 pPort
);
```

## <a name="parameters"></a>Параметры
`pPort`\
окне Объект [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , представляющий удаляемый порт.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод удаляет порт из внутреннего списка активных портов поставщика порта.

## <a name="see-also"></a>См. также
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
