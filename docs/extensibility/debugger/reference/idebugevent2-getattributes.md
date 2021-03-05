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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7402c2b5a367a3a0a681a9a17ef89872a7b3e96
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152979"
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

## <a name="remarks"></a>Комментарии
 Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) является общим для всех событий. Этот метод описывает тип события; Например, событие является синхронным или асинхронным и является событием остановки.

## <a name="see-also"></a>См. также раздел
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
