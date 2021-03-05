---
description: Определяет, содержится ли в данном документе расположение документа.
title: 'IDebugDocumentPosition2:: Испоситиониндокумент | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4800f3735e2d015e3638a642e8c0d54829ddd4c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154292"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Определяет, содержится ли в данном документе расположение документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsPositionInDocument( 
   IDebugDocument2* pDoc
);
```

```csharp
int IsPositionInDocument( 
   IDebugDocument2 pDoc
);
```

## <a name="parameters"></a>Параметры
`pDoc`\
окне Объект [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , представляющий документ, содержащий кандидат.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод используется главным образом при задании точек останова в интерфейсах [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) . По мере загрузки документов вызывается точка останова, чтобы определить, содержит ли документ эту точку.

## <a name="see-also"></a>См. также раздел
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
