---
description: Задает основной сервер для поставщика порта.
title: 'IDebugPortSupplierEx2:: Сетсервер | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2::SetServer
ms.assetid: 0e8ef194-3a4f-4abf-8382-4607ab3005d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81de22828536dd118cb69ed4c3c73d51f55a8535
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071913"
---
# <a name="idebugportsupplierex2setserver"></a>IDebugPortSupplierEx2::SetServer
Задает основной сервер для поставщика порта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetServer(
   IDebugCoreServer2* pServer
);
```

```csharp
int SetServer(
   IDebugCoreServer2 pServer
);
```

## <a name="parameters"></a>Параметры
`pServer`\
Основной сервер, устанавливаемый для поставщика порта.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugPortSupplierEx2](../../../extensibility/debugger/reference/idebugportsupplierex2.md)
