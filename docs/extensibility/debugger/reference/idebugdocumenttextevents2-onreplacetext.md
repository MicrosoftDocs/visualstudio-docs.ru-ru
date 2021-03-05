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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14b90f0ca28447e9e987767026165b0ff615f88c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167273"
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

## <a name="see-also"></a>См. также раздел
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
