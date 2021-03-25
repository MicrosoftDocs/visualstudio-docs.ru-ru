---
description: Уведомляет пакет отладки, что в документе были обновлены текстовые атрибуты.
title: 'IDebugDocumentTextEvents2:: Онупдатетекстаттрибутес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateTextAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateTextAttributes
ms.assetid: eb68d69a-1ad9-4ce4-84e1-40979ef16634
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bfa0e9676e408ddc93e42ccb03651598a32f1f7c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094124"
---
# <a name="idebugdocumenttextevents2onupdatetextattributes"></a>IDebugDocumentTextEvents2::onUpdateTextAttributes
Уведомляет пакет отладки, что в документе были обновлены текстовые атрибуты.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT onUpdateTextAttributes( 
   TEXT_POSITION pos,
   DWORD         dwNumToUpdate
);
```

```csharp
int onUpdateTextAttributes( 
   enum_TEXT_POSITION pos,
   uint               dwNumToUpdate
);
```

## <a name="parameters"></a>Параметры
`pos`\
окне Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , показывающая, где были обновлены текстовые атрибуты.

`dwNumToUpdate`\
окне Указывает количество символов в тексте, которые были обновлены.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
