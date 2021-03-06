---
title: Представление "Модули" — данные инструментирования | Документы Майкрософт
description: Сведения о том, что в представлении "Модули" отображаются данные производительности, сгруппированные по модулям, выбранным в данных профилирования.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 031068d159b7004b7cfe7fcf1c747c2eb582afc8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879778"
---
# <a name="modules-view---instrumentation-data"></a>Представление "Модули" — данные инструментирования
В представлении "Модули" отображаются данные производительности, сгруппированные по модулям, выбранным в данных профилирования. Функции модуля указываются в узле модуля.

## <a name="general"></a>Общие сведения
 Столбцы общего назначения позволяют определить функцию в строке представления.

|Столбец|Описание|
|------------|-----------------|
|**Имя**|Имя функции или модуля.|
|**Номер строки функции**|Номер строки, на которой эта функция начинается в исходном файле.|
|**Число вызовов**|Общее количество вызовов этой функции или модуля.|
|**Исходный файл**|Исходный файл, содержащий определение данной функции.|
|**Имя модуля**|Имя модуля, содержащего функцию.|
|**Путь к модулю**|Путь к модулю, содержащему функцию.|
|**Идентификатор процесса**|Идентификатор процесса (PID) сеанса профилирования.|
|**Имя процесса**|Имя процесса, в котором выполнялась функция или модуль.|
|**Эксклюзивные временные издержки на зонды**|Дополнительные временные затраты для этой функции или модуля, вызванные инструментированием.|
|**Инклюзивные временные издержки на зонды**|Дополнительные временные затраты для этой функции или модуля и их дочерних функций, вызванные инструментированием.|

## <a name="elapsed-inclusive-values"></a>Значения затраченного инклюзивного времени
 Значения затраченного инклюзивного времени указывают время, в течение которого функция находилась в стеке вызовов. В значении учтено время, которое было затрачено на выполнение дочерних функций и системных операций, например переключение контекста и операции ввода-вывода.

|Столбец|Описание|
|------------|-----------------|
|**Затраченное инклюзивное время**|— Для функции — время, которое было затрачено на выполнение функции. В значении учтено время, которое было затрачено на выполнение дочерних функций и на вызовы операционной системы, например переключение контекста и операции ввода-вывода.<br />— Для модуля — период времени, в течение которого хотя бы одна функция модуля находилась в стеке вызовов.|
|**% затраченного инклюзивного времени**|Процент общего затраченного инклюзивного времени сеанса профилирования, затраченный в общем инклюзивном времени этого модуля или функции.|
|**Среднее затраченное инклюзивное время**|— Для функции — среднее затраченное инклюзивное время для вызова данной функции.<br />— Для модуля — среднее затраченное инклюзивное время всех вызовов функций в модуле.|
|**Максимальное затраченное инклюзивное время**|— Для функции — максимальное затраченное инклюзивное время для вызова данной функции.<br />— Для модуля — максимальное затраченное инклюзивное время всех вызовов функций в модуле.|
|**Минимальное затраченное инклюзивное время**|— Для функции — минимальное затраченное инклюзивное время для вызова данной функции.<br />— Для модуля — минимальное затраченное инклюзивное время всех вызовов функций в модуле.|

## <a name="elapsed-exclusive-values"></a>Значения затраченного эксклюзивного времени
 Значения затраченного эксклюзивного времени соответствуют времени выполнения функции непосредственно вверху стека вызовов. В значении учтено время, которое было затрачено на выполнение вызовов системных операций, например переключение контекста и операции ввода-вывода, но не учтено время, которое было затрачено на выполнение дочерних функций.

