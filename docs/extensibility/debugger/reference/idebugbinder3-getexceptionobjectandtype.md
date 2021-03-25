---
description: Этот метод извлекает исключение, связанное с объектом, если таковой имеется.
title: 'IDebugBinder3:: Жетексцептионобжектандтипе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67f6c146182546f83782a0299c0ea3e29f94a3b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094254"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Этот метод извлекает исключение, связанное с объектом, если таковой имеется.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Параметры
`ppException`\
заполняет Возвращает объект, представляющий исключение.

`ppField`\
заполняет Возвращает объект, представляющий конкретное поле, которое может вызвать исключение (это может быть значение null).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

> [!NOTE]
> Чтобы проверить, существует ли исключение, проверьте значение, возвращаемое `ppException` : если это значение null, то исключение не связано с этим объектом.

## <a name="see-also"></a>См. также
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
