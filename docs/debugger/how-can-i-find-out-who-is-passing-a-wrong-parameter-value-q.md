---
title: Как определить, откуда передается неправильное значение параметра? | Документация Майкрософт
description: Вы можете узнать, какой код вызывает функцию и передает неправильное значение параметра, с помощью условной точки останова.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b2f747e2f92b7817530fe12e14f8f95a9bfbe791
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386921"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Как определить, откуда передается неправильное значение параметра?
## <a name="problem-description"></a>Описание проблемы
 Одной из функций передается неправильное значение параметра. Эта функция вызывается по всей программе. Как определить, откуда передается неправильное значение?

## <a name="solution"></a>Решение

#### <a name="to-resolve-this-problem"></a>Устранение неполадки

1. Установите точку останова в начале функции.

2. Щелкните правой кнопкой мыши точку останова и выберите пункт **Условие**.

3. В диалоговом окне **Условие для точек останова** установите флажок **Условие**. См. раздел [Расширенные точки останова](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

4. Введите в текстовое поле выражение, например `Var==3`, где `Var` представляет собой имя параметра, который содержит неправильное значение, а `3` — это неправильное значение, переданное параметру.

5. Установите переключатель в положение **верно** и нажмите кнопку **ОК**.

6. Запустите программу повторно. Точка останова заставит программу прервать выполнение на начале функции, когда параметр `Var` получит значение `3`.

7. Затем в окне "Стек вызовов" можно найти вызывающую функцию, чтобы перейти к ее исходному коду. Дополнительные сведения см. в разделе [Практическое руководство. использовать окно "Стек вызовов"](../debugger/how-to-use-the-call-stack-window.md).

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Точки останова](/previous-versions/ktf38f66(v=vs.100))
- [Отладка машинного кода](../debugger/debugging-native-code.md)
