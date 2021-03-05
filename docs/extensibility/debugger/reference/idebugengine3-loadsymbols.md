---
description: Загружает (при необходимости) символы для всех модулей, отлаживаемых с помощью этого модуля отладки.
title: 'IDebugEngine3:: Лоадсимболс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4b4f210ef07ad10b35251582dd8a3c0fe3b0685
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153811"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Загружает (при необходимости) символы для всех модулей, отлаживаемых с помощью этого модуля отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 При этом загружаются отладочные символы для всех модулей, на которые ссылается этот модуль отладки. Символы загружаются, только если они еще не загружены. Поиск символов выполняется по путям, заданным путем вызова [сетсимболпас](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>См. также раздел
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
