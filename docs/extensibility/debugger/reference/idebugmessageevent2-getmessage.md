---
description: Возвращает отображаемое сообщение.
title: IDebugMessageEvent2::/сообщение | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc9b1747a504b761b369b2995dfef4c28ff3d012
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058473"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Возвращает отображаемое сообщение.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMessage( 
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrMessage,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetMessage( 
   out enum_MESSAGETYPE pMessageType,
   out string           pbstrMessage,
   out uint             pdwType,
   out string           pbstrHelpFileName,
   out uint             dwHelpId
);
```

## <a name="parameters"></a>Параметры
`pMessageType`\
заполняет Возвращает значение из перечисления [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) , которое описывает тип сообщения.

`pbstrMessage`\
заполняет Возвращает сообщение.

`pdwType`\
заполняет Возвращает тип сообщения с использованием соглашений `MessageBox` функции Win32. Дополнительные сведения см. в описании функции [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) .

`pbstrHelpFileName`\
[вход, выход] Возвращает имя файла справки. Может иметь значение null (C++) или пустое (C#), если файл справки отсутствует.

`pdwHelpId`\
[вход, выход] Возвращает идентификатор справки. Может иметь значение 0, если нет справки, связанной с этим сообщением.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
