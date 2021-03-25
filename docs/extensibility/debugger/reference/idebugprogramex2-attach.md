---
description: Подключение сеанса к программе.
title: 'IDebugProgramEx2:: Attach | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4f7f6a083c37ece73be488ab0c4f6d4c25ce24c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084159"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Подключение сеанса к программе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Параметры
`pCallback`\
окне Объект [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , представляющий функцию обратного вызова, к которой подключенный обработчик отладки отправляет события.

`dwReason`\
окне Значение из перечисления [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) , описывающее причину операции присоединения.

`pSession`\
окне Значение, уникально идентифицирующее сеанс, который подключается к программе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Этот метод должен возвращать `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` значение, если программа уже присоединена.

## <a name="remarks"></a>Remarks
 Порт, содержащий программу, может использовать значение в, `pSession` чтобы определить, какой сеанс пытается подключиться к программе. Например, если порт допускает одновременное подключение только одного сеанса отладки к процессу, порт может определить, подключен ли тот же сеанс к другим программам в процессе.

> [!NOTE]
> Переданный интерфейс `pSession` должен обрабатываться только как файл cookie, значение, однозначно идентифицирующее диспетчер отладки сеанса, присоединенный к этой программе; ни один из методов предоставленного интерфейса не работает.

## <a name="see-also"></a>См. также
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
