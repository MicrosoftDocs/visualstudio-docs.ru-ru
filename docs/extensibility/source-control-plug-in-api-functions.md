---
title: Функции API подключаемого модуля системы управления версиями | Документация Майкрософт
description: Сведения о функциях, предоставляемых API подключаемого модуля системы управления версиями, который должен быть реализован с помощью подключаемого модуля системы управления версиями.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c28c175d53fb37cf890dad4240a84fb132f6af35
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090126"
---
# <a name="source-control-plug-in-api-functions"></a>Функции API подключаемого модуля системы управления версиями
Интерфейс API подключаемого модуля системы управления версиями предоставляет следующие функции, которые должны быть реализованы с помощью подключаемого модуля системы управления версиями в соответствии с этим API. Сигнатуры каждой функции и семантики, связанные с битовыми флагами и другими параметрами, подробно описаны в этом справочнике.

## <a name="initialization-and-housekeeping-functions"></a>Функции инициализации и обслуживания

|Функция|Описание|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Закрывает проект.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Запрашивает у пользователя дополнительные параметры для данной команды.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Возвращает версию подключаемого модуля системы управления версиями.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Инициализирует подключаемый модуль системы управления версиями. Он вызывается один раз для каждого экземпляра подключаемого модуля.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Открывает проект.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Универсальная функция, используемая для задания разнообразных параметров. Каждый параметр начинается с `SCC_OPT_xxx` и имеет собственный набор значений.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Вызывается один раз, когда необходимо отключить подключаемый модуль системы управления версиями.|

## <a name="core-source-control-functions"></a>Основные функции системы управления версиями

|Функция|Описание|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Добавляет в систему управления версиями массив файлов, заданный полными именами путей.|
|[SccAddFilesFromSCC](../extensibility/sccaddfromscc-function.md)|Позволяет пользователю просматривать файлы, уже находящиеся в системе управления версиями, а затем делать эти файлы частью текущего проекта.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Возвращает массив файлов.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Извлекает массив файлов.|
|[SccDiff](../extensibility/sccdiff-function.md)|Показывает различия между файлом локального пользователя, указанным полным именем пути и версией в системе управления версиями.|
|[SccGet](../extensibility/sccget-function.md)|Извлекает доступную только для чтения копию набора файлов.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Проверяет состояние файлов, о которых запросил вызывающий объект (через `SccQueryInfo` ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Заставляет подключаемый модуль системы управления версиями запрашивать у пользователя путь к проекту, который является значимым для подключаемого модуля.|
|[SccHistory](../extensibility/scchistory-function.md)|Показывает журнал для массива полных имен локальных файлов.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Проверяет список файлов на предмет их текущего состояния. Кроме того, использует `pfnPopulate` функцию для уведомления вызывающего объекта, если файл не соответствует критериям для `nCommand` .|
|[SccProperties](../extensibility/sccproperties-function.md)|Показывает свойства полного файла.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Проверяет список полных файлов в соответствии с их текущим состоянием.|
|[SccRemove](../extensibility/sccremove-function.md)|Удаляет массив полных файлов из системы управления версиями.|
|[SccRename](../extensibility/sccrename-function.md)|Переименовывает заданный файл в новое имя в системе управления версиями.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Обращается к полному спектру функций системы управления версиями.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Отменяет извлечение массива файлов.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Функции, поддерживающие дополнительные возможности (версия 1,2 интерфейса API подключаемого модуля системы управления версиями)
 Эта группа функций определяет дополнительные функциональные возможности, реализованные в версии 1,2 API подключаемого модуля системы управления версиями. Они предоставляют доступ к более сложным функциям и возможностям системы управления версиями.

|Функция|Описание|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Запускает пакетную операцию.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Создает подпроект с заданным именем в существующем родительском проекте.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Показывает различия между каталогом локального пользователя, заданным полным именем пути и расположением базы данных системы управления версиями.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Проверяет список полных каталогов на предмет их текущего состояния.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Завершает пакетную операцию.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Возвращает родительский путь данного проекта (проект должен существовать).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Проверяет, разрешено ли многократное извлечение файла.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Проверяет, будет ли подключаемый модуль создавать МССККПРЖ. Файлы SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Функции, поддерживающие расширенную возможность (версия 1,3 интерфейса API подключаемого модуля системы управления версиями)
 Эта группа функций определяет дополнительные функциональные возможности, реализованные в версии 1,3 API подключаемого модуля системы управления версиями. Они предоставляют доступ к более сложным функциям и возможностям системы управления версиями.

|Функция|Описание|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Добавляет список файлов из системы управления версиями в текущий проект.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Извлекает список файлов из системы управления версиями без пользовательского интерфейса.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Извлекает список файлов в системе управления версиями, которые отличаются от локальных файлов.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Получает флаги, указывающие расширенные возможности, поддерживаемые подключаемым модулем системы управления версиями.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Возвращает параметры, относящиеся к пользователю.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Проверяет список каталогов и файлов в проекте или проектах, которые находятся в системе управления версиями. Каждый найденный каталог и имя файла передаются в функцию обратного вызова.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Проверяет изменения имен, внесенные в список файлов. Каждое имя файла передается функции обратного вызова с состоянием изменения.|

## <a name="requirements"></a>Требования
 Заголовок: SCC. h

 (Указывается в папке Common SDK для среды, по умолчанию *[диск]* \Program филес\всип 8.0 \ енвсдк\коммон\инк; также можно задать в папке VSIP с помощью примера MSSCCI, *[диск]* \PROGRAM филес\всип 8.0 \ MSSCCI).

## <a name="see-also"></a>См. также раздел
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
- [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md)
