---
title: Подготовка к отладке проектов консоли | Документация Майкрософт
description: Сведения о подготовке к отладке консольных проектов (C#, C++, Visual Basic, F#) в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d1610919667fdaf1a752ca56aef5358c0bd34f3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387818"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Подготовка к отладке: Проекты консоли (C#, C++, Visual Basic, F#)

Подготовка к отладке консольного проекта аналогична подготовке к отладке проекта Windows, с некоторыми дополнительными соображениями, такими как установка аргументов командной строки и приостановка приложения для отладки. Дополнительные сведения см. в статье [Подготовка к отладке. Приложения Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md). Из-за схожести всех консольных приложений в этом разделе описываются следующие типы проектов:

- консольное приложение C#, Visual Basic и F#

- консольное приложение C++ (.NET);

- консольное приложение С++ (Win32).

  Консольное приложение использует окно **Консоль** для получения входных данных и отображения выходных сообщений. Для записи в окно **Консоль** приложение должно использовать объект **Консоль** вместо объекта Debug. Для записи в окно **Вывод Visual Studio** используется, как обычно, объект Debug. Необходимо убедиться в какое место приложение записывает данные, иначе может оказаться, что поиск сообщений ведется не в том месте. Дополнительные сведения см. в разделах [Класс Console](/dotnet/api/system.console), [Класс Debug](/dotnet/api/system.diagnostics.debug) и [Окно вывода](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Задание аргументов командной строки

Может потребоваться задание аргументов командной строки для консольного приложения. Дополнительные сведения см. в статьях [Параметры проектов для конфигураций отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md) и [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), или [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-csharp-debug-configurations.md).

Подобно всем свойствам проекта, эти аргументы сохраняются в интервале между сеансами (как отладки, так и Visual Studio). Поэтому необходимо учитывать, что если предыдущий сеанс был посвящен отладке консольного приложения, в диалоговом окне **Страницы свойств \<Project>** могут присутствовать аргументы, сохранившиеся от предыдущих сеансов.

## <a name="start-the-application"></a>Запуск приложения

 Некоторые консольные приложения после запуска выполняются до полного завершения, после чего сразу закрываются. Если это происходит быстро, то можно не успеть прервать выполнение приложения и выполнить отладку. Чтобы можно было выполнить отладку такого приложения, необходимо использовать один из следующих приемов для запуска приложения.

- Установите точку останова в коде и запустите приложение.

- Запустите приложение, нажав клавишу **F10** (**Отладка** > **Шаг с обходом**) или **F11** (**Отладка** > **Шаг с заходом**), а затем пройдите по коду, используя другие параметры, такие как **Run to click** (Выполнение до щелчка).

- В редакторе кода щелкните правой кнопкой мыши строку и выберите пункт **Выполнить до текущей позиции**.

  При отладке консольного приложения может потребоваться запуск приложения из командной строки, а не из Visual Studio. В этом случае можно запустить приложение из командной строки и присоединить к нему отладчик Visual Studio. См. сведения о [присоединении к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  При запуске консольного приложения из Visual Studio окно **Консоль** иногда отображается позади окна Visual Studio. Если при попытке запустить консольное приложение из Visual Studio кажется, что ничего не происходит, попробуйте переместить окно Visual Studio.

## <a name="see-also"></a>См. также
- [Отладка машинного кода](../debugger/debugging-native-code.md)
- [Отладка управляемого кода](../debugger/debugging-managed-code.md)
- [Подготовка к отладке проектов C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Безопасность отладчика](../debugger/debugger-security.md)