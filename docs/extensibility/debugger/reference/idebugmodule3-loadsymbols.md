---
description: Загружает символы для текущего модуля.
title: 'IDebugModule3:: Лоадсимболс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0612be8ffdde8a942331a89e08298f71414a4c76
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164829"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Загружает символы для текущего модуля.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Возвращаемое значение
 Если метод завершается успешно, возвращает значение `S_OK`. В противном случае функция возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод загружает символы из текущего пути поиска (который можно изменить, вызвав метод [сетсимболпас](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) ).

 Этот метод является предпочтительным по сравнению с методом [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
