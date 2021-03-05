---
description: Уведомляет получателя о том, что атрибуты документа были обновлены.
title: 'IDebugDocumentTextEvents2:: Онупдатедокументаттрибутес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateDocumentAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateDocumentAttributes
ms.assetid: 31b7d151-9ce2-438e-b405-f8cc46b9f537
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7c6f4ca65043410c8d2f3e6e843b10c149709f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154149"
---
# <a name="idebugdocumenttextevents2onupdatedocumentattributes"></a>IDebugDocumentTextEvents2::onUpdateDocumentAttributes
Уведомляет получателя о том, что атрибуты документа были обновлены.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT onUpdateDocumentAttributes( 
   TEXT_DOC_ATTR_2 textdocattr
);
```

```csharp
int onUpdateDocumentAttributes( 
   enum_TEXT_DOC_ATTR_2 textdocattr
);
```

## <a name="parameters"></a>Параметры
`textdocattr`\
окне Сочетание флагов из перечисления [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) , которое указывает обновленные атрибуты документа.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)
