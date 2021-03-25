---
description: Создает перечислитель для типа каждого аргумента, необходимого для вызова метода.
title: 'Идебугмесодфиелд:: Енумаргументс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ba48eb4d98c1ab331ee898a219584b7a4b6cf1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058421"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Создает перечислитель для типа каждого аргумента, необходимого для вызова метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Параметры
`ppParams`\
заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список типов аргументов. Возвращает значение null, если аргументы отсутствуют.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK или возвращает S_FALSE, если аргументы отсутствуют. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
 Каждый элемент является объектом [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющим типы каждого параметра. Вызовите метод " [info](../../../extensibility/debugger/reference/idebugfield-getinfo.md) ", чтобы получить сведения о типе каждого параметра.

 Если требуется имя параметра вместе с типом, вызовите метод [енумпараметерс](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) .

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
