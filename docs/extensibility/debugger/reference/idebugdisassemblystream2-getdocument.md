---
description: Возвращает исходный документ, связанный с этим входным потоком.
title: 'IDebugDisassemblyStream2:: \ Document | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetDocument
helpviewer_keywords:
- IDebugDisassemblyStream2::GetDocument
ms.assetid: 3d039a44-ebaa-4413-ac18-7cfd92c408bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d214cf9be09dea4a4bf244224a5ae1bd6d882ef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067001"
---
# <a name="idebugdisassemblystream2getdocument"></a>IDebugDisassemblyStream2::GetDocument
Возвращает исходный документ, связанный с этим входным потоком.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDocument( 
   BSTR              bstrDocumentUrl,
   IDebugDocument2** ppDocument
);
```

```csharp
int GetDocument( 
   string              bstrDocumentUrl,
   out IDebugDocument2 ppDocument
);
```

## <a name="parameters"></a>Параметры
`bstrDocumentUrl`\
окне URL-адрес документа.

`ppDocument`\
заполняет Возвращает объект [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , представляющий документ.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод реализуется механизмами отладки, которые содержат текстовые документы, которые не хранятся в фактическом файле.

## <a name="see-also"></a>См. также
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
