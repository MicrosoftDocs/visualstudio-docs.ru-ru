---
title: IDiaAddressMap | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e06acf045ce1893762d5c898752dd6bc40de50a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744991"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Предоставляет контроль над тем, как пакет SDK DIA рассчитывает виртуальные и относительные виртуальные адреса для объектов отладки.

## <a name="syntax"></a>Синтаксис

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDiaAddressMap`.

|Метод|Описание|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Указывает, была ли установлена схема адресов для конкретного сеанса.|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Указывает, следует ли использовать карту адресов для преобразования адресов символов.|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Указывает, включен ли расчет и использование относительных виртуальных адресов.|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Позволяет клиенту включать или отключать Вычисление относительных виртуальных адресов.|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Извлекает текущее выравнивание изображения.|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Задает выравнивание изображения.|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Задает заголовки изображений, чтобы включить перевод относительных виртуальных адресов.|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Предоставляет карту адресов для поддержки перевода макета изображения.|

## <a name="remarks"></a>Заметки
 Элемент управления, предоставляемый этим интерфейсом, инкапсулируется в два набора данных: заголовки изображений и карты адресов. Большинство клиентов используют метод [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) для поиска правильных отладочных данных для изображения, и метод обычно обнаруживает все необходимые заголовки и сопоставляет данные. Однако некоторые клиенты реализуют специализированную обработку и поиск данных. Такие клиенты используют методы интерфейса `IDiaAddressMap` для предоставления пакета SDK DIA с результатами поиска.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс доступен из объекта сеанса DIA. Клиент вызывает метод `QueryInterface` в интерфейсе объекта сеанса DIA, обычно [IDiaSession](../../debugger/debug-interface-access/idiasession.md), для получения интерфейса `IDiaAddressMap`.

## <a name="requirements"></a>Требования
 Заголовок: Dia2. h

 Библиотека: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>См. также
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)