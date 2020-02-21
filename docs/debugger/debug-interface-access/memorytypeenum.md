---
title: Меморитипинум | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0710ec5cdfcfcb59407d18b43b885603f017fdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738634"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Указывает тип памяти для доступа.

## <a name="syntax"></a>Синтаксис

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>Параметры
`MemTypeCode` обращается только к памяти кода.

`MemTypeData` обращается к данным или стековой памяти.

`MemTypeStack` обращается только к памяти стека.

`MemTypeAny` обращается к любому типу памяти.

## <a name="remarks"></a>Заметки
Значения в этом перечислении передаются методу [IDiaStackWalkHelper:: readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) , чтобы ограничить доступ к различным типам памяти.

## <a name="requirements"></a>Требования
Заголовок: квконст. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
