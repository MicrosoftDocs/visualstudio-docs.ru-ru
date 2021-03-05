---
description: Делает программу недоступной для отладки.
title: 'IDebugProgramPublisher2:: Унпублишпрограм | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7160b3bd3b954b722828542e8eead4fc6fedebf5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161265"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Делает программу недоступной для отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>Параметры
`pDebuggeeInterface`\
окне `IUnknown` Интерфейс программы. Это то же значение, которое передается в метод [публишпрограм](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) и уникально идентифицирует удаляемую программу (то есть она используется как файл cookie).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Чтобы сделать программу доступной для модулей отладки и диспетчера отладки сеансов, используйте метод [публишпрограм](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
