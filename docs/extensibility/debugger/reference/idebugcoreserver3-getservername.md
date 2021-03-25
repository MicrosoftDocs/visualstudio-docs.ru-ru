---
description: Возвращает имя сервера.
title: IDebugCoreServer3::/имя_сервера | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerName
helpviewer_keywords:
- IDebugCoreServer3::GetServerName
ms.assetid: 0fc3fcf5-d6a3-4a00-bf14-458b8645714e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c052e4995498c5b134126ceff39ac4ce3176311d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054339"
---
# <a name="idebugcoreserver3getservername"></a>IDebugCoreServer3::GetServerName
Возвращает имя сервера.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetServerName(
   BSTR* pbstrName
);
```

```csharp
int GetServerName(
   out string pbstrName
);
```

## <a name="parameters"></a>Параметры
`pbstrName`\
заполняет Возвращает имя сервера.

> [!NOTE]
> Вызывающий объект отвечает за освобождение строки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Для понятного имени сервера вызовите метод [жетсерверфриендлинаме](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md) .

## <a name="see-also"></a>См. также
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)
