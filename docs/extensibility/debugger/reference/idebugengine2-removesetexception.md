---
description: Удаляет указанное исключение, поэтому оно больше не обрабатывается модулем отладки.
title: 'IDebugEngine2:: Ремовесетексцептион | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b763291fccd39d46b32347d89df1a11e1b3d09f2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095411"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Удаляет указанное исключение, поэтому оно больше не обрабатывается модулем отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Параметры
`pException`\
окне Структура [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , описывающая удаляемое исключение.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Удаляемое исключение должно быть ранее задано предыдущим вызовом метода [сетексцептион](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Чтобы удалить все исключения из набора, вызовите метод [ремовеаллсетексцептионс](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) .

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
