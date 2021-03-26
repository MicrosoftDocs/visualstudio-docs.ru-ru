---
description: Сбрасывает перечисление путей кода к первому элементу.
title: 'IEnumCodePaths2:: Reset | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Reset
helpviewer_keywords:
- IEnumCodePaths2::Reset
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac7be476f1ec119d43b8794e5d2e1be02d66f521
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091790"
---
# <a name="ienumcodepaths2reset"></a>IEnumCodePaths2::Reset
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
 После вызова этого метода следующий вызов метода [Next](../../../extensibility/debugger/reference/ienumcodepaths2-next.md) возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
