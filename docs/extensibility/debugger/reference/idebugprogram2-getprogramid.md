---
description: Возвращает идентификатор GUID для этой программы.
title: 'IDebugProgram2:: Жетпрограмид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45721d4214c396f3366bd23c2bc48e74a1427ec8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168967"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Возвращает идентификатор GUID для этой программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>Параметры
`pguidProgramId`\
заполняет Возвращает `GUID` для этой программы.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Модуль отладки (DE) должен возвращать идентификатор программы, изначально переданный в методы [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) или [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) . Это позволяет идентифицировать программу в разных компонентах отладчика.

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
