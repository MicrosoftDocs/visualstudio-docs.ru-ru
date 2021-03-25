---
description: Возвращает идентификатор класса документа.
title: 'IDebugDocument2:: Жетдокументклассид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 829f0002a79f2fd5ec69f31ef4b59068bc5b5c05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066858"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Возвращает идентификатор класса документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDocumentClassID( 
   CLSID* pclsid
);
```

```csharp
int GetDocumentClassID( 
   out Guid pclsid
);
```

## <a name="parameters"></a>Параметры
`pclsid` заполняет Возвращает идентификатор GUID, который является ИДЕНТИФИКАТОРом класса документа.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Идентификатор GUID класса можно использовать для создания экземпляров отдельных классов, каждый из которых представляет документ.

## <a name="see-also"></a>См. также
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
