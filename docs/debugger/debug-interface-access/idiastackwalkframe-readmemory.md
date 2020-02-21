---
title: 'IDiaStackWalkFrame:: readMemory | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae1201fca1fc25cce19b40b47d6435d02d80e1b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741479"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Считывает память из образа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT readMemory ( 
   MemoryTypeEnum type,
   ULONGLONG va,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Параметры
 `type`

окне Одно из значений перечисления [перечисления меморитипинум](../../debugger/debug-interface-access/memorytypeenum.md) , указывающее тип памяти для доступа.

 `va`

окне Расположение виртуального адреса в образе для начала чтения.

 `cbData`

окне Размер буфера данных в байтах.

 `pcbData`

заполняет Возвращает число возвращенных байтов. Если `data` `NULL`, `pcbData` содержит общее количество доступных данных в байтах.

 `data`

заполняет Буфер, который должен быть заполнен данными из указанного расположения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)