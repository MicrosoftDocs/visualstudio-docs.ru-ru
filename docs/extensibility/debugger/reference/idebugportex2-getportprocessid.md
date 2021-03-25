---
description: Возвращает идентификатор процесса самого порта.
title: 'IDebugPortEx2:: Жетпортпроцессид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ed85141cc6f127867910777ca6fb5f417326bef5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072524"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Возвращает идентификатор процесса самого порта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

## <a name="parameters"></a>Параметры
`pdwProcessId`\
заполняет Возвращает идентификатор физического процесса самого порта.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Например, в среде выполнения Win32 этот метод обычно вызывает функцию Win32 `GetCurrentProcessId` для получения идентификатора физического процесса.

## <a name="see-also"></a>См. также
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
