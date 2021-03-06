---
title: Представление "Процесс" | Документация Майкрософт
description: Сведения о том, как в представлении процесса отображаются данные о профилировании для процессов и потоков, которые выполнялись во время сеанса профилирования.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bc1f30fa815030204b5f2d306151fe815ed819f8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910704"
---
# <a name="process-view"></a>Представление "Процесс"
В представлении процесса отображаются данные о профилировании для процессов и потоков, которые выполнялись во время сеанса профилирования.

 Процессы упорядочены по имени. Потоки указываются как дочерние узлы создавших их процессов. Потоки именуются по запустивших их функциям или по метке **[ntdll.dll]** при отсутствии доступных символов.

 Чтобы добавить или удалить столбцы, щелкните правой кнопкой мыши в представлении и выберите **Добавить или удалить столбцы**. Кроме того, щелкнув имя столбца, можно сортировать данные. Дополнительные сведения см. в разделе [Практическое руководство. Настройка столбцов представлений отчета](../profiling/how-to-customize-report-view-columns.md).

 Столбцы в представлении процесса являются одинаковыми для данных, которые созданы с помощью методов выборки и инструментирования, а также для данных, которые включают данные памяти .NET. В следующей таблице описаны значения столбцов.

|Столбец|Описание|
|------------|-----------------|
|**Уникальный идентификатор**|Созданный профилировщиком идентификатор, уникальным образом определяющий процесс или поток.|
|**ID**|Созданный системой идентификатор процесса или потока.|
|**Имя**|Имя процесса или потока.|
|**Время начала**|Количество миллисекунд или циклов процессора от начала профилирования до запуска процесса или потока.|
|**Время окончания**|Количество миллисекунд или циклов процессора от начала профилирования до завершения процесса или потока.|

## <a name="see-also"></a>См. также
- [Представления данных метода выборки](../profiling/profiler-sampling-method-data-views.md)
- [Представления данных метода инструментирования](../profiling/instrumentation-method-data-views.md)
- [Представления данных в памяти .NET](../profiling/dotnet-memory-data-views.md)
