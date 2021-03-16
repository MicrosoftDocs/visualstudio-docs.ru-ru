---
title: 'DA0029: неподдерживаемая версия среды CLR | Документация Майкрософт'
description: Предпринята попытка профилирования приложения, в котором используется .NET Framework версии 1.1, не поддерживаемая Средствами профилирования.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3f5e5129bed479273e141af70121d5a344972e2
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465846"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029. Неподдерживаемая версия среды CLR

|Элемент|Значение|
|-|-|
|Идентификатор правила|DA0029|
|Категория|Использование средств профилирования|
|Способ профилирования|Профилирование из командной строки|
|Сообщение|В процессе сбора данных обнаружена неподдерживаемая версия среды CLR. Невозможно надлежащим образом устранить конфликт управляемых символов.|
|Тип правила|Сведения.|

## <a name="cause"></a>Причина:
 Предпринята попытка профилирования приложения, в котором используется платформа [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)], не поддерживаемая Средствами профилирования.

## <a name="rule-description"></a>Описание правила
 Это предупреждение выдается по той причине, что Средствам профилирования не удается разрешить символы в управляемом коде, выполняющемся в приложении. Средства профилирования не могут разрешать символы управляемого кода в приложениях для платформы [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Отсутствует.
