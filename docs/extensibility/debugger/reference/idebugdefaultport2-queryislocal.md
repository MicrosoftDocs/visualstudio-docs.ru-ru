---
description: Этот метод определяет, находится ли этот порт на локальном компьютере.
title: 'IDebugDefaultPort2:: Куерислокал | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e678e1219bfc9c64fe33be545e82e7fbb596b2db
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067131"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Этот метод определяет, находится ли этот порт на локальном компьютере.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает, `S_OK` Если этот порт является локальным (на том же компьютере, что и вызывающий объект), или `S_FALSE` порт находится на другом компьютере.

## <a name="see-also"></a>См. также
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
