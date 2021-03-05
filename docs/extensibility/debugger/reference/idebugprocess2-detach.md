---
description: Отсоединяет отладчик от этого процесса, отключая все программы в процессе.
title: IDebugProcess2::D етач | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5775ee9ffc3fa3c4151df999b64ba1160da6f7c3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166285"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Отсоединяет отладчик от этого процесса, отключая все программы в процессе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Все программы и процесс продолжают выполняться, но больше не являются частью сеанса отладки. После завершения операции отсоединения больше не будут отправляться события отладки для этого процесса (и его программ).

## <a name="see-also"></a>См. также раздел
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
