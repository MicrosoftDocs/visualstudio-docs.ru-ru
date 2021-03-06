---
title: Представление "Функции" — данные выборки памяти .NET | Документы Майкрософт
description: Сведения о представлении "Функции" данных профилирования выделения памяти .NET, собранных с помощью метода выборки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 2c0bfd4c3355e6e4371fbec443ee38d7ba6e1da7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907326"
---
# <a name="functions-view---net-memory-sampling-data"></a>Представление "Функции" — данные выборки памяти .NET
В представлении "Функции" данных профилирования выделения памяти .NET, собранных с помощью методов выборки, представлены функции, выделявшие память в процессе профилирования, а также указан размер и количество выделенных блоков.

|Столбец|Описание|
|------------|-----------------|
|**Идентификатор процесса**|Идентификатор процесса (PID) сеанса профилирования.|
|**Имя процесса**|Имя процесса.|
|**Имя модуля**|Имя модуля, содержащего функцию.|
|**Путь к модулю**|Путь к модулю, содержащему функцию.|
|**Исходный файл**|Исходный файл, содержащий определение данной функции.|
|**Имя функции**|Полное имя функции.|
|**Номер строки функции**|Номер строки, на которой эта функция начинается в исходном файле.|
|**Адрес функции**|Адрес функции.|
|**Инклюзивные выделения**|Общее число объектов, выделенных в данной функции и ее дочерних функциях.|
|**Включающие выделения %**|Процент от общего числа объектов, выделенных при выполнении профилирования, в ходе которого осуществлялись инклюзивные выделения для данной функции.|
|**Исключающие выделения**|Количество объектов, которые были созданы, когда функция выполнялась непосредственно наверху стека вызовов. Это число не включает объекты, созданные в дочерних функциях.|
|**% эксклюзивных выделений**|Процент от общего числа объектов, выделенных в ходе сеанса профилирования, при котором выполнялись эксклюзивные выделения для данной функции.|
|**Включающие байты**|Число байтов памяти, которые были выделены данной функцией и ее дочерними функциями.|
|**% инклюзивных байтов**|Процент от общего числа байтов памяти, выделенных при профилировании, которые являются инклюзивными байтами для данной функции.|
|**Исключающие байты**|Число байтов памяти, которые были выделены данной функцией, но не ее дочерними функциями.|
|**Исключающие байты %**|Процент от общего числа байтов памяти, выделенных при профилировании, которые являются эксклюзивными байтами для данной функции.|

## <a name="see-also"></a>См. также
- [Представление "Функции" — инструментирование](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Представление "Функции"](../profiling/functions-view-sampling-data.md)
- [Представление "Функции"](../profiling/functions-view-instrumentation-data.md)
