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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ec511cc6145c890c4f62a76563c51aa7c667977
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167637"
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

## <a name="see-also"></a>См. также раздел
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
