---
description: Сбрасывает перечисление Programs к первому элементу.
title: 'IEnumDebugPrograms2:: Reset | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Reset
helpviewer_keywords:
- IEnumDebugPrograms2::Reset
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a54961b40f4bde286d2adfd0b8bb791a9750583e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079960"
---
# <a name="ienumdebugprograms2reset"></a>IEnumDebugPrograms2::Reset
Сбрасывает перечисление на первый элемент.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 После вызова этого метода следующий вызов метода [Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md) возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
