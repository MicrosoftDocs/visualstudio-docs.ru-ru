---
title: Идиатабле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc7a573eb92d7c51079b0a7e97067abd155ae4fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738714"
---
# <a name="idiatable"></a>IDiaTable
Перечисляет таблицу источника данных DIA.

## <a name="syntax"></a>Синтаксис

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDiaTable`.

|Метод|Описание|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Извлекает версию [интерфейса IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) этого перечислителя.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Возвращает имя таблицы.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Возвращает количество элементов в таблице.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Извлекает ссылку на определенный индекс записи.|

## <a name="remarks"></a>Заметки
Этот интерфейс реализует методы перечисления `IEnumUnknown` в пространстве имен Microsoft. VisualStudio. OLE. Interop. Интерфейс перечисления `IEnumUnknown` гораздо более эффективен для перебора содержимого таблицы по сравнению с методами [идиатабле:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) и [Идиатабле:: Item](../../debugger/debug-interface-access/idiatable-item.md) .

Интерпретация интерфейса `IUnknown`, возвращаемого либо методом `IDiaTable::Item`, либо методом `Next` (в пространстве имен Microsoft. VisualStudio. OLE. Interop) зависит от типа таблицы. Например, если интерфейс `IDiaTable` представляет список внедренных источников, интерфейсу `IUnknown` должен быть запрошен интерфейс [идиаинжектедсаурце](../../debugger/debug-interface-access/idiainjectedsource.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
Получите этот интерфейс, вызвав методы [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) или [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) .

Следующие интерфейсы реализуются с помощью интерфейса `IDiaTable` (то есть можно запрашивать интерфейс `IDiaTable` для одного из следующих интерфейсов):

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>Пример
Первая функция, `ShowTableNames`, отображает имена всех таблиц в сеансе. Вторая функция, `GetTable`, выполняет поиск таблицы, реализующей указанный интерфейс. Третья функция, `UseTable`, показывает, как использовать функцию `GetTable`.

> [!NOTE]
> `CDiaBSTR` — это класс, который заключает `BSTR` и автоматически обрабатывает освобождение строки, когда экземпляр выходит из области действия.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )
            && celt == 1 )
    {
        CDiaBSTR bstrTableName;
        if ( pTable->get_name( &bstrTableName ) != 0 )
        {
            Fatal( "get_name" );
        }
        printf( "Found table: %ws\n", bstrTableName );
    }

// Searches the list of all tables for a table that supports
// the specified interface.  Use this function to obtain an
// enumeration interface.
HRESULT GetTable(IDiaSession* pSession,
                 REFIID       iid,
                 void**       ppUnk)
{
    CComPtr<IDiaEnumTables> pEnumTables;
    HRESULT hResult;

    if (FAILED(pSession->getEnumTables(&pEnumTables)))
        Fatal("getEnumTables");

    CComPtr<IDiaTable> pTable;
    ULONG celt = 0;
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&
           celt == 1)
    {
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)
        {
            return S_OK;
        }
        pTable = NULL;
    }

    if (FAILED(hResult))
        Fatal("EnumTables->Next");

    return E_FAIL;
}

// This function shows how to use the GetTable function.
void UseTable(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pEnumSegments;
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))
    {
        // Do something with pEnumSegments.
    }
}
```

## <a name="requirements"></a>Требования
Заголовок: Dia2. h

Библиотека: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>См. также
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
