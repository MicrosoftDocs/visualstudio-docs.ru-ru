---
title: 'IDiaSymbol:: get_liveRangeLength | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeLength
ms.assetid: ffcce3cc-085c-44eb-8145-46e3819c54f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b663ef54959544764016fe59e4b0fb41607854b1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739932"
---
# <a name="idiasymbolget_liverangelength"></a>IDiaSymbol::get_liveRangeLength
Возвращает длину диапазона адресов, в котором является допустимым локальный символ.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_liveRangeLength ( 
   ULONGLONG* length
);
```

#### <a name="parameters"></a>Параметры
 `length`

заполняет Возвращает длину диапазона адресов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

> [!NOTE]
> Возвращенный код ошибки означает, что символ не содержит сведений о диапазоне в реальном времени.

## <a name="remarks"></a>Заметки

## <a name="requirements"></a>Требования
 Заголовок: Dia2. h

 Библиотека: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)