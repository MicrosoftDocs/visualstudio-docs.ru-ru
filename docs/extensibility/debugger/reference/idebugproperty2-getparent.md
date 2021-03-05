---
description: Возвращает родительское свойство свойства.
title: 'IDebugProperty2:: Parent | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ae5557734ab59a2e71a67404a50519d72ca1ec0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166831"
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
Возвращает родительское свойство свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetParent ( 
   IDebugProperty2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugProperty2 ppParent
);
```

## <a name="parameters"></a>Параметры
`ppParent`\
заполняет Возвращает объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий родительский элемент свойства.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. При отсутствии родительского объекта возвращает значение `S_GETPARENT_NO_PARENT`.

## <a name="see-also"></a>См. также раздел
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
