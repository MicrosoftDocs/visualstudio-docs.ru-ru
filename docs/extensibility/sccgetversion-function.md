---
description: Эта функция возвращает номер версии API подключаемого модуля системы управления версиями, поддерживаемый подключаемым модулем системы управления версиями.
title: Функция Сккжетверсион | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 42273951768591dc89f4c9e4b9a27de1d646e209
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063816"
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
