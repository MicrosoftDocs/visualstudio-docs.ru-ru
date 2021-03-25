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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 43651baac29b3904b9bc12d8d4b965ca1cd8e3ee
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066184"
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

## <a name="remarks"></a>Remarks
 При этом загружаются отладочные символы для всех модулей, на которые ссылается этот модуль отладки. Символы загружаются, только если они еще не загружены. Поиск символов выполняется по путям, заданным путем вызова [сетсимболпас](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>См. также
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
