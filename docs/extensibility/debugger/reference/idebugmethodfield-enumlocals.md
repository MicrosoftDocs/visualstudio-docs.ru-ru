---
description: Создает перечислитель для выбранных локальных переменных метода.
title: 'Идебугмесодфиелд:: Енумлокалс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d99b6e4b3cf30cccd4a2785f3712b34d9471bdd8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166337"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Создает перечислитель для выбранных локальных переменных метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Параметры
`pAddress`\
окне Объект [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) , представляющий адрес отладки, который выбирает контекст или область, из которой должны быть получены локальные переменные.

`ppLocals`\
заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список локальных переменных. в противном случае возвращает значение null, если нет локальных переменных.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает S_OK или возвращает S_FALSE, если нет локальных переменных. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Комментарии
Перечисляются только те переменные, которые определены в блоке, содержащем заданный адрес отладки. Если требуются все локальные переменные, включая все созданные компилятором локальные переменные, вызовите метод [енумалллокалс](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) .

Метод может содержать несколько контекстов области или блоков. Например, следующий метод надуманный содержит три области, два внутренних блока и сам текст метода.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

Объект [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md) представляет `func` сам метод. При вызове `EnumLocals` метода с [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) , для которого задан `Inner Scope 1` адрес, возвращается перечисление `temp1` , содержащее переменную, например.

## <a name="see-also"></a>См. также раздел
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
