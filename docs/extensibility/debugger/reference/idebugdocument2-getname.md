---
description: Возвращает имя документа в одной из нескольких форм.
title: 'IDebugDocument2:: Name | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49c9a2b4fd95fbb24b28b69003c8e462b09be38b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066819"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Возвращает имя документа в одной из нескольких форм.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>Параметры
`gnType`\
окне Значение из перечисления [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) , определяющее тип возвращаемого имени.

`pbstrFileName`\
заполняет Возвращает строку, содержащую имя документа.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод может, например, возвращать имя документа в виде заголовка или имя файла или даже часть имени файла.

## <a name="see-also"></a>См. также
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
