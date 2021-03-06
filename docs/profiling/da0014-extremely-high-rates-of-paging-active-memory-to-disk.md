---
title: 'DA0014: исключительно высокая частота подкачки активной памяти на диск | Документация Майкрософт'
description: Данные о производительности системы, собранные в ходе сеанса профилирования, указывают на исключительно высокую частоту подкачки активной памяти на диск и с него во время сеанса профилирования.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3467feff8a947146a5ec407054094a76e09d57fa
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469992"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014. Исключительно высокая скорость подкачки активной памяти на диск

|Элемент|Значение|
|-|-|
|Идентификатор правила|DA0014|
|Категория|Память и подкачка|
|Способ профилирования|Все|
|Сообщение|Сильно повысилась частота постраничного просмотра памяти на диске. Возможно, память вашего приложения ограничена.|
|Тип правила|Предупреждение|

 При профилировании с помощью выборки, памяти .NET или методов разрешения конфликтов ресурсов необходимо собрать минимум 25 выборок, чтобы активировать это правило.

## <a name="cause"></a>Причина:
 Данные о производительности системы, собранные в ходе сеанса профилирования, указывают на исключительно высокую частоту подкачки активной памяти на диск и с него во время сеанса профилирования. Такая высокая частота подкачки обычно влияет на производительность и скорость реагирования приложения. Рекомендуется сократить объем выделяемой памяти, изменив алгоритмы. Кроме того, возможно, потребуется учесть требования приложения к памяти. Запустите профилирование еще раз на компьютере с большим объемом памяти.

## <a name="rule-description"></a>Описание правила
 Чрезмерная частота подкачки на диск может быть вызвана нехваткой физической памяти. Если операции подкачки начинают преобладать на физическом диске, где находится файл подкачки, они могут замедлить другие операции приложений на том же диске.

 Страницы часто считываются с диска или записываются на диск во время выполнения массовых операций подкачки. Например, если значение "Вывод страниц/сек" намного превышает значение "Операций записи страниц/сек". Это связано с тем, что значение "Вывод страниц/сек" также включает измененные страницы данных из кэша файловой системы. Однако не всегда легко определить, какой процесс непосредственно вызывает подкачку и почему.

> [!NOTE]
> Это правило применяется тогда, когда частота подкачки активной памяти достигает очень высокого значения. Когда частота подкачки значительна, но не исключительно высокая, применяется правило информирования [DA0017. Высокая скорость подкачки активной памяти на диск](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Дважды щелкните сообщение в окне "Список ошибок", чтобы перейти к представлению [Метки](../profiling/marks-view.md). Найдите столбец **Память/страниц в секунду**. Определите, есть ли такие этапы выполнения программы, когда число операций ввода-вывода подкачки больше, чем на других этапах.

 При сборе данных профилирования для приложения ASP.NET в сценарии нагрузочного тестирования попробуйте снова выполнить нагрузочный тест на компьютере, оснащенном дополнительным объемом физической памяти (ОЗУ).

 Рекомендуется сократить объем выделяемой памяти, изменив алгоритмы и избегая использования ресурсоемких API, таких как String.Concat и String.Substring.
