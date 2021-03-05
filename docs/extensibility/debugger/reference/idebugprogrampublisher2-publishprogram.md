---
description: Этот метод делает программу доступной для модулей отладки (DEs) и диспетчера отладки сеанса.
title: IDebugProgramPublisher2::P Ублишпрограм | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2904376efa1a6798cbba967b93ad1c93d395b919
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171593"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Этот метод делает программу доступной для модулей отладки (DEs) и диспетчера отладки сеанса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT PublishProgram(
   CONST_GUID_ARRAY Engines,
   LPCOLESTR        szFriendlyName,
   IUnknown*        pDebuggeeInterface
);
```

```csharp
int PublishProgram(
   CONST_GUID_ARRAY Engines,
   string           szFriendlyName,
   object           pDebuggeeInterface
);
```

## <a name="parameters"></a>Параметры
`Engines`\
окне Массив идентификаторов GUID для DEs, который может запускать или присоединяться к этой программе.

`szFriendlyName`\
окне Понятное имя программы (отображается в меню или диалоговых окнах, предоставленных пользователю).

`pDebuggeeInterface`\
[входные] `IUnknown` интерфейс для программы (это значение используется в качестве файла cookie для уникальной идентификации программы; это же значение используется для отмены публикации программы).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Чтобы программа стала недоступной для отладки, вызовите [унпублишпрограм](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).

## <a name="see-also"></a>См. также раздел
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
