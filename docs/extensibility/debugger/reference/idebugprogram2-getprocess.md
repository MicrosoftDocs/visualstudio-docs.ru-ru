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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d87d863b954a9865ff3960f2f2cdd45ac40ce58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065402"
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

## <a name="remarks"></a>Remarks
 Если модуль отладки (DE) не реализует интерфейс [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , реализация этого метода de всегда должна возвращаться, `E_NOTIMPL` поскольку de не может определить, какой процесс выполняется в и, следовательно, не может удовлетворить реализацию этого метода.

 Реализация `IDebugEngineLaunch2` интерфейса означает, что de должен уметь создавать процесс, поэтому реализация интерфейса [IDEBUGPROGRAM2](../../../extensibility/debugger/reference/idebugprogram2.md) в de может определить процесс, в котором он выполняется.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
