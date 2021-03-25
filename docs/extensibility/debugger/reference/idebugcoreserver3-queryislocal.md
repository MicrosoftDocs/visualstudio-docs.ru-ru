---
description: Определяет, является ли сервер локальным для вызывающего.
title: 'IDebugCoreServer3:: Куерислокал | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::QueryIsLocal
helpviewer_keywords:
- IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e18074c92bdd63c1c378d71d3c84c4dde1745536
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054313"
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
Определяет, является ли сервер локальным для вызывающего.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает, `S_OK` чтобы указать, что сервер является локальным. Возвращает значение `S_FALSE` , если сервер запускается из экземпляра msvsmon.exe, который обычно используется для удаленной отладки.

## <a name="see-also"></a>См. также
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
