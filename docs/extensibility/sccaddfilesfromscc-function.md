---
description: Эта функция добавляет список файлов из системы управления версиями в текущий открытый проект.
title: Функция Сккаддфилесфромскк | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fa08ec93383fa661d1e2dd055b3139b2ba90f34
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904868"
---
# <a name="sccaddfilesfromscc-function"></a>Функция Сккаддфилесфромскк
Эта функция добавляет список файлов из системы управления версиями в текущий открытый проект.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>Параметры
 pContext

окне Указатель контекста для подключаемого модуля системы управления версиями.

 hWnd

окне Обработчик окна интегрированной среды разработки, который может использоваться подключаемым модулем системы управления версиями в качестве родительского для любых предоставляемых им диалоговых окон.

 лпусер

[вход, выход] Имя пользователя (до SCC_USER_SIZE, включая знак завершения null).

 лпаукспрожпас

[вход, выход] Вспомогательная строка, идентифицирующая проект (до `SCC_PRJPATH_` размера, включая знак завершения null).

 кфилес

окне Число файлов, заданное параметром `lpFilePaths` .

 лпфилепасс

[вход, выход] Массив имен файлов, добавляемых в текущий проект.

 лпдестинатион

окне Конечный путь, по которому должны быть записаны файлы.

 лпкоммент

окне Комментарий, применяемый к каждому добавляемому из файлов.

 пбресултс

[вход, выход] Массив флагов, для которых задано значение "успех" (ноль или TRUE) или сбой (нуль или FALSE) для каждого файла (размер массива должен быть не менее `cFiles` длительного).

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Проект не открыт.|
|SCC_E_OPNOTPERFORMED|Соединение не относится к тому же проекту, что указано в `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Пользователь не имеет права на обновление базы данных.|
|SCC_E_NONSPECIFICERROR|Неизвестная ошибка.|
|SCC_I_RELOADFILE|Необходимо перезагрузить файл или проект.|

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
