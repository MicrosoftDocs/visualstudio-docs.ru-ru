---
description: Возвращает программу, связанную с узлом программы.
title: 'IDebugPortEx2:: @ Program | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetProgram
helpviewer_keywords:
- IDebugPortEx2::GetProgram
ms.assetid: cd83a111-bfd5-4eae-b576-526466c6b6ec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5bb169ecdbd0dcea188054c96af06da609edf3f7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142808"
---
# <a name="idebugportex2getprogram"></a>IDebugPortEx2::GetProgram
Возвращает программу, связанную с узлом программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProgram( 
   IDebugProgramNode2* pProgramNode,
   IDebugProgram2**    ppProgram
);
```

```csharp
int GetProgram( 
   IDebugProgramNode2 pProgramNode,
   out IDebugProgram2 ppProgram
);
```

## <a name="parameters"></a>Параметры
`pProgramNode` окне Объект [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , представляющий узел программы.

`ppProgram` заполняет Возвращает объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, связанную с узлом программы.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
