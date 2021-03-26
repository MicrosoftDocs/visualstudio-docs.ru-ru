---
description: УСТАРЕВШИЕ. Перезагружает символы для этого модуля.
title: 'IDebugModule2:: ReloadSymbols_Deprecated | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5dfcd1edd92048cde6da6cc195c3e0ba8f1cd392
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065714"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
УСТАРЕВШИЕ. НЕ ИСПОЛЬЗУЙТЕ. Перезагружает символы для этого модуля.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>Параметры
`pszUrlToSymbols`\
окне Путь к хранилищу символов.

`pbstrDebugMessage`\
заполняет Возвращает информационное сообщение, например состояние или сообщение об ошибке, которое отображается справа от имени модуля в окне модули.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Модуль отладки должен всегда возвращать значение `E_FAIL` .

## <a name="remarks"></a>Remarks
 Этот метод больше не поддерживается. Вместо этого реализуйте метод [лоадсимболс](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) .

## <a name="see-also"></a>См. также
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
