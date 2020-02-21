---
title: 'IDiaSymbol:: Финдчилдренексбяддр | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4dc49d9501e72fb81849943144973574a0d55fef
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741286"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
Возвращает дочерние символы символа, которые являются допустимыми по указанному адресу.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findChildrenExByAddr ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `symtag`

окне Задает Теги символов для извлекаемых дочерних элементов, как определено в [перечислении симтаженум](../../debugger/debug-interface-access/symtagenum.md). Задайте значение `SymTagNull`, чтобы получить все дочерние элементы.

 `name`

окне Указывает имя извлекаемых дочерних элементов. Задайте значение `NULL`, чтобы получить все дочерние элементы.

 `compareFlags`

окне Задает параметры сравнения, применяемые к соответствию имен. Значения из перечисления [перечисления намесеарчоптионс](../../debugger/debug-interface-access/namesearchoptions.md) можно использовать отдельно или в сочетании.

 `address`

окне Адрес символа.

 `ppResult`

заполняет Возвращает объект [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md) , содержащий список извлеченных дочерних символов.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает `S_OK`, если хотя бы один дочерний элемент символа был найден, или `S_FALSE` значение, если не найдено потомков. в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 В число возвращаемых локальных символов входят сведения о диапазоне в реальном времени.

## <a name="requirements"></a>Требования
 Заголовок: Dia2. h

 Библиотека: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)