---
description: Возвращает контекст документа, описывающий расположение этого события.
title: 'IDebugCanStopEvent2:: Жетдокументконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44e1f2aa918547d8b3b0b1bea1940072fe2d8f84
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085083"
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
Возвращает контекст документа, описывающий расположение этого события.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocCxt
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocCxt
);
```

## <a name="parameters"></a>Параметры
`ppDocCxt`\
заполняет Возвращает интерфейс [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , представляющий позицию в документе исходного файла, соответствующую текущему расположению кода.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Как правило, контекст документа можно рассматривать как расположение в исходном файле.

 Чтобы получить контекст кода, ориентированный на инструкции кода, вызовите метод [жеткодеконтекст](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) .

## <a name="see-also"></a>См. также
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
