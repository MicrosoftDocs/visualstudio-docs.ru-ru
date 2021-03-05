---
description: Определяет, может ли диспетчер отладки сеанса (SDM) отсоединить процесс.
title: 'IDebugProcess2:: Кандетач | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e876d5642cf8a4b7b60f5119839e64959f296e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151679"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Определяет, может ли диспетчер отладки сеанса (SDM) отсоединить процесс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает значение, `S_OK.` `S_FALSE` Если отладчик не может отсоединиться от процесса. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
