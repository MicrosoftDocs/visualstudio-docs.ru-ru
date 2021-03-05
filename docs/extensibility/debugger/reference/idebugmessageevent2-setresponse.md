---
description: Задает ответ, если он есть, из окна сообщения.
title: 'IDebugMessageEvent2:: Сетреспонсе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77170bb95855d91dcad873a5254c0a0937001032
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160047"
---
# <a name="idebugmessageevent2setresponse"></a>IDebugMessageEvent2::SetResponse
Задает ответ, если он есть, из окна сообщения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetResponse( 
   DWORD dwResponse
);
```

```csharp
int SetResponse( 
   uint dwResponse
);
```

## <a name="parameters"></a>Параметры
`dwResponse`\
окне Задает ответ с использованием соглашений `MessageBox` функции Win32. Дополнительные сведения см. в описании функции [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
