---
title: Измерение производительности кода Python
description: Проверка производительности кода Python при использовании интерпретаторов на основе CPython с помощью профилировщика Visual Studio.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d860acad409f553a90186e6898077e7bfd81dd90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918882"
---
# <a name="profile-python-code"></a>Профилирование кода Python

Вы можете профилировать приложение Python при использовании интерпретаторов на основе CPython. (Сведения о доступности этой функции для разных версий Visual Studio см. в разделе [Матрица возможностей — профилирование](overview-of-python-tools-for-visual-studio.md#matrix-profiling).)

## <a name="profiling-for-cpython-based-interpreters"></a>Профилирование для интерпретаторов на основе CPython

Профилирование запускается с помощью команды меню **Отладка** > **Запустить профилирование Python**, которая открывает диалоговое окно настройки:

![Диалоговое окно профилирования](media/profiling-start.png)

Когда вы нажмете кнопку **ОК**, запустится профилировщик, в котором откроется отчет о производительности. Из отчета вы узнаете, сколько времени выполнялось ваше приложение:

![Отчет профилирования о производительности](media/profiling-results.png)

> [!Note]
> При профилировании приложения Python Visual Studio собирает данные за время существования процесса. В настоящее время возможность приостановки профилирования не поддерживается. Мы хотим получить ваши отзывы о будущих возможностях. Используйте кнопку **Отзыв о продукте** внизу страницы.

## <a name="profiling-for-ironpython"></a>Профилирование для IronPython

Так как интерпретатор IronPython не основан на CPython, функция профилирования для него не работает.

Вместо этого используйте профилировщик Visual Studio .NET, запустив *ipy.exe* непосредственно в качестве целевого приложения с аргументами, чтобы запустить нужный скрипт загрузки. Включите в командную строку параметр `-X:Debug`, чтобы обеспечить отладку и профилирование для всего кода Python. Этот аргумент создает отчет о производительности, где указано время, затраченное на среду выполнения IronPython и основной код. Для вашего кода используются искаженные имена.

Кроме того, IronPython имеет некоторые встроенные средства профилирования, но пока для них нет хорошего средства визуализации. В разделе [о профилировщике IronPython](/archive/blogs/curth/an-ironpython-profiler) (на сайте блогов MSDN) вы можете узнать, какие средства доступны.