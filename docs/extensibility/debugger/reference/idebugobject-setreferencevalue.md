---
description: Задает значение ссылки для этого объекта.
title: 'Идебугобжект:: Сетреференцевалуе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a65c14d4122ac6d877573822b4fa8be1cb6cdd1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054118"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Задает значение ссылки для этого объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Параметры
`pObject`\
окне Объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий новое значение ссылки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод делает этот объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) ссылкой на значение объекта, указанного в `pObject` параметре, вызывая предыдущую ссылку. Обратите внимание, что этот `IDebugObject` объект уже должен быть ссылочным типом.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
