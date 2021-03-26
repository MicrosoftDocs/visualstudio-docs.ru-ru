---
title: Решение (. SLN)
description: Сведения о файле sln, который является одним из файлов, сохраняющих сведения о состоянии проекта в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27364382a7e4318fce822b148e9d3df6747bfd1e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082001"
---
# <a name="solution-sln-file"></a>Файл решения (SLN)

Решение представляет собой структуру для организации проектов в Visual Studio. Решение хранит сведения о состоянии проектов в двух файлах:

- SLN-файл (на основе текста, общий)

- suo-файл (двоичный, параметры решения для конкретного пользователя)

Дополнительные сведения о suo-файлах см. в разделе [пользовательские параметры решения (. Файл SUO)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Если пакет VSPackage загружен в результате ссылки в файле. sln, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> чтение в SLN-файле.

Файл. sln содержит текстовую информацию, которую среда использует для поиска и загрузки параметров "имя-значение" для сохраненных данных и проекта VSPackage, на который он ссылается. Когда пользователь открывает решение, среда циклически переключается по данным `preSolution` , `Project` и `postSolution` в SLN-файле для загрузки решения, проектов в решении и всех сохраненных данных, присоединенных к решению.

Файл каждого проекта содержит дополнительные сведения, считанные средой для заполнения иерархии элементами этого проекта. Сохраняемость данных иерархии управляется проектом. Обычно данные не хранятся в файле. sln, хотя вы можете намеренно записать сведения о проекте в SLN-файл. Дополнительные сведения о сохраняемости см. в статьях [Сохранение проекта](../../extensibility/internals/project-persistence.md) и [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Заголовок файла

Заголовок файла SLN выглядит следующим образом:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Определения

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Стандартный заголовок, определяющий версию формата файла.

`# Visual Studio 15`\
Основной номер версии Visual Studio (последней) сохранил этот файл решения. Эта информация определяет номер версии в значке решения.

`VisualStudioVersion = 15.0.26730.15`\
Полная версия Visual Studio (самая последняя) сохранила файл решения. Если файл решения сохраняется в более новой версии Visual Studio, имеющей ту же основную версию, это значение не обновляется, чтобы уменьшить число обновлений в файлах решения.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Минимальная (самая старая) версия Visual Studio, которая может открыть этот файл решения.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Определения

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Стандартный заголовок, определяющий версию формата файла.

`# Visual Studio Version 16`\
Основной номер версии Visual Studio (последней) сохранил этот файл решения. Эта информация определяет номер версии в значке решения.

`VisualStudioVersion = 16.0.28701.123`\
Полная версия Visual Studio (самая последняя) сохранила файл решения. Если файл решения сохраняется в более новой версии Visual Studio, имеющей ту же основную версию, это значение не обновляется, чтобы уменьшить количество изменений в файле.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Минимальная (самая старая) версия Visual Studio, которая может открыть этот файл решения.

::: moniker-end

## <a name="file-body"></a>Тело файла

Текст файла. sln состоит из нескольких разделов `GlobalSection` , например:

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

Чтобы загрузить решение, среда выполняет следующую последовательность задач:

1. Среда считывает глобальный раздел файла SLN и обрабатывает все отмеченные разделы `preSolution` . В этом примере файла есть одна такая инструкция:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Когда среда считывает `GlobalSection('name')` тег, она сопоставляет имя с пакетом VSPackage с помощью реестра. Имя ключа должно присутствовать в реестре в папке [HKLM \\<приложение с идентификатором реестра root \> \солутионперсистенце\аггрегатегуидс]. Значение по умолчанию для ключей — это идентификатор GUID пакета VSPackage (REG_SZ), который записал записи.

2. Среда загружает пакет VSPackage, вызывает `QueryInterface` интерфейс VSPackage для <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> интерфейса и вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> метод с данными в разделе, чтобы пакет VSPackage мог хранить данные. Среда повторяет этот процесс для каждого `preSolution` раздела.

3. Среда выполняет итерацию по блокам сохранения проекта. В этом случае существует один проект.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Эта инструкция содержит уникальный идентификатор GUID проекта и идентификатор GUID типа проекта. Эти сведения используются средой для поиска файла проекта или файлов, принадлежащих решению, и пакета VSPackage, необходимого для каждого проекта. Идентификатор GUID проекта передается в <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> для загрузки конкретных VSPackage, связанных с проектом, затем проект загружается пакетом VSPackage. В этом случае пакет VSPackage, загруженный для этого проекта, Visual Basic.

   Каждый проект может сохранять уникальный идентификатор экземпляра проекта, чтобы к нему можно было обращаться по мере необходимости в других проектах решения. В идеале, если решение и проекты находятся под управлением исходного кода, путь к проекту должен быть указан относительно пути к решению. При первой загрузке решения файлы проекта не могут находиться на компьютере пользователя. Файл проекта, хранящийся на сервере относительно файла решения, сравнительно прост для того, чтобы файл проекта был найден и скопирован на компьютер пользователя. Затем он копирует и загружает остальные файлы, необходимые для проекта.

4. В зависимости от сведений, содержащихся в разделе проекта файла SLN, среда загружает каждый файл проекта. Затем сам проект отвечает за заполнение иерархии проекта и загрузку всех вложенных проектов.

5. После обработки всех разделов файла. sln решение отображается в обозреватель решений и будет готово к изменению пользователем.

Если ни один пакет VSPackage, реализующий проект в решении, не загружается, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> вызывается метод, и каждый другой проект в решении получает возможность игнорировать изменения, которые он мог сделать во время загрузки. При возникновении ошибок анализа, как можно больше сведений сохраняется в файлах решения, и среда отображает диалоговое окно с предупреждением о том, что решение повреждено.

При сохранении или закрытии решения <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> метод вызывается и передается в иерархию, чтобы узнать, были ли внесены изменения в решение, которое необходимо указать в SLN-файле. Значение null, передаваемое в `QuerySaveSolutionProps` в <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> , указывает, что информация сохраняется для решения. Если значение не равно null, то сохраненная информация относится к конкретному проекту, определяемому указателем на <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейс.

Если имеются сведения для сохранения, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> интерфейс вызывается с указателем на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> метод. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>Затем метод вызывается средой для получения пар "имя-значение" из `IPropertyBag` интерфейса и записи сведений в SLN-файл.

`SaveSolutionProps``WriteSolutionProps`объекты и вызываются рекурсивно средой для получения сведений, которые должны быть сохранены из интерфейса, `IPropertyBag` пока все изменения не будут введены в файл. sln. Таким образом можно убедиться, что информация будет сохранена в решении и доступна при следующем открытии решения.

Каждый загруженный пакет VSPackage перечисляется, чтобы убедиться, что в файле. sln есть что-либо, что нужно сохранить. Это происходит только во время загрузки, в которое запрашиваются разделы реестра. Среда знает обо всех загруженных пакетах, так как они находятся в памяти во время сохранения решения.

Только файл. sln содержит записи в `preSolution` `postSolution` разделах и. В файле SUO Нет похожих разделов, так как решению требуется правильная загрузка этих сведений. Suo-файл содержит пользовательские параметры, такие как закрытые заметки, которые не предназначены для совместного использования или размещения в системе управления исходным кодом.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Файл параметров пользователя решения (SUO-файл)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Решения](../../extensibility/internals/solutions-overview.md)