|Столбец|Описание|
|------------|-----------------|
|**Затраченное эксклюзивное время**|— Для функции — время, которое было затрачено на выполнение модуля или функции. В значении учтено время, которое было затрачено на вызовы системных операций, например переключение контекста и операции ввода-вывода, но не входит время, которое было затрачено на выполнение дочерних функций.<br />— Для модуля — сумма затраченного эксклюзивного времени функций в модуле.|
|**% затраченного эксклюзивного времени**|Процент общего затраченного эксклюзивного времени сеанса профилирования, затраченный в общем эксклюзивном времени этого модуля или функции.|
|**Среднее затраченное эксклюзивное время**|— Для функции — среднее затраченное эксклюзивное время для вызова данной функции.<br />— Для модуля — среднее затраченное эксклюзивное время всех вызовов функций в модуле.|
|**Максимальное затраченное эксклюзивное время**|— Для функции — максимальное затраченное эксклюзивное время для вызова данной функции.<br />— Для модуля — максимальное затраченное эксклюзивное время всех вызовов функций в модуле.|
|**Минимальное затраченное эксклюзивное время**|— Для функции — минимальное затраченное эксклюзивное время для вызова данной функции.<br />— Для модуля — минимальное затраченное эксклюзивное время всех вызовов функций в модуле.|

## <a name="application-inclusive-values"></a>Значения инклюзивного времени приложения
 Значения инклюзивного времени указывают время, в течение которого функция находилась в стеке вызовов. В значении не учтено время, которое было затрачено на выполнение вызовов системных операций, например переключение контекста и операции ввода-вывода, но учтено время, которое было затрачено на выполнение дочерних функций.

|Столбец|Описание|
|------------|-----------------|
|**Инклюзивное время приложения**|— Для функции — время, которое было затрачено на вызовы функции. В значении учтено время, затраченное на выполнение дочерних функций, но не учтены вызовы операционной системы, например переключение контекста и операции ввода-вывода.<br />— Для модуля — период времени, в течение которого хотя бы одна функция модуля находилась в стеке вызовов. При этом исключается время, затраченное на вызовы для операционной системы.|
|**% инклюзивного времени приложения**|Процент общего затраченного инклюзивного времени сеанса профилирования, затраченный в инклюзивном времени приложения этого модуля или функции.|
|**Среднее инклюзивное время приложения**|— Для функции — среднее инклюзивное время приложения для вызова данной функции.<br />— Для модуля — среднее инклюзивное время приложения для всех вызовов функций в модуле.|
|**Максимальное инклюзивное время приложения**|— Для функции — максимальное инклюзивное время приложения для вызова данной функции.<br />— Для модуля — максимальное инклюзивное время приложения для всех вызовов функций в модуле.|
|**Минимальное инклюзивное время приложения**|— Для функции — минимальное инклюзивное время приложения для вызова данной функции.<br />— Для модуля — минимальное инклюзивное время приложения для всех вызовов функций в модуле.|

## <a name="application-exclusive-values"></a>Значения эксклюзивного времени приложения
 Значения эксклюзивного времени приложения указывают время, затраченное на выполнение модуля или функции. В значении не учтено время, которое было затрачено на выполнение дочерних функций, а также не учтены вызовы операционной системы, например переключения контекста и операции ввода-вывода.

|Столбец|Описание|
|------------|-----------------|
|**Эксклюзивное время приложения**|Общее эксклюзивное время приложения для всех вызовов данного модуля или функции.|
|**% эксклюзивного времени приложения**|Процент общего затраченного эксклюзивного времени сеанса профилирования, затраченный в эксклюзивном времени приложения этого модуля или функции.|
|**Среднее эксклюзивное время приложения**|— Для функции — среднее эксклюзивное время приложения для вызова данной функции.<br />— Для модуля — среднее эксклюзивное время приложения для всех вызовов функций в модуле.|
|**Максимальное эксклюзивное время приложения**|— Для функции — максимальное эксклюзивное время приложения для вызова данной функции.<br />— Для модуля — максимальное эксклюзивное время приложения для всех вызовов функций в модуле.|
|**Минимальное эксклюзивное время приложения**|— Для функции — минимальное эксклюзивное время приложения для вызова данной функции.<br />— Для модуля — минимальное эксклюзивное время приложения для всех вызовов функций в модуле.|

## <a name="see-also"></a>См. также
- [Представление "Модули"](../profiling/modules-view-sampling-data.md)
- [Представление "Модули" — инструментирование](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Представление "Модули" — выборка](../profiling/modules-view-dotnet-memory-sampling-data.md)
