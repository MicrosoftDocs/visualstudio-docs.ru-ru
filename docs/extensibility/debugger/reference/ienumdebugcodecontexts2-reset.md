---
description: Сбрасывает перечисление контекстов кода к первому элементу.
title: 'IEnumDebugCodeContexts2:: Reset | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Reset
helpviewer_keywords:
- IEnumDebugCodeContexts2::Reset
ms.assetid: df6cf1e3-2ef8-4d38-81a0-8e9adf151884
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 48df7ce32f085ea387f6ce49e891a0f0e01eb2cf
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226960"
---
# <a name="ienumdebugcodecontexts2reset"></a>IEnumDebugCodeContexts2::Reset
Сбрасывает перечисление на первый элемент.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 После вызова этого метода следующий вызов метода [Next](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md) возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
