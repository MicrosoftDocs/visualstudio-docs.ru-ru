---
description: Регистрирует программу, которую можно отладить с помощью порта, на котором она запущена.
title: 'IDebugPortNotify2:: Аддпрограмноде | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2::AddProgramNode
helpviewer_keywords:
- IDebugPortNotify2::AddProgramNode
ms.assetid: 34c0e949-1eb9-4108-9cb8-a3eb87fcf190
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 186bfbfd44a88450aeade264020f70e0eddc7fb8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142587"
---
# <a name="idebugportnotify2addprogramnode"></a>IDebugPortNotify2::AddProgramNode
Регистрирует программу, которую можно отладить с помощью порта, на котором она запущена.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT AddProgramNode( 
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int AddProgramNode( 
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Параметры
`pProgramNode`\
окне Объект [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , представляющий программу для регистрации.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Можно отменить регистрацию узла программы в порте, вызвав метод [ремовепрограмноде](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
