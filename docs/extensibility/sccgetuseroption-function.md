---
description: Эта функция получает разнообразные параметры, относящиеся к пользователю.
title: Функция Сккжетусероптион | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 622abc04609edf410214af6b8acf795f969e2fbc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901114"
---
# <a name="sccgetuseroption-function"></a>Функция SccGetUserOption
Эта функция получает разнообразные параметры, относящиеся к пользователю.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Параметры
 pContext

окне Указатель контекста для подключаемого модуля системы управления версиями.

 ноптион

окне Параметр для извлечения (см. раздел Примечания для возможных параметров).

 лпвал

заполняет Значение, связанное с параметром.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Параметр успешно получен.|
|SCC_E_OPNOTSUPPORTED|Параметр не поддерживается.|
|SCC_E_NONSPECIFICERROR|Произошла неизвестная ошибка.|

## <a name="remarks"></a>Remarks
 Эта команда поддерживает следующие параметры:

|Параметр пользователя|Описание|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Определяет, хочет ли пользователь извлечь локальную версию файлов. `lpVal` назначается `SCC_USEROPT_COLV_YES` (пользователь хочет извлечь локальные файлы) или `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Код ошибки](../extensibility/error-codes.md)
