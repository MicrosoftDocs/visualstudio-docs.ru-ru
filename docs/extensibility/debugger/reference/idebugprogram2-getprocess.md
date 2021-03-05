---
description: Получите процесс, в котором выполняется эта программа.
title: 'IDebugProgram2:: выполнить процесс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 233bd9bbb41f64b375e899dba9c0be9a9fba3d97
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168993"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Получите процесс, в котором выполняется эта программа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Параметры
`ppProcess`\
заполняет Возвращает интерфейс [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий процесс.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Если модуль отладки (DE) не реализует интерфейс [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , реализация этого метода de всегда должна возвращаться, `E_NOTIMPL` поскольку de не может определить, какой процесс выполняется в и, следовательно, не может удовлетворить реализацию этого метода.

 Реализация `IDebugEngineLaunch2` интерфейса означает, что de должен уметь создавать процесс, поэтому реализация интерфейса [IDEBUGPROGRAM2](../../../extensibility/debugger/reference/idebugprogram2.md) в de может определить процесс, в котором он выполняется.

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
