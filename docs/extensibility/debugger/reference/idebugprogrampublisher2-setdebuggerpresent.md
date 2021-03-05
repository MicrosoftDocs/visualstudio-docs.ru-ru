---
description: Сообщает издателю программы, что отладчик имеется и работает.
title: 'IDebugProgramPublisher2:: Сетдебугжерпресент | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3db8703ed05fd4a386b9265998de2f27017d0d76
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161291"
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
Сообщает издателю программы, что отладчик имеется и работает.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetDebuggerPresent(
   BOOL fDebuggerPresent
);
```

```csharp
int SetDebuggerPresent(
   int fDebuggerPresent
);
```

## <a name="parameters"></a>Параметры
`fDebuggerPresent`\
окне Ненулевое значение ( `TRUE` ), если имеется отладчик, ноль ( `FALSE` ), если нет.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Присутствие или отсутствие отладчика отражается в данных, возвращаемых методом [жетпровидерпроцессдата](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) : возвращаемое значение задается или сбрасывается при предыдущем вызове `SetDebuggerPresent` метода.

## <a name="see-also"></a>См. также раздел
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
