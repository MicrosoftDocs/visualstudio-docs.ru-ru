---
description: Завершает процесс.
title: 'IDebugProcess2:: Terminate | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Terminate
helpviewer_keywords:
- IDebugProcess2::Terminate
ms.assetid: 5e6bf373-0fe9-4321-b04a-473a65f664d9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e26a4486e9c97638d20f9c634b66183824c2b39
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081650"
---
# <a name="idebugprocess2terminate"></a>IDebugProcess2::Terminate
Завершает процесс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 После завершения процесса все программы в этом процессе завершаются; ни один из них не может выполнять код.

## <a name="see-also"></a>См. также
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
