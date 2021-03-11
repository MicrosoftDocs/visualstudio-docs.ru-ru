---
title: Отладка приложения, не входящего в состав решения Visual Studio
titleSuffix: ''
description: Сведения об отладке приложения, не входящего в состав решения Visual Studio. Это можно сделать, подключив отладчик Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/21/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f201121eb65f7c045ac42783ac71b2d49fafd802
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155007"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Отладка приложения, которое не входит в решение Visual Studio (C++, C#, Visual Basic, F#)

Иногда требуется выполнить отладку приложения (*EXE*-файл), которое не является частью решения Visual Studio. Это может быть проект с [открытой папкой](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), вы или кто-то другой мог создать приложение вне Visual Studio или вы получили приложение в другом месте.

- Для проекта с открытой папкой в Visual Studio (без файла проекта или решения) см. статью [Выполнение и отладка кода](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) или (для C++) [Настройка параметров отладки с помощью launch.vs.json](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- Для приложения, которое не существует в Visual Studio, отладка обычно выполняется путем запуска за пределами Visual Studio, а затем присоединения с помощью функции **Присоединение к процессу** в отладчике Visual Studio. Дополнительные сведения см. в статье [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   Присоединение к приложению требует выполнения некоторых операций вручную, и это занимает несколько секунд. Из-за этой задержки присоединение не помогает отладить проблемы при запуске или приложение, которое не ждет ввода данных пользователем и быстро завершается.

   В таких ситуациях можно создать проект Visual Studio EXE для приложения или импортировать его в существующее решение C#, Visual Basic или C++. Не все языки программирования поддерживают исполняемые проекты.

>[!IMPORTANT]
>Функции отладки для приложения, не созданного в Visual Studio, ограниченны, независимо от того, присоединяетесь ли вы к нему или добавляете в решение Visual Studio.
>
>Если у вас есть исходный код, лучше всего импортировать его в проект Visual Studio. Затем запустите отладочную сборку приложения.
>
>Если у вас нет исходного кода и у приложения нет [отладочной информации](../debugger/how-to-set-debug-and-release-configurations.md) в совместимом формате, вам доступно немного функций отладки.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Создание EXE-проекта для существующего приложения

1. В Visual Studio последовательно выберите **Файл** > **Открыть** > **Проект**.

1. В диалоговом окне **Открыть проект** выберите **Все файлы проекта**, если они еще не выбраны, в раскрывающемся списке рядом с полем **Имя файла**.

1. Перейдите к *EXE*-файлу, выберите его и щелкните **Открыть**.

   Файл появится в новом временном решении Visual Studio.

1. Запустите отладку приложения, выбрав команду выполнения, например **Начать отладку** в меню **Отладка**.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Чтобы импортировать приложение в решение Visual Studio

1. Когда решение C++, C# или Visual Basic будет открыто в Visual Studio, выберите **Файл** > **Добавить** > **Существующий проект**.

1. В диалоговом окне **Открыть проект** выберите **Все файлы проекта**, если они еще не выбраны, в раскрывающемся списке рядом с полем **Имя файла**.

1. Перейдите к *EXE*-файлу, выберите его и щелкните **Открыть**.

   Файл появится как новый проект в текущем решении.

1. Выберите новый файл и запустите отладку приложения, выбрав команду выполнения, например **Начать отладку** в меню **Отладка**.

### <a name="see-also"></a>См. также
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)
- [Безопасность отладчика](../debugger/debugger-security.md)
- [DBG-файлы](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))
