---
description: При наличии списка локальных файлов Эта функция определяет, какие файлы отличаются от соответствующих версий в базе данных управления исходным кодом.
title: Функция Скценумчанжедфилес | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 10f14fb915d461255eddbd4a00747dfbdf59cde4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085563"
---
# <a name="sccenumchangedfiles-function"></a>Функция Скценумчанжедфилес
При наличии списка локальных файлов Эта функция определяет, какие файлы отличаются от соответствующих версий в базе данных управления исходным кодом.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>Параметры
 pContext

окне Указатель контекста для подключаемого модуля системы управления версиями.

 hWnd

окне Обработчик окна интегрированной среды разработки, который может использоваться подключаемым модулем системы управления версиями в качестве родительского для любых предоставляемых им диалоговых окон.

 кфилес

окне Число имен файлов, указанное в `lpFileNames` массиве. Также указывает размер `plIsFileDifferent` массива.

 лпфиленамес

окне Массив имен локальных файлов для проверки.

 плисфиледифферент

[вход, выход] Массив значений, указывающий состояние различий для каждого файла (массив должен содержать по крайней мере `cFiles` записи). Ненулевое значение означает, что файл отличается.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Operation completed successfully (Операция выполнена успешно).|
|SCC_UNSPECIFIEDERROR|Общая ошибка.|

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
