---
title: Начало работы (SDK для доступа к интерфейсу отладки) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dd6a98f377ba295d6a866c9db95671de4ff16ea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745108"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Начало работы (SDK для доступа к интерфейсу отладки)
Пакет SDK для доступа к интерфейсу отладки (DIA) содержит документацию с инструкциями и пример, демонстрирующий использование API DIA. Используйте интерфейсы и методы в пакете SDK DIA для разработки пользовательских приложений, открывающих файлы PDB и DBG, и поиска в содержимом символов, значений, атрибутов, адресов и других отладочных данных. Этот пакет SDK также содержит справочные таблицы по свойствам, связанным C++ с символами, найденными в приложениях.

 Для лучшего использования пакета SDK для DIA необходимо ознакомиться со следующими разрешениями:

- C++язык программирования

- Программирование COM

- Интегрированная среда разработки (IDE) Visual Studio для компиляции образцов

  Пакет SDK DIA обычно устанавливается вместе с Visual Studio, и его расположение по умолчанию — *[диск]* \Program Files\Microsoft Visual Studio 9.0 \ DIA SDK. В рамках установки библиотека msdia90. dll, которая реализует пакет SDK для DIA, автоматически регистрируется, поэтому все, что необходимо для его использования, — включить в программу `dia2.h` и привязать к `diaguids.lib`.

  Заголовок: include\dia2.h

  Библиотека: lib\diaguids.lib

  DLL: bin\msdia80.dll

  IDL: idl\dia2.idl

## <a name="in-this-section"></a>Содержание

[Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

Проверяет базовую архитектуру DIA.

[Запрос PDB-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Содержит пошаговые инструкции по использованию API DIA для запроса PDB-файла.

## <a name="see-also"></a>См. также

- [SDK для доступа к интерфейсу отладки](../../debugger/debug-interface-access/debug-interface-access-sdk.md)