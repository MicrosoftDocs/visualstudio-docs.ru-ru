---
description: Эта функция завершает пакет операций системы управления версиями.
title: Функция Скцендбатч | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11ff596f19d3a98b929f9346bbf579e0ad1258c5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904595"
---
# <a name="sccendbatch-function"></a>Функция Скцендбатч
Эта функция завершает пакет операций системы управления версиями. Эти пакеты не могут быть вложенными.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Выполнение пакета операций успешно завершено.|
|SCC_E_UNKNOWNERROR|Неконкретный сбой.|

## <a name="remarks"></a>Remarks
 Пакеты управления версиями используются для выполнения одних и тех же операций с системой управления версиями в нескольких проектах или в нескольких контекстах. Пакеты можно использовать для исключения избыточных диалоговых окон из-за работы пользователя во время пакетной операции. [Сккбегинбатч](../extensibility/sccbeginbatch-function.md) и `SccEndBatch` функция используются в качестве пары для указания начала и конца операции. Они не могут быть вложенными.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
