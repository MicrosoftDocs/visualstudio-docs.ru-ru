---
description: Эта функция перечисляет заданный список файлов, предоставляя сведения об изменениях имен для каждого файла с помощью функции обратного вызова.
title: Функция Скккуеричанжес | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e34c37ca999b05e7148d910032fe90c33470ce50
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220525"
---
# <a name="sccquerychanges-function"></a>Функция SccQueryChanges
Эта функция перечисляет заданный список файлов, предоставляя сведения об изменениях имен для каждого файла с помощью функции обратного вызова.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Параметры
 pContext

окне Указатель контекста для подключаемого модуля системы управления версиями.

 Nфайлы оставленные

окне Число файлов в `lpFileNames` массиве.

 лпфиленамес

окне Массив имен файлов для получения сведений о.

 пфнкаллбакк

окне Функция обратного вызова для вызова каждого имени файла в списке (Дополнительные сведения см. в [куеричанжесфунк](../extensibility/querychangesfunc.md) ).

 пвкаллердата

окне Значение, которое будет передано в функцию обратного вызова без изменений.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Процесс запроса успешно завершен.|
|SCC_E_PROJNOTOPEN|Проект не был открыт в системе управления версиями.|
|SCC_E_ACCESSFAILURE|Возникла проблема при доступе к системе управления версиями, возможно, из-за проблем с сетью или состязаниями.|
|SCC_E_NONSPECIFICERROR|Произошла неопределенная или общая ошибка.|

## <a name="remarks"></a>Комментарии
 Запрошенные изменения относятся к пространству имен: в частности, переименование, Добавление и удаление файла.

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Код ошибки](../extensibility/error-codes.md)
