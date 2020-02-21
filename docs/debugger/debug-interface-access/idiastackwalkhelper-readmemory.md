---
title: 'IDiaStackWalkHelper:: readMemory | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57afd033b2d969a4ed57dc713b2c4266e0ead632
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741364"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Считывает блок данных из образа исполняемого файла в памяти.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>Параметры
 `type`

окне Значение из перечисления [перечисления меморитипинум](../../debugger/debug-interface-access/memorytypeenum.md) , указывающее тип памяти для чтения.

 va

окне Виртуальный адрес в образе, с которого начинается чтение.

 `cbData`

окне Размер буфера данных в байтах.

 `pcbData`

заполняет Возвращает число фактически считанных байтов. Если `pbData` `NULL`, то это общее число доступных данных в байтах.

 `pbData`

[вход, выход] Буфер, который заполняется считанной памятью.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Перечисление MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)