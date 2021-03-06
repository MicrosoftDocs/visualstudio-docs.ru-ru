---
title: Управление результатами нагрузочных тестов
description: Узнайте, как управлять данными, собранными во время нагрузочного теста, который хранится в базе данных SQL "Репозиторий результатов нагрузочного теста".
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 5245ccdb9130d3fac9639e7befc63ee2a5ebf70a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887618"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Управление результатами нагрузочного теста в репозитории результатов нагрузочного теста

При выполнении нагрузочных тестов собранные сведения сохраняются в *хранилище результатов нагрузочных тестов*, которое представляет собой базу данных SQL. В хранилище результатов нагрузочных тестов содержатся данные счетчиков производительности и сведения о записанных ошибках. База данных хранилища создается при установке для контроллеров или автоматически создается во время первого запуска нагрузочного теста на локальном компьютере. При запуске в локальной системе база данных будет создана автоматически, если отсутствует схема нагрузочного теста.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Если изменить в контроллере строку подключения к хранилищу, чтобы использовать другой сервер, на новом сервере для создания схемы нужно выполнить скрипт *loadtestresultsrepository.sql*.

В Visual Studio Enterprise предоставляются именованные наборы счетчиков, собирающие общие данные о производительности по технологиям. Эти наборы можно использовать при анализе работы сервера IIS, сервера ASP.NET или сервера SQL Server. Все данные, собранные наборами счетчиков, сохраняются в хранилище результатов нагрузочных тестов.

> [!IMPORTANT]
> Существуют различия между данными наборов счетчиков и счетчиков производительности. Набор счетчиков — это метаданные. Он определяет группу счетчиков производительности, данные которых нужно собирать с компьютера, обладающего определенной ролью, например ролью сервера IIS или сервера SQL Server. Набор счетчиков является частью определения нагрузочного теста. Данные счетчиков производительности собираются на базе наборов счетчиков, сопоставления набора счетчиков с определенным компьютером и частоты выборки.

## <a name="sql-server-versions"></a>Версии SQL Server

Для работы с нагрузочными тестами вы можете использовать сервер SQL Server Express LocalDB, который устанавливается вместе с Visual Studio. Этот сервер баз данных используется по умолчанию для нагрузочных тестов (включая интеграцию с Microsoft Excel). SQL Server Express LocalDB — это режим выполнения SQL Server Express, предназначенный для разработчиков программ. Установка SQL Server Express LocalDB копирует минимальный набор файлов, необходимый для запуска ядра базы данных SQL Server.

Если команда планирует интенсивно использовать базу данных или для проектов уже не хватает возможностей SQL Server Express LocalDB, следует рассмотреть обновление до SQL Express или полного выпуска SQL Server для обеспечения дальнейшего масштабирования. При обновлении SQL Server файлы MDF и LDF для SQL Server Express LocalDB будут храниться в папке профиля пользователя. Эти файлы можно использовать для импорта базы данных нагрузочных тестов в SQL Server Express или SQL Server.

## <a name="load-test-results-store-considerations"></a>Особенности хранилищ результатов нагрузочных тестов

Если установлен выпуск Visual Studio Enterprise, в качестве хранилища результатов нагрузочных тестов используется установленный на компьютере экземпляр SQL Express. Выпуск SQL Express поддерживает использование не более 4 ГБ места на диске. Если планируется запускать большое число нагрузочных тестов в течение длительного периода времени, следует подумать о настройке в качестве хранилища результатов экземпляра полной версии SQL Server, если таковой имеется.

## <a name="load-test-analyzer-tasks"></a>Задачи анализатора тестовой нагрузки

|Задания|Связанные разделы|
|-|-----------------------|
|**Настройка репозитория результатов нагрузочного теста**. Можно настроить репозиторий результатов нагрузочного теста в базе данных SQL. **Примечание.** Кроме того, репозиторий нагрузочного тестирования можно создать при установке контроллера тестирования. Дополнительные сведения см. в статье [Установка и настройка агентов тестирования](../test/lab-management/install-configure-test-agents.md).||
|**Выбор и просмотр репозитория результатов**. Можно выбрать конкретный репозиторий результатов. Не обязательно использовать локальное хранилище результатов. Нагрузочные тесты зачастую выполняются на наборе удаленных компьютеров агентов. Результаты тестов с компьютеров-агентов или с локального компьютера можно сохранить на любом сервере SQL Server, где было создано хранилище результатов нагрузочных тестов. В обоих случаях нужно указать расположение для сохранения результатов с помощью окна **Администрирование контроллеров тестов**.|-   [Практическое руководство. Выбор репозитория результатов нагрузочного теста](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Практическое руководство. обращение к результатам нагрузочного теста для их анализа](../test/how-to-access-load-test-results-for-analysis.md)|
|**Удаление результатов нагрузочных тестов из репозитория**. Результаты нагрузочного теста можно удалить из **редактора тестовой нагрузки** с помощью диалогового окна **Открытие и обработка результатов нагрузочных тестов**.|-   [Практическое руководство. удаление результатов нагрузочного тестирования из репозитория](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Импорт результатов в репозиторий и экспорт результатов из репозитория**. Результаты нагрузочных тестов можно импортировать в **редактор тестовой нагрузки** и экспортировать из него.|-   [Практическое руководство. импорт результатов нагрузочного тестирования в репозиторий](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Практическое руководство. экспорт результатов нагрузочного тестирования из репозитория](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>Связанные задачи

[Анализ результатов нагрузочных тестов](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

**Анализатор тестовой нагрузки** позволяет просматривать результаты выполняющихся и завершенных нагрузочных тестов.

## <a name="see-also"></a>См. также

- [Анализ результатов нагрузочных тестов](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Практическое руководство. Обращение к результатам нагрузочного теста для их анализа](../test/how-to-access-load-test-results-for-analysis.md)
