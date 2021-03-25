---
description: Возвращает идентификатор расположения кода для определенного контекста кода.
title: 'IDebugDisassemblyStream2:: Жеткоделокатионид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f68ee6ff0495fe36d8de8ccf0e3c2c81f3d05ac5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067092"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Возвращает идентификатор расположения кода для определенного контекста кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>Параметры
`pCodeContext`\
окне Объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) для преобразования в идентификатор.

`puCodeLocationId` заполняет Возвращает идентификатор расположения кода. См. заметки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает значение, `E_CODE_CONTEXT_OUT_OF_SCOPE` Если контекст кода является допустимым, но находится за пределами области.

## <a name="remarks"></a>Remarks
 Идентификатор расположения кода зависит от модуля отладки (DE), поддерживающего дизассемблирование. Этот идентификатор расположения используется для внутренних целей DE для трассировки положений в коде и обычно является адресом или смещением какого-либо типа. Единственное требование заключается в том, что если контекст кода одного места меньше, чем контекст кода другого расположения, соответствующий идентификатор местоположения кода первого контекста кода также должен быть меньше, чем идентификатор расположения кода второго контекста кода.

 Чтобы получить контекст кода для идентификатора расположения кода, вызовите метод [жеткодеконтекст](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .

## <a name="see-also"></a>См. также
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
