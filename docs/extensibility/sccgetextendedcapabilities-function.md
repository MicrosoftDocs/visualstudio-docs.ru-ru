---
description: Эта функция возвращает дополнительные возможности, поддерживаемые подключаемым модулем системы управления версиями.
title: Функция Сккжетекстендедкапабилитиес | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca2f2f77c586c5c71658a8f0cab32385eb3f73d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073005"
---
# <a name="sccgetextendedcapabilities-function"></a>Функция Сккжетекстендедкапабилитиес
Эта функция возвращает дополнительные возможности, поддерживаемые подключаемым модулем системы управления версиями.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Параметры
 pContext

окне Указатель контекста для подключаемого модуля системы управления версиями.

 лскцекскапс

окне Флаг, указывающий расширенную возможность для тестирования (дополнительные флаги см. в таблице кода расширенной возможности в [флагах возможностей](../extensibility/capability-flags.md) ).

 пбсуппортед

заполняет Возвращает ненулевое значение ( `TRUE` ), если указанная возможность поддерживается; в противном случае возвращает ноль ( `FALSE` ).

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Операция получения возможности успешно завершена.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Произошла неизвестная или Неуказанная ошибка.|

## <a name="remarks"></a>Remarks
 Этот метод вызывается по запросу; то есть, когда необходимо проверить возможность, этот метод вызывается для определения того, поддерживается ли эта возможность. Указан только один флаг за раз.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Коды ошибок](../extensibility/error-codes.md)
- [Флаги возможностей](../extensibility/capability-flags.md)
