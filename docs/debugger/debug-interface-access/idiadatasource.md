---
title: Идиадатасаурце | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 453be1d77f1d2b1759e3de4433225cf97d026054
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744905"
---
# <a name="idiadatasource"></a>IDiaDataSource
Инициирует доступ к источнику отладочных символов.

## <a name="syntax"></a>Синтаксис

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDiaDataSource`.

|Метод|Описание|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Возвращает имя файла для последней ошибки загрузки.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Открывает и готовит файл базы данных программы (PDB) в качестве источника данных отладки.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Открывает и проверяет, совпадает ли файл базы данных программы (PDB) с предоставленными сведениями о сигнатуре. подготавливает pdb-файл в качестве источника данных отладки.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Открывает и готовит данные отладки, связанные с файлом EXE/. dll.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Подготавливает данные отладки, хранящиеся в файле базы данных программы (. pdb), к которому осуществляется доступ через поток данных в памяти.|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Открывает сеанс для запроса символов.|

## <a name="remarks"></a>Заметки
Вызов одного из методов Load интерфейса `IDiaDataSource` открывает источник символов. Успешный вызов метода [идиадатасаурце:: опенсессион](../../debugger/debug-interface-access/idiadatasource-opensession.md) возвращает интерфейс [IDiaSession](../../debugger/debug-interface-access/idiasession.md) , который поддерживает запросы к источнику данных. Если метод Load возвращает ошибку, связанную с файлом, то возвращаемое значение метода [идиадатасаурце:: get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) содержит имя файла, связанного с ошибкой.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
Этот интерфейс получается путем вызова функции `CoCreateInstance` с идентификатором класса `CLSID_DiaSource` и ИДЕНТИФИКАТОРом интерфейса `IID_IDiaDataSource`. В примере показано, как получен этот интерфейс.

## <a name="example"></a>Пример

```C++

      IDiaDataSource* pSource;
HRESULT hr = CoCreateInstance(CLSID_DiaSource,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaDataSource,
                              (void**) &pSource);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Требования
Заголовок: Dia2. h

Библиотека: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>См. также
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
