---
title: 'IDiaStackWalkHelper:: Симболфорва | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f646616fddc0e7727ef9e8e80d9c29fbcba6ebc0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741326"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Извлекает символ, который содержит указанный виртуальный адрес.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT symbolForVA( 
   ULONGLONG     va,
   IDiaSymbol**  ppSymbol
);
```

#### <a name="parameters"></a>Параметры
 `va`

окне Виртуальный адрес, содержащийся в запрошенном символе. Символ должен быть `SymTagFunctionType` (значение из перечисления [перечисления симтаженум](../../debugger/debug-interface-access/symtagenum.md) ).

 `ppSymbol`

заполняет Объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий символ по указанному адресу.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)