---
description: Указывает, как модуль отладки (DE) должен выполнять обработку данного исключения.
title: 'IDebugEngine2:: Сетексцептион | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 543cccbbefd12accd75213f255f8e3b677cdea38
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153942"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Указывает, как модуль отладки (DE) должен выполнять обработку данного исключения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Параметры
`pException`\
окне Структура [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , описывающая исключение и способ его отладки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Команда DE может быть указана для того, чтобы программа не создавала исключение при первой попытке, во второй вероятности или вообще не была.

## <a name="see-also"></a>См. также раздел
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
