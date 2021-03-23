---
title: Запуск от имени администратора
description: Узнайте, как запустить Visual Studio от имени администратора.
ms.date: 03/09/2021
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3d2a22533137bf2c1f2e7cfeb3802f5824c3926
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607253"
---
# <a name="user-permissions-and-visual-studio"></a>Разрешения пользователей и Visual Studio

Для обеспечения безопасности следует по возможности запускать Visual Studio от имени обычного пользователя.

> [!WARNING]
> Также необходимо компилировать, запускать и отлаживать только те решения Visual Studio, которые получены от надежных людей или из надежных расположений.

Под именем обычного пользователя в Visual Studio IDE можно делать практически все. Разрешения администратора необходимы для выполнения следующих задач.

|Область|Задача|Дополнительные сведения|
|----------|----------| - |
|Установка|Установите или измените Visual Studio.|[Установка Visual Studio](../install/install-visual-studio.md), [изменение Visual Studio](../install/modify-visual-studio.md)|
||Установка, обновление или удаление содержимого локальной справки.|[Установка содержимого локальной справки и управление им](../help-viewer/install-manage-local-content.md)|
|Панель элементов|Добавление классических элементов управления COM в **панель элементов**.|[Панель элементов](../ide/reference/toolbox.md)|
|Сборка|Использование выполняющихся после сборки событий, которые регистрируют компонент.|[Сведения о настраиваемых этапах сборки и событиях сборки](/cpp/build/understanding-custom-build-steps-and-build-events)|
||Включение этапа регистрации при сборке проектов С++.||
|Отладка|Отладка приложений с повышенными разрешениями.|[Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)|
||Отладка приложений, выполняемых под другой учетной записью пользователя, например веб-сайтов ASP.NET.|[Отладка приложений ASP.NET и AJAX](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||Отладка в зоне для приложений XAML-браузера (XBAP).|[Основное приложение WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Использование эмулятора для отладки проектов облачных служб для Microsoft Azure.|[Отладка облачной службы в Visual Studio](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Настройка брандмауэра для удаленной отладки.|[Удаленная отладка](../debugger/remote-debugging.md)|
|Средства производительности|Подключение к приложению с повышенными правами.|[Руководство по профилированию производительности для начинающих](../profiling/beginners-guide-to-performance-profiling.md)|
||Используйте профилировщик GPU.|[Профилирование GPU](../profiling/gpu-usage.md)|
|Развертывание|Развертывание веб-приложения в службах IIS на локальном компьютере.|[Развертывание веб-приложения ASP.NET с помощью Visual Studio](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Запуск Visual Studio от имени администратора

Если необходимо запустить Visual Studio от имени администратора, выполните следующие действия, чтобы открыть интегрированную среду разработки.

> [!NOTE]
> Эти инструкции предназначены для Windows 10. Для других версий Windows они аналогичны.

::: moniker range="vs-2017"

1. Откройте меню **Пуск** и перейдите к Visual Studio 2017.

1. При помощи щелчка правой кнопкой или контекстного меню **Visual Studio 2017** выберите **Дополнительно** > **Запуск от имени администратора**.

   После запуска Visual Studio в заголовке окна после имени продукта будет указано **(Администратор)**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Откройте меню **Пуск** и перейдите к Visual Studio 2019.

1. При помощи щелчка правой кнопкой или контекстного меню **Visual Studio 2019** выберите **Дополнительно** > **Запуск от имени администратора**.

   После запуска Visual Studio в заголовке окна после имени продукта будет указано **(Администратор)**.

::: moniker-end

Можно также изменить ярлык приложения, чтобы всегда запускать его с правами администратора:

1. Откройте меню **Пуск**, перейдите к версии Visual Studio, которую вы используете, и выберите **Дополнительно** > **Перейти к расположению файла**.

1. В **Проводнике** найдите ярлык для используемой версии **Visual Studio**. Затем щелкните ярлык правой кнопкой мыши и выберите **Отправить** > **Рабочий стол (создать ярлык)** .

1. На рабочем столе **Windows** щелкните правой кнопкой мыши ярлык **Visual Studio** и выберите **Свойства**.

1. Нажмите кнопку **Дополнительно**, а затем установите флажок **Запуск от имени администратора**.

1. Щелкните **ОК**, а затем снова **ОК**.

## <a name="see-also"></a>См. также раздел

- [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Установка Visual Studio](../install/install-visual-studio.md)
