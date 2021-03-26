---
description: Извлекает список контекстов кода для заданной позицией в исходном файле.
title: 'IDebugProgram2:: Енумкодеконтекстс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2dbcc3f967f0569efcfc1287ba2b215760ce0b34
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076060"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Извлекает список контекстов кода для заданной позицией в исходном файле.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumCodeContexts( 
   IDebugDocumentPosition2*  pDocPos,
   IEnumDebugCodeContexts2** ppEnum
);
```

```csharp
int EnumCodeContexts( 
   IDebugDocumentPosition2     pDocPos,
   out IEnumDebugCodeContexts2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`pDocPos`\
окне Объект [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) , представляющий абстрактное расположение в исходном файле, известном интегрированной среде разработки.

`ppEnum` заполняет Возвращает объект [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) , содержащий список контекстов кода.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод позволяет диспетчеру отладки сеансов (SDM) или интегрированной среде разработки сопоставлять расположение исходного файла с позицией в коде. Если источник создает несколько блоков кода (например, шаблоны C++), возвращается более одного контекста кода.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
