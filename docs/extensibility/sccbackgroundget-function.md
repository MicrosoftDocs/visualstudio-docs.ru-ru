---
title: Функция Сккбаккграунджет | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6d081389124b8703958f82cb97fc877f9f812290
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952126"
---
# <a name="sccbackgroundget-function"></a>Функция Сккбаккграунджет
Эта функция получает из системы управления версиями каждый из указанных файлов без взаимодействия с пользователем.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Параметры
 pContext

окне Указатель контекста для подключаемого модуля системы управления версиями.

 Nфайлы оставленные

окне Число файлов, указанных в `lpFileNames` массиве.

 лпфиленамес

[вход, выход] Массив имен файлов для извлечения.

> [!NOTE]
> Имена должны быть полными именами локальных файлов.

 dwFlags

окне Флаги команд ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 двбаккграундоператионид

окне Уникальное значение, связанное с этой операцией.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Operation completed successfully (Операция выполнена успешно).|
|SCC_E_BACKGROUNDGETINPROGRESS|Фоновое извлечение уже выполняется (подключаемый модуль системы управления версиями должен возвращать этот параметр только в том случае, если он не поддерживает одновременные пакетные операции).|
|SCC_I_OPERATIONCANCELED|Операция была отменена до ее завершения.|

## <a name="remarks"></a>Remarks
 Эта функция всегда вызывается в потоке, отличном от того, который загрузил подключаемый модуль системы управления версиями. Эта функция не должна возвращаться, пока она не будет создана. Однако его можно вызывать несколько раз с несколькими списками файлов одновременно.

 Использование `dwFlags` аргумента совпадает с параметром [сккжет](../extensibility/sccget-function.md).

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
