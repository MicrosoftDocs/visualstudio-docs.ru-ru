---
description: Возвращает ссылку на значение свойства.
title: 'IDebugProperty2:: IsReference | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc8a922ad29b7f6b3ecff57ee5df7ad0e7dded1d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064765"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
Возвращает ссылку на значение свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

## <a name="parameters"></a>Параметры
`ppRererence`\
заполняет Возвращает объект [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , представляющий ссылку на значение свойства.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки, обычно `E_NOTIMPL` или `E_GETREFERENCE_NO_REFERENCE` .

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
