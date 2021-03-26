---
description: Возвращает контекст документа, соответствующий данному контексту кода.
title: 'IDebugCodeContext2:: Жетдокументконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80420f12369ef038c2faccb51c9b1bfc9b0073a4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088423"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Возвращает контекст документа, соответствующий данному контексту кода. Контекст документа представляет собой расположение в исходном файле, соответствующее исходному коду, вызвавшему эту инструкцию.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>Параметры
`ppSrcCxt`\
заполняет Возвращает объект [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , соответствующий контексту кода. Если `S_OK` возвращается значение, этого не должно быть `null` .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Модуль отладки должен возвращать код сбоя, например, если `E_FAIL` в `out` `null` контексте кода нет связанной с исходным положением.

## <a name="remarks"></a>Remarks
 Как правило, контекст документа можно рассматривать как расположение в исходном файле, в то время как контекст кода является позицией инструкции кода в потоке выполнения.

## <a name="see-also"></a>См. также
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
