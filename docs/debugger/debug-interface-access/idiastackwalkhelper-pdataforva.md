---
title: IDiaStackWalkHelper::p Датафорва | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d51736a80021847881db164c9e176a010124638
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741403"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Возвращает блок данных PDATA, связанный с виртуальным адресом.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>Параметры
 `va`

окне Указывает виртуальный адрес данных для получения.

 `cbData`

окне Размер данных в байтах для получения.

 `pcbData`

заполняет Возвращает фактический размер данных в байтах, которые были получены.

 `pbData`

[вход, выход] Буфер, который заполняется запрошенными данными. Не может иметь значение `NULL`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если для указанного адреса не существует PDATA. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Заметки
 В разделе PDATA (раздел с именем ". pdata") компилируемого объекта содержатся сведения об обработке исключений для функций.

 Вызывающий объект знает, сколько данных должно быть возвращено, поэтому вызывающему объекту не нужно запрашивать, сколько данных доступно. Таким образом, можно реализовать этот метод, чтобы он возвращал ошибку, если параметр `pbData` имеет значение `NULL`.

## <a name="see-also"></a>См. также
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)