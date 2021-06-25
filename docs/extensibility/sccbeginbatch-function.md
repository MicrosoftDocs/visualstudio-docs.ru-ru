---
description: Эта функция запускает пакетную последовательность операций системы управления версиями.
title: Функция Сккбегинбатч | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 08b9199b98e566a71bfeb95124ebd85781e69950
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904764"
---
# <a name="sccbeginbatch-function"></a>Функция Сккбегинбатч
Эта функция запускает пакетную последовательность операций системы управления версиями. Для завершения пакета будет вызван [скцендбатч](../extensibility/sccendbatch-function.md) . Эти пакеты не могут быть вложенными.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Пакетная операция успешно началась.|
|SCC_E_UNKNOWNERROR|Неконкретный сбой.|

## <a name="remarks"></a>Remarks
 Пакеты управления версиями используются для выполнения одних и тех же операций в нескольких проектах или нескольких контекстах. Пакеты можно использовать для исключения избыточных диалоговых окон для отдельных проектов из процесса выполнения пакетной операции. `SccBeginBatch`Функция и [скцендбатч](../extensibility/sccendbatch-function.md) используются в качестве пары функций для указания начала и конца операции. Они не могут быть вложенными. `SccBeginBatch` задает флаг, указывающий, что выполняется пакетная операция.

 Во время выполнения пакетной операции подключаемый модуль системы управления версиями должен представлять максимум одно диалоговое окно для любого вопроса пользователя и применять ответ от этого диалогового окна во всех последующих операциях.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
