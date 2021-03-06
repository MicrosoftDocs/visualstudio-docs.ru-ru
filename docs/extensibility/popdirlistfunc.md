---
title: ПОПДИРЛИСТФУНК | Документация Майкрософт
description: Сведения о функции обратного вызова ПОПДИРЛИСТФУНК, которая передается в каталоги обновления для выяснения того, что находится под управлением системы управления версиями.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c98b35d9f915e16072333c72df2e1e045850f5d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900399"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Это функция обратного вызова, предоставляемая функции [сккпопулатедирлист](../extensibility/sccpopulatedirlist-function.md) для обновления коллекции каталогов и (необязательно) имен файлов, которые следует найти в системе управления версиями.

 `POPDIRLISTFUNC`Обратный вызов должен вызываться только для тех каталогов и имен файлов (в списке, заданном для `SccPopulateDirList` функции), которые фактически находятся в системе управления версиями.

## <a name="signature"></a>Подпись

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Параметры
 пвкаллердата

окне Значение пользователя, заданное в [сккпопулатедирлист](../extensibility/sccpopulatedirlist-function.md).

 бфолдер

[входные] `TRUE` значение, если имя в `lpDirectoryOrFileName` папке является каталогом; в противном случае — имя файла.

 лпдиректорйорфиленаме

окне Полный локальный путь к каталогу или имени файла в системе управления исходным кодом.

## <a name="return-value"></a>Возвращаемое значение
 Интегрированная среда разработки возвращает соответствующий код ошибки:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Продолжайте обработку.|
|SCC_I_OPERATIONCANCELED|Останавливает обработку.|
|SCC_E_xxx|Любая соответствующая ошибка системы управления версиями должна прерывать обработку.|

## <a name="remarks"></a>Remarks
 Если `fOptions` параметр `SccPopulateDirList` функции содержит `SCC_PDL_INCLUDEFILES` флаг, то список может содержать имена файлов, а также имена каталогов.

## <a name="see-also"></a>См. также
- [Функции обратного вызова, реализованные интегрированной средой разработки](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Коды ошибок](../extensibility/error-codes.md)
