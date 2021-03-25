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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9499af30f9e9139d0ff64fcf17695b7a4ad69c9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066338"
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

## <a name="remarks"></a>Remarks

 [Только C++] Если определенное значение не требуется, передайте значение NULL для параметра.

 [Только C#] Необходимо указать оба параметра.

## <a name="see-also"></a>См. также
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
