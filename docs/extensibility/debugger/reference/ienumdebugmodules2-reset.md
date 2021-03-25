---
description: Сбрасывает перечисление modules к первому элементу.
title: 'IEnumDebugModules2:: Reset | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Reset
helpviewer_keywords:
- IEnumDebugModules2::Reset
ms.assetid: f6ff364c-2644-4919-b950-3cb82eb6f601
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de8ef3fa6b5b35d27c37802ee8cdcd6e4845e46
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080038"
---
# <a name="ienumdebugmodules2reset"></a>IEnumDebugModules2::Reset
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
 После вызова этого метода следующий вызов метода [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
