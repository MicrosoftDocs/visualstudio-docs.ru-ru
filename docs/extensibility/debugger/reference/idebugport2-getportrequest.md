---
description: Возвращает описание порта, который ранее использовался для создания порта (если он доступен).
title: 'IDebugPort2:: Жетпортрекуест | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77224f98d953b61529ffed083e7be4cee0ed662f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087487"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Возвращает описание порта, который ранее использовался для создания порта (если он доступен).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>Параметры
`ppRequest`\
заполняет Возвращает объект [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) , представляющий запрос, который использовался для создания порта.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  Возвращает значение, `E_PORT_NO_REQUEST` Если порт не был создан с помощью запроса порта [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) .

## <a name="see-also"></a>См. также
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
