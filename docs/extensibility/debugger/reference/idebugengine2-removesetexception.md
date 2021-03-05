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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 588037ef9dcf495f8fbbb210acc3154c31558a32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153953"
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

## <a name="remarks"></a>Комментарии
 Удаляемое исключение должно быть ранее задано предыдущим вызовом метода [сетексцептион](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Чтобы удалить все исключения из набора, вызовите метод [ремовеаллсетексцептионс](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
