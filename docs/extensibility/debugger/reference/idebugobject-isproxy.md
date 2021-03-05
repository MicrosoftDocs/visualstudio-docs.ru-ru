---
description: Определяет, является ли объект прозрачным прокси-сервером.
title: 'Идебугобжект:: прокси | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9cc2bc45a1e4cfe3e71f07bd2305aa0c7f1fde8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161495"
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

## <a name="remarks"></a>Комментарии
 Этот метод реализуется модулем отладки C++ по умолчанию.

## <a name="see-also"></a>См. также раздел
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
