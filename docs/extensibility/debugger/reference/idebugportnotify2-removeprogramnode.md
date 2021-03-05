---
description: Отменяет регистрацию программы, которая может быть отлаживаться из порта, на котором она выполняется.
title: 'IDebugPortNotify2:: Ремовепрограмноде | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2::RemoveProgramNode
helpviewer_keywords:
- IDebugPortNotify2::RemoveProgramNode
ms.assetid: 3668157b-66d2-416e-a359-fc04dcd18a48
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90918aed8652328a8aa02edac3517ec524a6cfa0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142652"
---
# <a name="idebugportnotify2removeprogramnode"></a>IDebugPortNotify2::RemoveProgramNode
Отменяет регистрацию программы, которая может быть отлаживаться из порта, на котором она выполняется.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT RemoveProgramNode( 
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int RemoveProgramNode( 
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Параметры
`pProgramNode`\
окне Объектов [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , представляющий программу для отмены регистрации.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод удаляет узел программы, добавленный с помощью вызова метода [аддпрограмноде](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
