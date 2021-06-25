---
title: Флаги возможностей | Документация Майкрософт
description: Сведения о флагах SCC_CAP_xxx, которые указывают возможности подключаемого модуля системы управления версиями, а также флаги SCC_EXCAP_xxx, которые указывают на расширенные возможности.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3fdb660fd4e7c595f522686280f8bec6c0acae81
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905102"
---
# <a name="capability-flags"></a>Флаги возможностей
Флаги SCC_CAP_ *xxx* — это битовые флаги, используемые для указания возможностей подключаемого модуля системы управления версиями. Флаги SCC_EXCAP_ *xxx* — это добавочные флаги, которые указывают расширенные возможности и разрешаются в целочисленные значения.

|Код возможности|Значение|Описание|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Поддерживает [сккремове](../extensibility/sccremove-function.md) и Command.|
|`SCC_CAP_RENAME`|0x00000002L|Поддерживает [сккренаме](../extensibility/sccrename-function.md) и Command.|
|`SCC_CAP_DIFF`|0x00000004L|Поддерживает [сккдифф](../extensibility/sccdiff-function.md) и Command.|
|`SCC_CAP_HISTORY`|0x00000008L|Поддерживает [скчистори](../extensibility/scchistory-function.md) и Command.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Поддерживает [сккпропертиес](../extensibility/sccproperties-function.md) и Command.|
|`SCC_CAP_RUNSCC`|0x00000020L|Поддерживает [сккрунскк](../extensibility/sccrunscc-function.md) и Command.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Поддерживает [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и Command.|
|`SCC_CAP_QUERYINFO`|0x00000080L|Поддерживает [скккуеринфо](../extensibility/sccqueryinfo-function.md) и Command.|
|`SCC_CAP_GETEVENTS`|0x00000100L|Поддерживает [сккжетевентс](../extensibility/sccgetevents-function.md) и Command.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Поддерживает [сккжетпрожпас](../extensibility/sccgetprojpath-function.md) и Command.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Поддерживает [сккаддфромскк](../extensibility/sccaddfromscc-function.md) и Command.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Поддерживает комментарий при извлечении.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Поддерживает комментарий к возврату.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Поддерживает комментарий к добавлению.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Поддерживает комментарий к удалению.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Записывает текст в выходную функцию, предоставляемую интегрированной средой разработки.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Поддерживает хранение файлов без разностей.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Поддерживает несколько журналов файлов.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Поддерживает сравнение файлов без учета регистра.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Поддерживает сравнение файлов, которое игнорирует пробелы.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Поддерживает поиск дополнительных файлов.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Поддерживает комментарии по созданию проекта.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Поддерживает diff во всех состояниях, если элемент управления находится под контролем.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Подключаемый модуль не поддерживает пользовательский интерфейс для Get, но интегрированная среда разработки по-прежнему может вызывать [сккжет](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|Подключаемый модуль является повторным входом и потокобезопасным. В версии 1,0 не предполагается, что подключаемые модули были перезапущены и являются потокобезопасными. Если этот бит устанавливает подключаемый модуль 1,1, узел может параллельно открывать несколько проектов.|

## <a name="capability-bits-added-in-version-12"></a>Биты возможностей, добавленные в версии 1,2

|Код возможности|Значение|Описание|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Поддерживает [скккреатесубпрожект](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Поддерживает [сккжетпарентпрожектпас](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Поддерживает [сккбегинбатч](../extensibility/sccbeginbatch-function.md) и [скцендбатч](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Поддерживает [сккдиркуеринфо](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Поддерживает [сккдирдифф](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Поддерживает несколько извлечений для файла и [скЦисмултичеккаутенаблед](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Поддерживает файл *мссккпрж. SCC* (переопределение пользователем или администратором) и [скквиллкреатесккфиле](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Биты возможностей, добавленные в версии 1,3
 Эти флаги передаются в функцию [сккжетекстендедкапабилитиес](../extensibility/sccgetextendedcapabilities-function.md) по одному за раз, чтобы определить, поддерживается ли эта возможность.

|Расширенный код возможности|Значение|Описание|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Поддерживает `SCC_CHECKOUT_LOCALVER` параметр для извлечений.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Поддерживает [сккбаккграунджет](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Поддерживает [скценумчанжедфилес](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Поддерживает поиск дополнительных каталогов.|
|`SCC_EXCAP_QUERYCHANGES`|5|Поддерживает перечисление изменений в файлах.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Поддерживает [сккаддфилесфромскк](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Поддерживает [сккжетусероптион](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Поддерживает вызов Скккуеринфо для нескольких потоков.|
|`SCC_EXCAP_REMOVE_DIR`|9|Поддерживает функцию Сккремоведир.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Может удалять извлеченные файлы.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Может переименовывать извлеченные файлы.|

## <a name="see-also"></a>См. также
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
