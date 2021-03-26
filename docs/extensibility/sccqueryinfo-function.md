---
description: Эта функция получает сведения о состоянии для набора выбранных файлов в системе управления версиями.
title: Функция Скккуеринфо | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 911219605859025f1877d040b5932714b10f836a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073902"
---
# <a name="sccqueryinfo-function"></a>Функция SccQueryInfo
Эта функция получает сведения о состоянии для набора выбранных файлов в системе управления версиями.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Параметры
 пвконтекст

окне Структура контекста подключаемого модуля системы управления версиями.

 Nфайлы оставленные

окне Число файлов, указанных в `lpFileNames` массиве, и длина `lpStatus` массива.

 лпфиленамес

окне Массив имен файлов для запроса.

 лпстатус

[вход, выход] Массив, в котором подключаемый модуль системы управления версиями возвращает флаги состояния для каждого файла. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Запрос выполнен успешно.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблем с сетью или состязаниями. Рекомендуется повторить попытку.|
|SCC_E_PROJNOTOPEN|Проект не открыт в системе управления версиями.|
|SCC_E_NONSPECIFICERROR|Неконкретный сбой.|

## <a name="remarks"></a>Remarks
 Если `lpFileName` является пустой строкой, в настоящее время нет сведений о состоянии для обновления. В противном случае это полный путь к файлу, сведения о состоянии которого могли измениться.

 Возвращаемый массив может быть битовой маской `SCC_STATUS_xxxx` битов. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md). Система управления версиями может не поддерживать все типы битов. Например, если `SCC_STATUS_OUTOFDATE` не предложено, бит просто не задан.

 При использовании этой функции для извлечения файлов Обратите внимание на следующие `MSSCCI` требования к состоянию:

- `SCC_STATUS_OUTBYUSER` задается, когда текущий пользователь извлекает файл.

- `SCC_STATUS_CHECKEDOUT` не может быть задан `SCC_STATUS_OUTBYUSER` , если не задан параметр.

- `SCC_STATUS_CHECKEDOUT` задается только при извлечении файла в назначенный рабочий каталог.

- Если файл извлечен текущим пользователем в каталог, отличный от рабочего каталога, то задается, но не `SCC_STATUS_OUTBYUSER` `SCC_STATUS_CHECKEDOUT` является.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Код состояния файла](../extensibility/file-status-code-enumerator.md)
