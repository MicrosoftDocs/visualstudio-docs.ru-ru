---
description: Эта функция определяет, поддерживает ли подключаемый модуль системы управления версиями создание МССККПРЖ. Файл SCC для каждого из заданных файлов.
title: Функция Скквиллкреатесккфиле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 00988afe980a29a7176c8632d95514813efaad37
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063725"
---
# <a name="sccwillcreatesccfile-function"></a>Функция SccWillCreateSccFile
Эта функция определяет, поддерживает ли подключаемый модуль системы управления версиями создание МССККПРЖ. Файл SCC для каждого из заданных файлов.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>Параметры
 pContext

окне Указатель контекста для подключаемого модуля системы управления версиями.

 Nфайлы оставленные

окне Количество имен файлов, содержащихся в `lpFileNames` массиве, а также длина `pbSccFiles` массива.

 лпфиленамес

окне Массив полных имен файлов для проверки (массив должен быть выделен вызывающим объектом).

 пбсккфилес

[вход, выход] Массив, в котором сохраняются результаты.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Успешно.|
|SCC_E_INVALIDFILEPATH|Один из путей в массиве является недопустимым.|
|SCC_E_NONSPECIFICERROR|Неконкретный сбой.|

## <a name="remarks"></a>Remarks
 Эта функция вызывается со списком файлов, чтобы определить, обеспечивает ли подключаемый модуль системы управления версиями поддержку в МССККПРЖ. Файл SCC для каждого из заданных файлов (Дополнительные сведения о МССККПРЖ. Файле SCC см. в разделе [мссккпрж. Файл SCC](../extensibility/mssccprj-scc-file.md)). Подключаемые модули системы управления версиями могут объявлять, имеют ли они возможность создания МССККПРЖ. Файлы SCC путем объявления `SCC_CAP_SCCFILE` во время инициализации. Подключаемый модуль возвращает `TRUE` или `FALSE` для каждого файла в `pbSccFiles` массиве, чтобы указать, какие из заданных файлов имеют мссккпрж. Поддержка SCC. Если подключаемый модуль возвращает код успешного выполнения из функции, учитываются значения в возвращаемом массиве. В случае сбоя массив пропускается.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Файл MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
