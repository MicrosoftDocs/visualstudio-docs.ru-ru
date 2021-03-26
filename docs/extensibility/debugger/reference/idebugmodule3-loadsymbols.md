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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e8a9c34c85263ab538bf07b10b87f12fddf12db
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065519"
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

## <a name="remarks"></a>Remarks
 Этот метод загружает символы из текущего пути поиска (который можно изменить, вызвав метод [сетсимболпас](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) ).

 Этот метод является предпочтительным по сравнению с методом [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) .

## <a name="see-also"></a>См. также
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
