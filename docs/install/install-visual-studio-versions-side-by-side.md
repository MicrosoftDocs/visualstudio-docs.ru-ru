---
title: Параллельная установка версий Visual Studio
description: Узнайте, как можно установить Visual Studio на компьютер, на котором уже установлена более ранняя версия Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.openlocfilehash: f17759d186805dc72623f27c9f254c7a6c0d36e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941532"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Параллельная установка версий Visual Studio

Visual Studio можно установить на компьютер, на котором уже установлена более ранняя версия Visual Studio.

::: moniker range="vs-2017"

Прежде чем устанавливать несколько версий среды на одном компьютере, следует учесть следующие условия:

* При использовании Visual Studio 2017 для открытия решения, которое было создано в Visual Studio 2015, можно впоследствии снова открыть и изменить решение в более ранней версии, если в нем не реализованы никакие функции, относящиеся только к Visual Studio 2017.

* При попытке открыть решение, которое было создано в Visual Studio 2015 или более ранней версии, с помощью Visual Studio 2017 может потребоваться изменить проекты и файлы, чтобы они стали совместимы с Visual Studio 2017. Дополнительные сведения см. в разделе [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true).

::: moniker-end

::: moniker range=">= vs-2019"

Прежде чем устанавливать несколько версий среды на одном компьютере, следует учесть следующие условия:

* При использовании Visual Studio 2019 для открытия решения, которое было создано в Visual Studio 2017, можно впоследствии снова открыть и изменить решение в более ранней версии, если в нем не реализованы никакие функции, относящиеся только к Visual Studio 2019.

* При попытке открыть решение, которое было создано в Visual Studio 2017 или более ранней версии, с помощью Visual Studio 2019 может потребоваться изменить проекты и файлы, чтобы они стали совместимы с Visual Studio 2019. Дополнительные сведения см. в разделе [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

::: moniker-end

* В случае удаления версии Visual Studio с компьютера, на котором установлено более одной версии, сопоставления файлов Visual Studio будут удалены для всех версий.

* Visual Studio не обновляет расширения автоматически, так как не все расширения совместимы. Необходимо переустановить расширения из [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или с помощью средств издателя программного обеспечения.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Параллельная установка дополнительных номеров версий Visual Studio

При обновлении с одного дополнительного номера версии Visual Studio до следующего установщик Visual Studio по умолчанию обновит текущую установку до следующей версии в этом канале. Например, при установке предварительной версии 16.6.4 установщик попытается заменить текущую установку предварительной версии 16.6.3, так как обе версии находятся в канале предварительной версии 16.6. Это помогает гарантировать, что старые версии Visual Studio не занимают место на компьютере. В некоторых случаях может быть полезно устанавливать дополнительные номера версий параллельно. В нашем примере это означает, что на компьютере будут установлены обе версии — 16.6.3 и 16.6.4.

1. Скачайте [файл начального загрузчика Visual Studio](/visualstudio/releases/2019/history#installing-an-earlier-release) для дополнительного номера версии, который вы хотите установить параллельно с существующими версиями Visual Studio.
2. Откройте командную строку с правами администратора. Для этого откройте меню "Пуск" Windows, введите cmd, щелкните результат поиска "Командная строка" правой кнопкой мыши и выберите **Запуск от имени администратора**. В командной строке измените каталог на папку, в которой находится файл начального загрузчика Visual Studio.
3. Выполните следующую команду, указав новый путь к папке для расположения установки и заменив имя EXE-файла соответствующим именем начального загрузчика для устанавливаемой версии Visual Studio. Имя EXE-файла должно совпадать с одним из указанных ниже или быть похожим на него:
   * vs_community.exe для Visual Studio Community
   * vs_professional.exe для Visual Studio Professional
   * vs_enterprise.exe для Visual Studio Enterprise

   ```
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<2019 AddNewPath>"
   ```

4. Следуйте указаниям в диалоговых окнах установщика, чтобы выбрать компоненты для установки. Дополнительные сведения см. в разделе [Установка Visual Studio](install-visual-studio.md#step-4---choose-workloads).

## <a name="net-framework-versions-and-side-by-side-installations"></a>Версии платформы .NET Framework и установка нескольких версий на один компьютер

В проектах Visual Basic, Visual C# и Visual F# параметр **Целевая рабочая среда** в **конструкторе проектов** используется для определения того, какая версия платформы .NET Framework используется в проекте. Для проекта C++ можно вручную изменить целевую платформу, изменив VCXPROJ-файл. Дополнительные сведения см. в разделе [Совместимость версий в .NET Framework](/dotnet/framework/migration-guide/version-compatibility).

При создании проекта можно указать целевую версию .NET Framework проекта в списке **.NET Framework** в диалоговом окне **Создание проекта** .

Сведения, относящиеся к конкретному языку, см. в соответствующем разделе следующей таблицы.

::: moniker range="vs-2017"

| Язык | Раздел |
|--------------|-----------|
| Visual Basic | [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017&preserve-view=true) |
| Visual C# | [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017&preserve-view=true) |
| Visual F# | [Разработка в Visual Studio с использованием Visual F#](../ide/fsharp-visual-studio.md?view=vs-2017&preserve-view=true) |
|C++ | [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md?view=vs-2017&preserve-view=true)
* [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)
* [Создание изолированных приложений и параллельных сборок C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Язык | Раздел |
|--------------|-----------|
| Visual Basic | [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Разработка в Visual Studio с использованием Visual F#](../ide/fsharp-visual-studio.md) |
| C++ | [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md)
* [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Создание изолированных приложений и параллельных сборок C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
