---
description: Возвращает контекст документа, описывающий расположение в документе, который должен быть сделан активным пакетом отладки.
title: 'IDebugActivateDocumentEvent2:: Жетдокументконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocumentContext
helpviewer_keywords:
- GetDocumentContext method
- IDebugActivateDocumentEvent2::GetDocumentContext method
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 680382e43feee9298a2de99933847ea633982a15
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154942"
---
# <a name="idebugactivatedocumentevent2getdocumentcontext"></a>IDebugActivateDocumentEvent2::GetDocumentContext
Возвращает контекст документа, описывающий расположение в документе, который должен быть сделан активным пакетом отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocContext
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Параметры
`ppDocContext`\
заполняет Возвращает объект [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , представляющий расположение в исходном файле документа.

## <a name="remarks"></a>Комментарии
 Это расположение может использоваться для отображения курсора, например.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
