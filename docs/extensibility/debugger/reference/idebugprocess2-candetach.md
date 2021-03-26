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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0ffc6e8ee787960baf7ccb709ab76ab5d66be4d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071692"
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

## <a name="see-also"></a>См. также
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
