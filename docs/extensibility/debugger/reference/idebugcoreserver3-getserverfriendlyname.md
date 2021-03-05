---
description: Возвращает понятное имя для сервера.
title: 'IDebugCoreServer3:: Жетсерверфриендлинаме | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1ccb77cca920706dc7622e98dfca62743bf3b65
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163113"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Возвращает понятное имя для сервера.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

## <a name="parameters"></a>Параметры
`pbstrName`\
заполняет Возвращает понятное имя для сервера.

> [!NOTE]
> Вызывающий объект отвечает за освобождение строки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Для серверов, запускаемых пользователем, имя, возвращаемое этим методом, является полным именем сервера. Для автоматического запуска серверов используется имя компьютера, на котором запущен сервер.

 Для имени, ориентированного на компьютер, вызовите метод- [ServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [Имя_сервера](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
