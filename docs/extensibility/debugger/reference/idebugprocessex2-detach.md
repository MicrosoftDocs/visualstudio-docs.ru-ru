---
description: Этот метод информирует процесс о том, что сеанс больше не находится в процессе отладки.
title: IDebugProcessEx2::D етач | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3140da647b46a1cbc3b60691e820238c2c6c83eb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166259"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Этот метод информирует процесс о том, что сеанс больше не находится в процессе отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Параметры
`pSession`\
окне Значение, уникально идентифицирующее сеанс, из которого отсоединяется этот процесс.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Переданный интерфейс `pSession` должен обрабатываться только как файл cookie, значение которого однозначно определяет диспетчер отладки сеанса, изначально подключенный к этому процессу; ни один из методов предоставленного интерфейса не работает.

## <a name="see-also"></a>См. также раздел
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
