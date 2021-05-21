---
title: Документация по Visual Studio. Новые возможности выпуска за апрель 2021 г.
titleSuffix: ''
description: Обновления документации по Visual Studio за апрель 2021 г.
ms.date: 05/03/2021
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 38115892acc9c27e70ad956740cee8ae9e9c66ef
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2021
ms.locfileid: "108640939"
---
# <a name="visual-studio-docs-whats-new-for-april-2021"></a>Документация по Visual Studio. Новые возможности выпуска за апрель 2021 г.

Узнайте, что изменилось в документации по Visual Studio за апрель 2021 г. В этой статье перечислены основные изменения, внесенные в документацию в течение этого периода. Сведения об изменениях за предыдущие месяцы см. в [сводке по изменениям](whats-new-visual-studio-docs-history.md).

## <a name="azure"></a>Azure

**Обновленные статьи**

- [Создание и развертывание в облачных службах (расширенная поддержка) в Visual Studio](../azure/cloud-services-extended-support.md) — изменения в общедоступной версии облачных служб (расширенная поддержка)

## <a name="containers"></a>Контейнеры

**Новые статьи**

- [Использование управляемого удостоверения с Bridge to Kubernetes](../containers/managed-identity.md) — управляемое удостоверение для Bridge to Kubernetes

**Обновленные статьи**

- [Свойства сборки Docker Compose](../containers/docker-compose-properties.md) — дополнения для свойств Compose
- [Как Visual Studio создает контейнерные приложения](../containers/container-build.md) — обновление для LTS

## <a name="debugger"></a>Отладчик

**Новые статьи**

- [IDiaSymbol::get_framePadOffset](../debugger/debug-interface-access/idiasymbol-get-framepadoffset.md) — дополнения к пакету SDK для доступа к интерфейсу отладки
- [IDiaSymbol::get_framePadSize](../debugger/debug-interface-access/idiasymbol-get-framepadsize.md) — дополнения к пакету SDK для доступа к интерфейсу отладки
- [IDiaSymbol::get_isRTCs](../debugger/debug-interface-access/idiasymbol-get-isrtcs.md) — дополнения к пакету SDK для доступа к интерфейсу отладки
- [Отладка дампа управляемой памяти с помощью диагностических анализаторов .NET](../debugger/how-to-debug-managed-memory-dump.md) — анализаторы дампа памяти VS

**Обновленные статьи**

- [Файлы дампа в отладчике Visual Studio](../debugger/using-dump-files.md) — анализаторы дампа памяти VS
- [Принципы отладки для начинающих](../debugger/debugging-absolute-beginners.md) — добавлено руководство по VB для начинающих

## <a name="get-started"></a>Начало работы

**Обновленные статьи**

