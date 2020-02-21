---
title: Идиастакквалкхелпер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40c2b58778b2a1073b31acc7007388d8e8fe222c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741307"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Облегчает проход по стеку с помощью файла базы данных отладки (PDB) программы.

## <a name="syntax"></a>Синтаксис

```

IDiaStackWalkHelper: IUnknown

```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В таблице ниже показаны методы `IDiaStackWalkHelper`.

|Метод|Описание|
|------------|-----------------|
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Возвращает значение регистра.|
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Задает значение регистра.|
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Считывает блок данных из образа исполняемого файла в памяти.|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Выполняет поиск по указанному кадру стека для ближайшего адреса возврата функции.|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Ищет в указанном кадре стека обратный адрес по указанному адресу стека или рядом с ним.|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Извлекает кадр стека, который содержит указанный виртуальный адрес.|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Извлекает символ, который содержит указанный виртуальный адрес. **Примечание.**  Символ должен иметь тип `SymTagFunctionType` (значение из перечисления [перечисления симтаженум](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Возвращает блок данных PDATA, связанный с указанным виртуальным адресом.|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Извлекает начальный виртуальный адрес исполняемого файла по заданному виртуальному адресу в пространстве памяти исполняемого файла.|

## <a name="remarks"></a>Заметки
 Этот интерфейс вызывается кодом DIA для получения сведений о исполняемом файле для создания списка кадров стека во время выполнения программы.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Клиентское приложение реализует этот интерфейс для поддержки прохода стека во время выполнения программы. Экземпляр этого интерфейса передается методам [идиастакквалкер:: жетенумфрамес](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) или [Идиастакквалкер:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .

## <a name="requirements"></a>Требования
 Заголовок: Dia2. h

 Библиотека: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>См. также
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)