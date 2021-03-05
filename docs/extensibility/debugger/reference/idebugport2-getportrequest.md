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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 084e8bb94356ea4e2cff1fa83e83e7e08b35134e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142873"
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

## <a name="see-also"></a>См. также раздел
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
