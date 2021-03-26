---
title: КУЕРИЧАНЖЕСФУНК | Документация Майкрософт
description: Функция обратного вызова КУЕРИЧАНЖЕСФУНК используется для перечисления коллекции имен файлов и определения состояния каждого файла.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc797d68f6df6d9aab93554ba95955a7d9f45eea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068626"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Это функция обратного вызова, используемая операцией [скккуеричанжес](../extensibility/sccquerychanges-function.md) для перечисления коллекции имен файлов и определения состояния каждого файла.

 `SccQueryChanges`Функции предоставляется список файлов и указатель на `QUERYCHANGESFUNC` обратный вызов. Подключаемый модуль системы управления версиями перечисляет данные по заданному списку и предоставляет состояние (через этот обратный вызов) для каждого файла в списке.

## <a name="signature"></a>Подпись

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Параметры
 пвкаллердата

окне `pvCallerData` Параметр, передаваемый вызывающей стороной (интегрированной средой разработки) в [скккуеричанжес](../extensibility/sccquerychanges-function.md). Подключаемый модуль системы управления версиями не должен делать никаких предположений о содержимом этого значения.

 пчанжесдата

окне Указатель на структуру [структуры куеричанжесдата](#LinkQUERYCHANGESDATA) , описывающую изменения в файле.

## <a name="return-value"></a>Возвращаемое значение
 Интегрированная среда разработки возвращает соответствующий код ошибки:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Продолжайте обработку.|
|SCC_I_OPERATIONCANCELED|Останавливает обработку.|
|SCC_E_xxx|Любая соответствующая ошибка SCC должна прерывать обработку.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> Структура КУЕРИЧАНЖЕСДАТА
 Структура, передаваемая для каждого файла, выглядит следующим образом:

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 Двсизе размер этой структуры (в байтах).

 Лпфиленаме имя исходного файла для этого элемента.

 Код Двчанжетипе, указывающий состояние файла:

|Код|Описание|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Не удается определить, что изменилось.|
|`SCC_CHANGE_UNCHANGED`|Для этого файла не изменяются имена.|
|`SCC_CHANGE_DIFFERENT`|Файл с другим удостоверением, но в базе данных существует такое же имя.|
|`SCC_CHANGE_NONEXISTENT`|Файл не существует ни в базе данных, ни на локальном компьютере.|
|`SCC_CHANGE_DATABASE_DELETED`|Файл удален в базе данных.|
|`SCC_CHANGE_LOCAL_DELETED`|Файл удален локально, но файл по-прежнему существует в базе данных. Если это невозможно определить, возвращается `SCC_CHANGE_DATABASE_ADDED` .|
|`SCC_CHANGE_DATABASE_ADDED`|Файл добавлен в базу данных, но не существует локально.|
|`SCC_CHANGE_LOCAL_ADDED`|Файл не существует в базе данных и является новым локальным файлом.|
|`SCC_CHANGE_RENAMED_TO`|Файл переименован или перемещен в базе данных как `lpLatestName` .|
|`SCC_CHANGE_RENAMED_FROM`|Файл переименован или перемещен в базу данных из `lpLatestName` ; если это слишком дорого для трассировки, возвращается другой флаг, например `SCC_CHANGE_DATABASE_ADDED` .|

 Лплатестнаме текущее имя файла для этого элемента.

## <a name="see-also"></a>См. также
- [Функции обратного вызова, реализованные интегрированной средой разработки](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Коды ошибок](../extensibility/error-codes.md)
