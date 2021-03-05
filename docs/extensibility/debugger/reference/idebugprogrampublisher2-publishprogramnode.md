---
description: Делает узел программы доступным для использования механизмами отладки (DEs) и диспетчером отладки сеансов (SDM).
title: IDebugProgramPublisher2::P Ублишпрограмноде | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 56d407e22aabb396b331c14047f5a1753a5adf09
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161330"
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
Делает узел программы доступным для использования механизмами отладки (DEs) и диспетчером отладки сеансов (SDM).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT PublishProgramNode(
   IDebugProgramNode2 *pProgramNode
);
```

```csharp
int PublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Параметры
`pProgramNode`\
окне Объект [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , представляющий узел программы, который нужно сделать доступным.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод позволяет программам запрашивать информацию, прежде чем выбирать и запускать их для отладки.

 Чтобы удалить узел программы из уровня доступности, вызовите метод [унпублишпрограмноде](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)
