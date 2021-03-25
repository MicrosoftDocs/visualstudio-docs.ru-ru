---
description: Возвращает атрибуты для данного события отладки.
title: 'IDebugEvent2:: OutAttribute | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b41e3f50b73c16c9acb28a809b8c33b535370c47
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065857"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Возвращает атрибуты для данного события отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>Параметры
`pdwAttrib`\
заполняет Сочетание флагов из перечисления [евентаттрибутес](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) является общим для всех событий. Этот метод описывает тип события; Например, событие является синхронным или асинхронным и является событием остановки.

## <a name="see-also"></a>См. также
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