- [Учебник. Расширение простого консольного приложения C#](../get-started/csharp/tutorial-console-part-2.md) — добавлены пояснения к действиям и полный код для расширения учебника

## <a name="ide"></a>IDE

**Обновленные статьи**

- [Справка F1: совпадение не найдено](./not-in-toc/default.md) — обновлен документ default.md
- [Командная строка разработчика и PowerShell для разработчиков в Visual Studio](./reference/command-prompt-powershell.md) — улучшения производительности содержимого
- [Подключение к проектам в Team Explorer](./connect-team-project.md) — изменена страница "Подключение к проектам в Team Explorer" в VS 2019

## <a name="install"></a>Установка

**Обновленные статьи**

- [Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) — обновлен документ use-command-line-parameters-to-install-visual-studio.md
- [Использование параметров командной строки для установки Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) — обновлен документ use-command-line-parameters-to-install-visual-studio.md
- [Настройка параметров по умолчанию для корпоративных развертываний Visual Studio](../install/set-defaults-for-enterprise-deployments.md) — устранены опечатки, связанные с обновлениями администратора, и удалены ненужные предупреждения из корпоративных развертываний по умолчанию
- [Номера сборки и даты выпуска Visual Studio](../install/visual-studio-build-numbers-and-release-dates.md) — добавлены обновления в день установки исправлений
- [Применение обновлений администратора с использованием Microsoft Endpoint Configuration Manager](../install/applying-administrator-updates.md) — обновления администратора
- [Управление обновлением сетевых развертываний Visual Studio](../install/controlling-updates-to-visual-studio-deployments.md) — обновления администратора
- [Создание сетевой установки Visual Studio](../install/create-a-network-installation-of-visual-studio.md) — обновления администратора
- [Включение обновлений администратора в Visual Studio с помощью Microsoft Endpoint Configuration Manager](../install/enabling-administrator-updates.md) — обновления администратора
- [Средства для обнаружения экземпляров Visual Studio и управления ими](../install/tools-for-managing-visual-studio-instances.md) — обновления администратора
- [Обновление до последнего выпуска Visual Studio](../install/update-visual-studio.md) — обновления администратора
- [Руководство администратора Visual Studio](../install/visual-studio-administrator-guide.md) — обновления администратора
- [Руководство по Visual Studio Enterprise](../install/visual-studio-enterprise-guide.md) — обновления администратора

## <a name="msbuild"></a>MSBuild

**Новые статьи**

- [MSB8066: пользовательская сборка для "item-list" завершилась с кодом "error code"](../msbuild/errors/msb8066.md) — черновик новой страницы для msb8066
- [MSB8040: для этого проекта требуются библиотеки с устранением рисков Spectre](../msbuild/errors/msb8040.md) — сообщения об ошибках MSBuild для C++
- [MSB8041: для этого проекта требуются библиотеки MFC](../msbuild/errors/msb8041.md) — сообщения об ошибках MSBuild для C++
- [MSB3277: обнаружены конфликты между разными версиями сборки, разрешить которые не удалось](../msbuild/errors/msb3277.md) — ошибка MSB3277 MSBuild

## <a name="python"></a>Python

**Обновленные статьи**

- [Создание расширения C++ для Python](../python/working-with-c-cpp-python-in-visual-studio.md)
  - Небольшие обновления для устранения проблем с GH
  - Улучшен документ working-with-c-cpp-python-in-visual-studio.md

## <a name="sharepoint"></a>SharePoint

**Обновленные статьи**

- [Создание связи между сущностями](../sharepoint/creating-an-association-between-entities.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 6
- [Практическое руководство. Добавление в обозреватель сервера пользовательского узла SharePoint](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 6
- [Практическое руководство. Доступ к службе проектов SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 6
- [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 6
- [Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 6
- [Пошаговое руководство. Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 6
- [Пошаговое руководство. Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 6
- [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 6
- [Пошаговое руководство. Создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 6
- [Пошаговое руководство. Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 6
- [Пошаговое руководство. Расширение обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 6

## <a name="test"></a>Тест

**Обновленные статьи**

- [Приступая к работе с модульным тестированием](../test/getting-started-with-unit-testing.md) — добавлен VB в руководство для начинающих
- [Начало работы с Live Unit Testing](../test/live-unit-testing-start.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7

## <a name="vsto"></a>Vsto

**Обновленные статьи**

- [Пошаговое руководство. Отображение настраиваемых областей задач с сообщениями электронной почты в Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Пошаговое руководство. Импорт области формы, созданной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Пошаговое руководство. Вставка данных в книгу на сервере](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Пошаговое руководство. Программирование реакции на события элемента управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Пошаговое руководство. Получение кэшированных данных из книги на сервере](../vsto/walkthrough-retrieving-cached-data-from-a-workbook-on-a-server.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Пошаговое руководство. Простая привязка данных в проекте уровня документа](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Пошаговое руководство. Простая привязка данных в проекте надстройки VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Пошаговое руководство. Синхронизация настраиваемой области задач с помощью кнопки ленты](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Пошаговое руководство. Обновление диаграммы в документе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Пошаговое руководство. Обновление диаграммы на листе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Пошаговое руководство. Обновление элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 11
- [Устранение ошибок в решениях Office](../vsto/troubleshooting-errors-in-office-solutions.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Добавление элементов управления в документ во время выполнения с помощью надстройки VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Добавление элементов управления на лист во время выполнения с помощью надстройки VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Автоматизация приложения в настраиваемой области задач](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Привязка элементов управления содержимым к пользовательским XML-частям](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Привязка данных к элементам управления на панели действий Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Привязка данных к элементам управления на панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Привязка к данным из службы в проекте надстройки VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Вызов кода из VBA в надстройке VSTO](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Изменение кэшированных данных из книги на сервере](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Изменение форматирования документа с помощью элементов управления CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Изменение форматирования листа с помощью элементов управления CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Сбор данных с использованием Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Сложная привязка данных в проекте уровня документа](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Сложная привязка данных в проекте надстройки VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью элемента "Лента (XML)"](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Создание связи "основной/подробности" с помощью кэшированного набора данных](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Создание шаблона с помощью элементов управления содержимым](../vsto/walkthrough-creating-a-template-by-using-content-controls.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Создание контекстных меню для закладок](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Пошаговое руководство. Создание первой надстройки VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 10
- [Практическое руководство. Программное заполнение таблиц Word свойствами документа](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md) — перемещение образцов файлов и обновление ссылок на код (часть 1) — 9
- [Практическое руководство. Программная печать документов](../vsto/how-to-programmatically-print-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программная печать листов](../vsto/how-to-programmatically-print-worksheets.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программная защита документов и их частей](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программная защита книг](../vsto/how-to-programmatically-protect-workbooks.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программный сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программное восстановление выделения после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Программное выполнение вычислений Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программное сохранение документов](../vsto/how-to-programmatically-save-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программное сохранение книг](../vsto/how-to-programmatically-save-workbooks.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программный поиск и замена текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Программный поиск текста в диапазонах ячеек на листе](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Программная сортировка данных на листах](../vsto/how-to-programmatically-sort-data-in-worksheets.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программное хранение и извлечение значений дат в диапазонах Excel](../vsto/how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программное обновление текста закладки](../vsto/how-to-programmatically-update-bookmark-text.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программное использование встроенных диалоговых окон в Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Чтение и запись в свойства документа](../vsto/how-to-read-from-and-write-to-document-properties.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Изменение размеров элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Изменение размеров элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Изменение размеров элементов управления NamedRange](../vsto/how-to-resize-namedrange-controls.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Проверка данных при добавлении новой строки в элемент управления ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Сохранение динамических элементов управления в документах Office](../vsto/persisting-dynamic-controls-in-office-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 9
- [Практическое руководство. Программное применение цвета к диапазонам Excel](../vsto/how-to-programmatically-apply-color-to-excel-ranges.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное кэширование источника данных в документе Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md) — перемещение образцов файлов и обновление ссылок на код (часть 1) — 8
- [Практическое руководство. Программное изменение форматирования в строках листа, содержащих выбранные ячейки](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное закрытие документов](../vsto/how-to-programmatically-close-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное закрытие книг](../vsto/how-to-programmatically-close-workbooks.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программный подсчет символов в документах](../vsto/how-to-programmatically-count-characters-in-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное создание таблиц в Word](../vsto/how-to-programmatically-create-word-tables.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное отображение документов в режиме предварительного просмотра](../vsto/how-to-programmatically-display-documents-in-print-preview.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное исключение знаков абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программное скрытие текста в документах](../vsto/how-to-programmatically-hide-text-in-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Практическое руководство. Программный перебор найденных элементов в документах](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 8
- [Доступ к области формы во время выполнения](../vsto/accessing-a-form-region-at-run-time.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Общие сведения о панели действий](../vsto/actions-pane-overview.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Практическое руководство. Добавление области действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Практическое руководство. Добавление элементов управления Bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Практическое руководство. Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Практическое руководство. Добавление пользовательских XML-частей в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Практическое руководство. Заполнение данными элементов управления ListObject](../vsto/how-to-fill-listobject-controls-with-data.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Практическое руководство. Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Практическое руководство. Сопоставление столбцов элемента управления ListObject данным](../vsto/how-to-map-listobject-columns-to-data.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Практическое руководство. Программное добавление и удаление примечаний на листе](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Практическое руководство. Программное добавление верхних и нижних колонтитулов к документам](../vsto/how-to-programmatically-add-headers-and-footers-to-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Практическое руководство. Программное добавление рисунков и объектов Word Art в документы](../vsto/how-to-programmatically-add-pictures-and-word-art-to-documents.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7
- [Практическое руководство. Программное добавление строк и столбцов в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md) — перемещены примеры файлов и обновлены ссылки на код (часть 1) — 7

## <a name="xaml-tools"></a>Средства XAML

**Обновленные статьи**

- [Использование данных времени разработки в Конструкторе XAML в Visual Studio](../xaml-tools/xaml-designtime-data.md) — добавлен пример UWP для ListView

## <a name="community-contributors"></a>Участники сообщества

Указанные ниже пользователи в течение этого периода внесли свой вклад в улучшение документации по Visual Studio. Спасибо! Сведения о том, как вносить изменения в документацию по Visual Studio, вы найдете в [руководстве для участников](/contribute/).

- [scott-xu](https://github.com/scott-xu) — Скотт Сюй (Scott Xu) (1)
- [shreyanavigyan](https://github.com/shreyanavigyan) — Шреян Авигян (Shreyan Avigyan) (1)
