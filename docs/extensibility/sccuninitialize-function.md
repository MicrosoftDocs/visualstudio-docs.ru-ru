---
description: Эта функция очищает все выделения или открытые соединения, созданные с помощью предыдущего вызова СкЦинитиализе, при подготовке к завершению работы подключаемого модуля системы управления версиями.
title: Функция Сккунинитиализе | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d46aedd3e962d0684689ff29a34061b777fe08e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904078"
---
# <a name="sccuninitialize-function"></a>Функция SccUninitialize
Эта функция очищает все выделения или открытые соединения, созданные с помощью предыдущего вызова [скЦинитиализе](../extensibility/sccinitialize-function.md) , при подготовке к завершению работы подключаемого модуля системы управления версиями.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Параметры
 пвконтекст

окне Указатель на структуру контекста подключаемого модуля системы управления версиями, созданную в [скЦинитиализе](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Очистка успешно завершена.|

## <a name="remarks"></a>Remarks
 Подключаемый модуль системы управления версиями отвечает за подготовку к завершению работы и освобождение памяти, выделенной подключаемым модулем для структуры контекста. Функция вызывается один раз для каждого заданного экземпляра подключаемого модуля. Вызов [скЦинитиализе](../extensibility/sccinitialize-function.md) предшествует этому вызову. Проекты по-прежнему не могут быть открыты во время вызова `SccUninitialize` .

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
