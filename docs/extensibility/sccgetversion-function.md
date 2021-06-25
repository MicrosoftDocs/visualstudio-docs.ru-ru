---
description: Эта функция возвращает номер версии API подключаемого модуля системы управления версиями, поддерживаемый подключаемым модулем системы управления версиями.
title: Функция Сккжетверсион | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f49d33ebe70390a364d0ae8336e7f69549b6876f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901088"
---
# <a name="sccgetversion-function"></a>Функция SccGetVersion
Эта функция возвращает номер версии API подключаемого модуля системы управления версиями, поддерживаемый подключаемым модулем системы управления версиями.

## <a name="syntax"></a>Синтаксис

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 `LONG`Тип данных, содержащий номер версии поддерживаемого интерфейса API подключаемого модуля системы управления версиями:

|WORD|Описание|
|----------|-----------------|
|HIWORD|Основной номер версии|
|ловорд|Дополнительный номер версии|

## <a name="remarks"></a>Remarks
 Например, если подключаемый модуль системы управления версиями поддерживает версию 1,3 API подключаемого модуля системы управления версиями, эта функция возвратит 0x0103.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
