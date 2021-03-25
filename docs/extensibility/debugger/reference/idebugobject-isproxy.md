---
description: Определяет, является ли объект прозрачным прокси-сервером.
title: 'Идебугобжект:: прокси | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f66c8f460e284776f15e393a4adbc8bfd0ea9076
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054144"
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
Определяет, является ли объект прозрачным прокси-сервером.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsProxy (
   BOOL* pfIsProxy
);
```

```csharp
int IsProxy (
   out bool pfIsProxy
);
```

## <a name="parameters"></a>Параметры
`pfIsProxy`\
[out] `TRUE` значение, если объект является прозрачным прокси-сервером; в противном случае — `FALSE` .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод реализуется модулем отладки C++ по умолчанию.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
