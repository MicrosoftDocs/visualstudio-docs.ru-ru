---
description: Эта функция очищает все выделения или открытые соединения, созданные с помощью предыдущего вызова СкЦинитиализе, при подготовке к завершению работы подключаемого модуля системы управления версиями.
title: Функция Сккунинитиализе | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 187451aba5151c95d8947bd4f5a1419894cc65e7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221331"
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

## <a name="remarks"></a>Комментарии
 Подключаемый модуль системы управления версиями отвечает за подготовку к завершению работы и освобождение памяти, выделенной подключаемым модулем для структуры контекста. Функция вызывается один раз для каждого заданного экземпляра подключаемого модуля. Вызов [скЦинитиализе](../extensibility/sccinitialize-function.md) предшествует этому вызову. Проекты по-прежнему не могут быть открыты во время вызова `SccUninitialize` .

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
