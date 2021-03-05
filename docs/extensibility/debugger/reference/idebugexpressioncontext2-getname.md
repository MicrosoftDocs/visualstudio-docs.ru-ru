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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d43af7eeb733aca978a4c3b09fd4f97ca828fe5a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152653"
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

## <a name="remarks"></a>Комментарии
 Имя является описанием этого контекста оценки. Обычно это то, что может быть проанализировано средством оценки выражений, ссылающимся на этот точный контекст оценки. Например, в C++ имя имеет следующий вид:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>См. также раздел
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
