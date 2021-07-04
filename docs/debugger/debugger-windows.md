---
title: Проверка данных с помощью окон отладчика | Документация Майкрософт
description: Отладчик выводит информацию с использованием различных окон. В этой статье описываются существующие типы окон. Воспользовавшись представленными ссылками, вы можете просмотреть дополнительные сведения о каждом из них.
ms.custom: SEO-VS-2020
ms.date: 04/25/2018
ms.topic: conceptual
ms.assetid: 4c6fe8f1-b015-4989-bb31-72ebac390026
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9959c73802e15ca25dcce62631e4faa81391d47a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389895"
---
# <a name="inspect-data-using-debugger-windows-in-visual-studio"></a>Проверка данных с помощью окон отладчика в Visual Studio

В процессе отладки программы можно открывать большинство окон отладчика. Чтобы просмотреть список окон отладчика, установите точку останова и начните отладку. Когда точка останова будет достигнута и выполнение остановится, выберите пункт **Отладка > Окна**.

|Окно|Сочетание клавиш|Раздел|
|-|-|-|
|Точки останова|CTRL+ALT+B|[Использование точек останова](../debugger/using-breakpoints.md)|
|Параметры исключений|CTRL+ALT+E|[Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)|
|Вывод|CTRL+ALT+O|[Окно выходных данных](../ide/reference/output-window.md)|
|Контрольное значение|CTRL+ALT+W, (1, 2, 3, 4)|[Окна "Контрольные значения" и "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)|
|Контрольное значение|SHIFT+F9|[Окна "Контрольные значения" и "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)|
|Автоматические|CTRL+ALT+V, A|[Окна "Видимые" и "Локальные"](../debugger/autos-and-locals-windows.md)|
|Локальные|CTRL+ALT+V, L|[Окна "Видимые" и "Локальные"](../debugger/autos-and-locals-windows.md)|
|Стеки вызовов|CTRL+ALT+C|[Практическое руководство. использование окна "Стек вызовов"](../debugger/how-to-use-the-call-stack-window.md)|
|Интерпретация|CTRL+ALT+I|[Окно интерпретации](../ide/reference/immediate-window.md)|
|Параллельные стеки|CTRL+SHIFT+D, S|[Использование окна "Параллельные стеки"](../debugger/using-the-parallel-stacks-window.md)|
|Контроль параллельных данных|CTRL+SHIFT+D, (1, 2, 3, 4)|[Начало отладки многопоточных приложений](../debugger/get-started-debugging-multithreaded-apps.md)|
|Потоки|CTRL+ALT+H|[Отладка с помощью окна потоков](../debugger/how-to-use-the-threads-window.md)|
|Модули|CTRL+ALT+U|[Практическое руководство. Использование окна модулей](../debugger/how-to-use-the-modules-window.md)|
|Потоки GPU|-|[Практическое руководство. использование окна потоков GPU](../debugger/how-to-use-the-gpu-threads-window.md)|
|Задачи|CTRL+SHIFT+D, K|[Использование окна задач](../debugger/using-the-tasks-window.md)|
|Интерактивная отладка Python|SHIFT+ALT+I|[Интерактивная оболочка REPL для Python](../python/python-interactive-repl-in-visual-studio.md)|
|Консоль JavaScript|CTRL+ALT+V, C|[Краткое руководство. Отладка JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)|
|Обозреватель DOM|CTRL+ALT+V, D|[Отладка макета с использованием проводника DOM](quickstart-debug-html-and-css.md)|
|Динамическое визуальное дерево|-|[Просмотр свойств XAML во время отладки](../xaml-tools/inspect-xaml-properties-while-debugging.md)|
|Динамический обозреватель свойств|-|[Просмотр свойств XAML во время отладки](../xaml-tools/inspect-xaml-properties-while-debugging.md)|
|Процессы|CTRL+ALT+Z|[Отладка потоков и процессов](../debugger/debug-threads-and-processes.md)|
|Память|CTRL+ALT+M, (1, 2, 3, 4)|[Окно памяти](../debugger/memory-windows.md)|
|Дизассемблированный код|CTRL+ALT+D|[Практическое руководство. Использование окна дизассемблирования](../debugger/how-to-use-the-disassembly-window.md)|
|Регистры|CTRL+ALT+G|[Практическое руководство. Использование окна регистров](../debugger/how-to-use-the-registers-window.md)|

## <a name="see-also"></a>См. также

[Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)