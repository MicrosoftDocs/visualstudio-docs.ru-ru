---
title: '&apos;Новые возможности API подключаемого модуля системы управления версиями 1,3'
description: Узнайте о новых возможностях в интерфейсе API подключаемого модуля системы управления версиями 1,3, в котором представлены новые функции, обеспечивающие более расширенный контроль.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ab9079248931758efbcfcd792ce3c79ccffb270
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074266"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Новые&#39;в API подключаемого модуля системы управления версиями 1,3
В API-интерфейсе версии 1,3 для подключаемого модуля системы управления версиями представлены следующие новые функции, обеспечивающие более расширенный контроль.

## <a name="changes"></a>Изменения
 Следующие функции являются новыми для подключаемого модуля управления версиями для API версии 1,3:

|Функция|Обзор|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Позволяет сообщать о дополнительных битах возможностей|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Позволяет проанализировать файлы, имеющие более новые версии в базе данных системы управления версиями, чем на локальном диске.|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Позволяет проанализировать состояние изменений имен (переименований, дополнений и удалений) для указанных файлов.|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Позволяет проанализировать каталоги и файлы в базе данных системы управления версиями|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Добавляет указанный список файлов из базы данных системы управления версиями в текущий проект|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Выполняет неавтоматический "получение" указанных файлов (пользовательский интерфейс не отображается)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Разрешает доступ к параметрам, относящимся к пользователю|

## <a name="see-also"></a>См. также
- [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
