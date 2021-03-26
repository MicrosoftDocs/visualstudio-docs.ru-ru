---
description: Этот метод информирует процесс о том, что сеанс теперь отлаживается процесс.
title: 'IDebugProcessEx2:: Attach | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: da538b5ba91a976e96f447ba63843f20ae0b6f62
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076372"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Этот метод информирует процесс о том, что сеанс теперь отлаживается процесс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Параметры
`pSession`\
окне Значение, уникально идентифицирующее сеанс, присоединяемый к этому процессу.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Переданный интерфейс `pSession` должен обрабатываться только как файл cookie, значение, однозначно идентифицирующее диспетчер отладки сеанса, присоединенный к этому процессу; ни один из методов предоставленного интерфейса не работает.

## <a name="see-also"></a>См. также
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
