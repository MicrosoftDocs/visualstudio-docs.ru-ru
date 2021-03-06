---
title: Визуализация событий EventSource как маркеров | Документы Майкрософт
description: Сведения о том, как визуализатор параллелизма может отображать события EventSource в качестве маркеров и предоставляет возможность настройки того, как должны отображаться эти маркеры.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8c919c72cbf06faccf5bb39b0753533f2b2a441f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890530"
---
# <a name="visualize-eventsource-events-as-markers"></a>Визуализация событий EventSource как маркеров
Визуализатор параллелизма может отображать события EventSource в качестве маркеров и предоставляет возможность настройки того, как должны отображаться эти маркеры. Чтобы просмотреть маркеры EventSource, зарегистрируйте GUID поставщика трассировки событий Windows с помощью диалогового окна [Дополнительные параметры](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md). У визуализатора параллелизма по умолчанию есть соглашения по представлению события EventSource как [маркеров флагов](../profiling/flag-markers.md), [маркеров интервалов](../profiling/span-markers.md) и [маркеров сообщений](../profiling/message-markers.md). Вы можете настраивать то, как отображаются события EventSource, путем добавления пользовательских полей в события. Дополнительные сведения о маркерах см. в разделе [Маркеры визуализатора параллелизма](../profiling/concurrency-visualizer-markers.md). Дополнительные сведения о событиях EventSource см. в разделе <xref:System.Diagnostics.Tracing>.

## <a name="default-visualization-of-eventsource-events"></a>Визуализация событий EventSource по умолчанию
 По умолчанию визуализатор параллелизма использует указанные ниже соглашения по представлению событий EventSource.

### <a name="marker-type"></a>Тип маркера

1. События с [кодом](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) win:Start или win:Stop рассматриваются как начало или конец интервала соответственно.  Вложенные или перекрывающиеся интервалы не могут отображаться. Пары событий, которые начинаются в одном потоке и заканчиваются в другом, также не могут отображаться.

2. Событие, код которого отличен от win:Start и win:Stop, рассматривается как флаг маркера, если оно не имеет [уровень](/windows/desktop/WES/defining-severity-levels) (поле EVENT_RECORD.EVENT_HEADER.EVENT_DESCRIPTOR) win:Verbose или выше.

3. Во всех остальных случаях это событие обрабатывается как сообщение.

### <a name="importance"></a>Важность
 В приведенной ниже таблице определяется способ сопоставления уровня события и важности маркера.

|Уровень трассировки событий Windows|Важность в визуализаторе параллелизма|
|---------------|---------------------------------------|
|win:LogAlways|Норм.|
|win:Critical|Критически важно|
|win:Error|Критически важно|
|win:Warning|Высокий|
|win:Informational|Норм.|
|win:Verbose|Низкий|
|Выше, чем win:verbose|Низкий|

### <a name="series-name"></a>Имя ряда
 Имя задачи события используется для имени ряда. Имя ряда остается пустым, если для данного события не указана задача.

### <a name="category"></a>Category
 Если уровень — win:Critical или win:Error, то категория — Alert (–1). В противном случае категория имеет значение по умолчанию (0).

### <a name="text"></a>Текст
 Если для события определено сообщение форматированного текста (как для функции printf), то оно отображается в качестве описания маркера. В противном случае описанием будет имя события и значение каждого поля полезных данных.

## <a name="customize-visualization-of-eventsource-events"></a>Настройка визуализации событий EventSource
 Вы можете настраивать параметры отображения событий EventSource, добавляя соответствующие поля к событию, как описано в следующих разделах.

### <a name="marker-type"></a>Тип маркера
 Используйте поле `cvType` типа byte для управления типом маркера, который используется для представления события. Ниже приведены доступные значения для cvType.

|Значение cvType|Итоговый тип маркера|
|------------------|---------------------------|
|0|Сообщение|
|1|Начало интервала|
|2|Конец интервала|
|3|Flag|
|Все остальные значения|Сообщение|

### <a name="importance"></a>Важность
 Вы можете использовать поле `cvImportance` типа byte, чтобы управлять параметром важности для события EventSource. Однако рекомендуется управлять представляемой важностью события с помощью его уровня.

|Значение cvImportance|Важность в визуализаторе параллелизма|
|------------------------|---------------------------------------|
|0|Норм.|
|1|Критически важно|
|2|Высокий|
|3|Высокий|
|4|Норм.|
|5|Низкий|
|Все остальные значения|Низкий|

### <a name="series-name"></a>Имя ряда
 Используйте строковое поле события `cvSeries`, чтобы управлять именем ряда, которое визуализатор параллелизма назначает событию EventSource.

### <a name="category"></a>Category
 Используйте поле `cvCategory` типа byte, чтобы управлять категорией, которую визуализатор параллелизма назначает событию EventSource.

### <a name="text"></a>Текст
 Используйте строковое поле `cvTextW`, чтобы управлять описанием, которое визуализатор параллелизма назначает событию EventSource.

### <a name="spanid"></a>SpanID
 Используйте поле cvSpanId типа int, чтобы сопоставлять пары событий. Значение для каждой пары событий start — stop, представляющей интервал, должно быть уникальным. Обычно для параллельного кода это требует использования примитивов синхронизации, таких как <xref:System.Threading.Interlocked.Exchange%2A>, для обеспечения правильности ключа (значения, которое используется для CvSpanID).

> [!NOTE]
> Не поддерживается использование SpanID для вложения интервалов, их частичного перекрытия в одном потоке, а также обеспечения ситуации, когда интервал начинается в одном потоке, а завершается в другом.

## <a name="see-also"></a>См. также
- [Маркеры визуализатора параллелизма](../profiling/concurrency-visualizer-markers.md)