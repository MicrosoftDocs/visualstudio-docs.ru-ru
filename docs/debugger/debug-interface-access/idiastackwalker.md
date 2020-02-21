---
title: Идиастакквалкер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2366c933bf072c295b29d06ff5610bd3735c0077
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741510"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Предоставляет методы для прохода по стеку с использованием сведений в PDB-файле.

## <a name="syntax"></a>Синтаксис

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDiaStackWalker`.

|Метод|Описание|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Извлекает перечислитель кадров стека для платформ x86.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Извлекает перечислитель кадров стека для определенного типа платформы.|

## <a name="remarks"></a>Заметки
Этот интерфейс используется для получения списка кадров стека для загруженного модуля. Каждому методу передается объект [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (реализованный клиентским приложением), который предоставляет необходимую информацию для создания списка кадров стека.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
Этот интерфейс получается путем вызова метода `CoCreateInstance` с идентификатором класса `CLSID_DiaStackWalker` и ИДЕНТИФИКАТОРом интерфейса `IID_IDiaStackWalker`. В примере показано, как получен этот интерфейс.

## <a name="example"></a>Пример
В этом примере показано, как получить интерфейс `IDiaStackWalker`.

```C++

IDiaStackWalker* pStackWalker;
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaStackWalker,
                              (void**) &pStackWalker);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Требования
Заголовок: Dia2. h

Библиотека: диагуидс. lib

DLL: msdia80.dll

## <a name="see-also"></a>См. также
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
