---
description: Проверяет, может ли поставщик порта добавлять новые порты.
title: 'IDebugPortSupplier2:: Канаддпорт | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad704eda53807d344b23736d2d9b55e172c36468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072212"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Проверяет, может ли поставщик порта добавлять новые порты.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Возвращаемое значение
 Если порт можно добавить, возвращает значение `S_OK` ; в противном случае возвращается значение, `S_FALSE` указывающее, что порты не могут быть добавлены к этому поставщику портов.

## <a name="remarks"></a>Remarks
 Вызовите этот метод перед вызовом метода [аддпорт](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) , так как последний метод создает порт, а также добавляет его, что может занять много времени.

## <a name="see-also"></a>См. также
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
