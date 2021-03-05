---
description: Возвращает имя компьютера, на котором выполняется процесс, на котором размещается эта программа.
title: 'IDebugProgramHost2:: Жесостмачиненаме | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramHost2::GetHostMachineName
ms.assetid: 4677ffe4-aa9b-4450-a63b-74cd3984d956
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a5ba8a2598af54f700ec85f3e3856b29166f2613
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145252"
---
# <a name="idebugprogramhost2gethostmachinename"></a>IDebugProgramHost2::GetHostMachineName
Возвращает имя компьютера, на котором выполняется процесс, на котором размещается эта программа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetHostMachineName( 
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName( 
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>Параметры
`pbstrHostMachineName`\
заполняет Возвращает имя компьютера.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
