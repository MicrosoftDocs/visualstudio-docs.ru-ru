---
title: 'IDiaSymbol:: get_liveRangeStartRelativeVirtualAddress | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea82e9d1dee4b82e78ea3f6409acfdcfc30b2a27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739897"
---
# <a name="idiasymbolget_liverangestartrelativevirtualaddress"></a>IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
Возвращает начало диапазона адресов, в котором является допустимым локальный символ.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_liveRangeStartRelativeVirtualAddress ( 
   DWORD* address
);
```

#### <a name="parameters"></a>Параметры
 `address`

заполняет Возвращает начало диапазона адресов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращаемый относительный виртуальный адрес — это начало диапазона, в котором символ является допустимым.

> [!NOTE]
> Возвращенный код ошибки означает, что символ не содержит сведений о диапазоне в реальном времени.

## <a name="remarks"></a>Заметки

## <a name="requirements"></a>Требования
 Заголовок: Dia2. h

 Библиотека: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)