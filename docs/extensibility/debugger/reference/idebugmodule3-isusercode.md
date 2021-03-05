---
description: Получает сведения о том, представляет ли модуль пользовательский код.
title: 'IDebugModule3:: Исусеркоде | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a936d4408b2d289477a860ffca3d53ca7b0ad61d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164842"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Получает сведения о том, представляет ли модуль пользовательский код.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>Параметры
`pfUser`\
заполняет Ненулевое ( `TRUE` ) Если модуль представляет пользовательский код, ноль ( `FALSE` ), если нет.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
