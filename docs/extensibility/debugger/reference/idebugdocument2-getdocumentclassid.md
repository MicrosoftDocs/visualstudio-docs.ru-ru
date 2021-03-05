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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36a95914f470d0ce095db0c0db8d1397b02be3cf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166558"
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

## <a name="remarks"></a>Комментарии
 Идентификатор GUID класса можно использовать для создания экземпляров отдельных классов, каждый из которых представляет документ.

## <a name="see-also"></a>См. также раздел
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
