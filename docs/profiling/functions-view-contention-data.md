---
title: Представление "Функции" — данные о конфликтах | Документы Майкрософт
description: Сведения о представлении отчета "Функции" данных о конфликтах, в котором перечислены функции сеанса профилирования, выполнение которых было заблокировано.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6392263e7e30790ff09340bffebed8f921e24765
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907414"
---
# <a name="functions-view---contention-data"></a>Представление "Функции" — данные о конфликтах
В представлении отчета "Функции" данных о конфликтах перечислены функции сеанса профилирования, выполнение которых было заблокировано.

 В таблице ниже приведено объяснение значений в представлении "Функции" файла данных профилирования, которые были получены с помощью метода параллелизма.

|Столбец|Описание|
|------------|-----------------|
|**Эксклюзивное время блокировки**|Время блокировки выполнения функцией кода в теле функции. Время блокирования в функциях, которые были вызваны данной функцией, не включается.|
|**% эксклюзивного времени блокировки**|Процент общего времени блокировки в ходе сеанса профилирования, которое являлось эксклюзивным временем блокировки указанной функции.|
|**Эксклюзивные конфликты**|Количество блокировок выполнения функцией кода в теле функции. Конфликты в функциях, которые были вызваны данной функцией, не включаются.|
|**% эксклюзивных конфликтов**|Процент всех конфликтов в ходе сеанса профилирования, являющихся эксклюзивными конфликтами этой функции.|
|**Адрес функции**|Адрес функции.|
|**Имя функции**|Полное имя функции.|
|**Включая время блокировки**|Время блокировки выполнения этой функции или вызванной ею функции.|
|**Включая % времени блокирования**|Процент общего времени блокировки в ходе сеанса профилирования, которое являлось инклюзивным временем блокировки указанной функции или модуля.|
|**Включая состязания**|Количество блокировок выполнения этой функции или вызванной ею функции.|
|**Включая % состязаний**|Процент общего времени блокировки в ходе сеанса профилирования, которое являлось инклюзивным временем блокировки указанной функции или модуля.|
|**Номер строки функции**|Номер строки, на которой эта функция начинается в исходном файле.|
|**Имя модуля**|Имя модуля, содержащего функцию.|
|**Путь к модулю**|Путь к модулю, содержащему функцию.|
|**Идентификатор процесса**|Идентификатор процесса, в котором выполнялась функция.|
|**Имя процесса**|Имя процесса.|
|**Исходный файл**|Исходный файл, содержащий определение данной функции.|

## <a name="see-also"></a>См. также
- [Практическое руководство. Настройка столбцов представлений отчета](../profiling/how-to-customize-report-view-columns.md)
- [Представление "Функции"](../profiling/functions-view.md)
- [Представление "Функции" — инструментирование](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Представление "Функции" — выборка](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Представление "Функции"](../profiling/functions-view-instrumentation-data.md)
- [Представление "Функции"](../profiling/functions-view-sampling-data.md)
