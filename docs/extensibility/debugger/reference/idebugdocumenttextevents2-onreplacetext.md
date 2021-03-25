---
description: Уведомляет пакет отладки, что текст был заменен в документе.
title: 'IDebugDocumentTextEvents2:: Онреплацетекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnReplaceText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onReplaceText
ms.assetid: cb39f025-66d8-4dc0-bef6-1bdc8e07db92
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9f57c0a48e523a57582130107a0d8b1012b1232e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054352"
---
# <a name="idebugdocumenttextevents2onreplacetext"></a>IDebugDocumentTextEvents2::onReplaceText
Уведомляет пакет отладки, что текст был заменен в документе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT onReplaceText( 
   TEXT_POSITION pos,
   DWORD         dwNumToReplace
);
```

```csharp
int onReplaceText( 
   enum_TEXT_POSITION pos,
   uint               dwNumToReplace
);
```

## <a name="parameters"></a>Параметры
`pos`\
окне [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) указывает, где текст был заменен.

`dwNumToReplace`\
окне Указывает количество символов в тексте, которые были заменены.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
