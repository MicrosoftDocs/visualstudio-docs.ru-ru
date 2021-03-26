---
description: Возвращает имя контекста вычисления.
title: 'IDebugExpressionContext2:: Name | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c3aa27ba70e0b407e72a42d2904467ee85fc027b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092323"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Возвращает имя контекста вычисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Параметры
`pbstrName`\
заполняет Возвращает имя контекста вычисления.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Имя является описанием этого контекста оценки. Обычно это то, что может быть проанализировано средством оценки выражений, ссылающимся на этот точный контекст оценки. Например, в C++ имя имеет следующий вид:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>См. также
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
