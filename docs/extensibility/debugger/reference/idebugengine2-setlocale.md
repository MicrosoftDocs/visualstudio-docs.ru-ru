---
description: Задает языковой стандарт модуля отладки (DE).
title: 'IDebugEngine2:: SetLocale | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54cfd2d9d51cbad414cfb481b88f1e3277500efa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153915"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Задает языковой стандарт модуля отладки (DE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale( 
   ushort wLangID
);
```

## <a name="parameters"></a>Параметры
`wLangID`\
окне Указывает языковой стандарт языка. Например, 1033 для английского языка.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод вызывается диспетчером отладки сеансов (SDM) для распространения параметров языкового стандарта интегрированной среды разработки, чтобы строки, возвращаемые методом DE, были правильно локализованы.

## <a name="see-also"></a>См. также раздел
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
