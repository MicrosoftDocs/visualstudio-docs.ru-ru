---
title: Граф использования ЦП | Документы Майкрософт
description: Сведения о графе использования ЦП, который показывает уровень использования приложения с течением времени. Данные отображаются в виде количества используемых логических ядер.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5ec57ac6601557bf644c818822fea70a296fd0c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956013"
---
# <a name="cpu-utilization-graph"></a>Граф использования ЦП
На графе использования ЦП показывает уровень использования приложения с течением времени. Ось Х представляет время работы трассировки, а ось Y — количество логических ядер в системе. Этот граф не показывает, какое из ядер активно в заданный момент времени. Например, если два ядра были загружены на 50 процентов производительности в течение заданного периода времени, представление показывает, что использовалось одно логическое ядро.

## <a name="cpu-utilization-graph-colors"></a>Цвета графа использования ЦП

- Зеленый цвет означает использование логических ядер в системе текущим процессом.

- Светло-серый цвет обозначает использование логических ядер другими процессами в системе. Высокий процент светло-серого цвета на графе ЦП указывает, что система сильно загружена другими процессами и данный процесс, вероятно, был прерван ими. Чтобы уменьшить потребление логических ядер другими процессами, уменьшите количество таких работающих процессов в системе.

- Темно-серый цвет обозначает потребление логических ядер системным процессом. Этим процессом невозможно управлять непосредственно, но полезно знать, когда он выполняется, так как он может повлиять на доступность логических ядер для данного процесса.

- Белый цвет обозначает доступность неиспользуемых логических ядер в системе. Эти ядра доступны для данного процесса, если можно найти дополнительные возможности для параллелизма.

## <a name="see-also"></a>См. также
- [Представление использования](../profiling/utilization-view.md)
- [Среднее использование ЦП](../profiling/average-cpu-utilization.md)