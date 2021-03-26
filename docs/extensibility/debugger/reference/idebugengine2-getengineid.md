---
description: Возвращает идентификатор GUID модуля отладки (DE).
title: 'IDebugEngine2:: Жетенгинеид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d7a483517f89c91005f465c539d2af4b9d442a8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088033"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
Возвращает идентификатор GUID модуля отладки (DE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

## <a name="parameters"></a>Параметры
`pguidEngine`\
заполняет Возвращает идентификатор GUID для DE.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
Примеры типичных идентификаторов GUID: `guidScriptEng` , `guidNativeEng` или `guidSQLEng` . Новые модули отладки будут создавать собственные идентификаторы GUID для идентификации.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CEngine` объекта, реализующего интерфейс [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) .

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
