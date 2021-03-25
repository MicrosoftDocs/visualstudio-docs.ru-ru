---
title: Как использовать журнал действий | Документация Майкрософт
description: Пакеты VSPackage могут записывать сообщения в журнал действий. Узнайте, как использовать журнал действий для отладки пакетов VSPackage в розничных средах.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f02a8dd1497680239db9363a2e0682082f0c68d8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057342"
---
# <a name="how-to-use-the-activity-log"></a>Как использовать журнал действий
Пакеты VSPackage могут записывать сообщения в журнал действий. Эта функция особенно полезна для отладки пакетов VSPackage в розничных средах.

> [!TIP]
> Журнал действий всегда включен. Visual Studio сохраняет последовательный буфер последних 100 записей, а также первые 10 записей, имеющих общие сведения о конфигурации.

## <a name="to-write-an-entry-to-the-activity-log"></a>Запись записи в журнал действий

1. Вставьте этот код в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод или в любой другой метод, кроме конструктора VSPackage:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Этот код получает <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> службу и приводит ее к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейсу. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Записывает информационную запись в журнал действий, используя текущий контекст культуры.

2. При загрузке VSPackage (обычно при вызове команды или открытии окна) текст записывается в журнал действий.

## <a name="to-examine-the-activity-log"></a>Проверка журнала действий

1. Запустите Visual Studio с параметром командной строки [/log](../ide/reference/log-devenv-exe.md) , чтобы записать ActivityLog.xml на диск во время сеанса.

2. После закрытия Visual Studio найдите журнал действий во вложенной папке для данных Visual Studio:

   <em> *% AppData%</em>\микрософт\висуалстудио \\ \<version>\ActivityLog.xml*.

3. Откройте журнал действий в любом текстовом редакторе. Вот типичная запись:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Отказоустойчивость

Так как журнал действий является службой, журнал действий недоступен в конструкторе VSPackage.

Журнал действий следует получить непосредственно перед записью в него. Не кэшировать или не сохраняйте журнал действий для будущего использования.

## <a name="see-also"></a>См. также

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Устранение неполадок, связанных с пакетами VSPackage](../extensibility/troubleshooting-vspackages.md)
- [VSPackages](../extensibility/internals/vspackages.md)
