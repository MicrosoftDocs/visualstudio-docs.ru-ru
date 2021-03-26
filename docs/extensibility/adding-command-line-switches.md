---
title: Добавление параметров Command-Line | Документация Майкрософт
description: Узнайте, как добавить параметры командной строки, применяемые к VSPackage при выполнении команды devenv.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 826029154763a98279b5e5446317802531b08bfe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097569"
---
# <a name="add-command-line-switches"></a>Добавление параметров командной строки
При выполнении *devenv.exe* можно добавить параметры командной строки, которые применяются к пакету VSPackage. Используйте <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> для объявления имени переключателя и его свойств. В этом примере параметр Мисвитч добавляется для подкласса VSPackage с именем **аддкоммандсвитчпаккаже** без аргументов и при этом автоматически загружается пакетом VSPackage.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Именованные параметры показаны в следующих описаниях.

|Имя|Описание|
|-|-|
| Аргументы | Число аргументов для переключателя. Может быть "*" или списком аргументов. |
| DemandLoad | Загружать VSPackage автоматически, если задано значение 1, в противном случае — значение 0. |
| HelpString | Строка справки или идентификатор ресурса строки, отображаемой с помощью **команды devenv/?**. |
| Имя | Параметр. |
| PackageGuid | Идентификатор GUID пакета. |

 Первое значение аргумента обычно равно 0 или 1. Специальное значение "*" можно использовать для указания того, что весь остаток командной строки является аргументом. Это может быть полезно для сценариев отладки, в которых пользователь должен передать командную строку отладчика.

 Значение DemandLoad либо `true` (1), либо `false` (0) указывает, что пакет VSPackage должен быть загружен автоматически.

 Значение HelpString — это идентификатор ресурса строки, которая отображается в **devenv/?** Отображение справки. Это значение должно быть в формате "#nnn", где NNN — целое число. Строковое значение в файле ресурсов должно заканчиваться символом новой строки.

 Значение Name — это имя переключателя.

 Значение PackageGuid — это идентификатор GUID пакета, который реализует этот параметр. Интегрированная среда разработки использует этот идентификатор GUID для поиска пакета VSPackage в реестре, к которому применяется параметр командной строки.

## <a name="retrieve-command-line-switches"></a>Получение параметров командной строки
 После загрузки пакета можно получить параметры командной строки, выполнив следующие действия.

1. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации VSPackage вызовите on, `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> чтобы получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> интерфейс.

2. Вызовите метод, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> чтобы получить параметры командной строки, которые пользователь указал.

   В следующем коде показано, как определить, была ли указана пользователем команда Мисвитч в командной строке:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Вы обязаны проверять параметры командной строки каждый раз при загрузке пакета.

## <a name="see-also"></a>См. также раздел
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Параметры командной строки для devenv](../ide/reference/devenv-command-line-switches.md)
- [Служебная программа CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. Файлы pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
