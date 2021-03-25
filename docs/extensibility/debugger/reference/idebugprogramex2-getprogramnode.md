---
description: Возвращает узел программы, связанный с программой.
title: 'IDebugProgramEx2:: Жетпрограмноде | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 1545ffbf-1422-4b5d-9bb9-314ba8665041
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10e96e69459e591567b873e6268a29249439210a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084068"
---
# <a name="idebugprogramex2getprogramnode"></a>IDebugProgramEx2::GetProgramNode
Возвращает узел программы, связанный с программой.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProgramNode( 
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProgramNode( 
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Параметры
`ppProgramNode`\
заполняет Возвращает объект [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , представляющий узел программы, связанный с этой программой.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
