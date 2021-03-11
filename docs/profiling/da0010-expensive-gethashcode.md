---
title: 'DA0010: затратный метод GetHashCode | Документация Майкрософт'
description: Вызовы метода GetHashCode типа составляют значительную часть данных профилирования, или метод выделяет память.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5d44c998cabd3611e2ed393be0ad7df20e1ac49c
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469928"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010. Затратный метод GetHashCode

|Элемент|Значение|
|-|-|
|Идентификатор правила|DA0010|
|Категория|Использование .NET Framework|
|Методы профилирования|Дискретизация<br /><br /> Память .NET|
|Сообщение|Функции GetHashCode должны быть малозатратными и не должны выделять память. Если возможно, уменьшите сложность функции хэш-кода.|
|Тип сообщения|Предупреждение|

## <a name="cause"></a>Причина:
 Вызовы метода GetHashCode типа составляют значительную часть данных профилирования, или метод выделяет память.

## <a name="rule-description"></a>Описание правила
 Хэширование — это метод для быстрого нахождения определенного элемента в большой коллекции. Так как хэш-таблицы могут быть большими и должны поддерживать очень высокую интенсивность доступа, они должны быть эффективными. Это требование подразумевает, что методы GetHashCode в .NET Framework не должны выделять память. Выделение памяти увеличивает нагрузку на сборщик мусора и повышает вероятность задержек метода, если станет необходимо выполнить сборку мусора в результате выполнения запроса на выделение памяти.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Упростите метод.
