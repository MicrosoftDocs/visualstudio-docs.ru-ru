---
description: Получает размер текста в данной позиции в документе.
title: 'IDebugDocumentText2:: DataSize | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91dd1b2a510589ab048bd1bd290b0ab4aabe571b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167312"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Получает размер текста в данной позиции в документе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>Параметры
`pcNumLines`\
заполняет Возвращает количество строк текста.

`pcNumChars`\
заполняет Возвращает количество символов текста.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии

 [Только C++] Если определенное значение не требуется, передайте значение NULL для параметра.

 [Только C#] Необходимо указать оба параметра.

## <a name="see-also"></a>См. также раздел
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
