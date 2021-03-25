---
title: 'Создание нового проекта: внутри, часть 2 | Документация Майкрософт'
description: Ознакомьтесь с подробным описанием того, что происходит в интегрированной среде разработки Visual Studio (IDE) при создании собственного типа проекта (часть 2 из 2).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e391ad66c9925dc68997ff610dc5d1556ddf09b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063088"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Создание проекта: как это работает, часть 2

В [новом создании проекта: в части](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) мы увидели, как заполняется диалоговое окно **Новый проект** . Предположим, что вы выбрали **приложение Windows на Visual C#**, заполнили текстовые поля **имя** и **Расположение** и щелкнули ОК.

## <a name="generating-the-solution-files"></a>Создание файлов решения
 При выборе шаблона приложения выполняется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Распаковка и открытие соответствующего VSTEMPLATE-файла, а также запуск шаблона для интерпретации команд XML в этом файле. Эти команды создают проекты и элементы проекта в новом или существующем решении.

 Шаблон распаковать исходные файлы, называемые шаблонами элементов, из той же ZIP-папки, в которой находится VSTEMPLATE-файл. Шаблон копирует эти файлы в новый проект, соответствующим образом настраивая их.

### <a name="template-parameter-replacement"></a>Замена параметра шаблона
 Когда шаблон копирует шаблон элемента в новый проект, он заменяет все параметры шаблона строками для настройки файла. Параметр шаблона — это специальный маркер, которому предшествует и следует знак доллара, например $date $.

 Рассмотрим типичный шаблон элемента проекта. Извлеките и изучите программу Program. cs в папке Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace $safeprojectname$
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

При создании нового проекта приложения Windows с именем Simple шаблон заменяет `$safeprojectname$` параметр именем проекта.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Simple
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

 Полный список параметров шаблона см. в разделе [Параметры шаблона](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Взгляните внутри. Файл VSTemplate
 Файл Basic. vstemplate имеет этот формат

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Мы рассматривали \<TemplateData> раздел, посвященный [созданию нового проекта: внутри его части](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Теги в этом разделе используются для управления внешним видом диалогового окна « **Создание проекта** ».

 Теги в \<TemplateContent> разделе управляют созданием новых проектов и элементов проектов. Ниже приведен \<TemplateContent> раздел из файла ксвиндовсаппликатион. vstemplate в папке \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
      Settings.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">
      Form1.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Form1.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Program.cs
    </ProjectItem>
  </Project>
</TemplateContent>
```

 \<Project>Тег управляет созданием проекта, а \<ProjectItem> тег управляет созданием элемента проекта. Если параметр Реплацепараметерс имеет значение true, шаблон будет настраивать все параметры шаблона в файле проекта или элементе. В этом случае все элементы проекта настроены, за исключением Settings. Settings.

 Параметр Таржетфиленаме задает имя и относительный путь к результирующему файлу проекта или элементу. Это позволяет создать структуру папок для проекта. Если не указать этот аргумент, элемент проекта будет иметь то же имя, что и шаблон элемента проекта.

 Итоговая структура папки приложения Windows выглядит следующим образом:

 ![Снимок экрана структуры папок приложений Windows для решения "Simple" в обозреватель решений Visual Studio.](../../extensibility/internals/media/simplesolution.png)

 Первый и только \<Project> тег в шаблоне считывает:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Это указывает новому шаблону проекта создать файл проекта Simple. csproj путем копирования и настройки элемента шаблона виндовсаппликатион. csproj.

### <a name="designers-and-references"></a>Конструкторы и ссылки
 В обозреватель решений можно увидеть, что папка Properties существует и содержит ожидаемые файлы. Но как насчет ссылок проекта и зависимостей файлов конструктора, таких как Resources. Designer. CS to Resources. resx и Form1. Designer. CS to Form1. CS?  Они настраиваются в файле Simple. csproj при его создании.

 Вот \<ItemGroup> из простого. csproj, который создает ссылки на проект:

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 Вы видите, что это шесть ссылок на проекты, которые отображаются в обозреватель решений. Вот раздел из другого \<ItemGroup> . Для ясности было удалено несколько строк кода. В этом разделе зависят параметры Settings. Designer. cs для параметров. Settings:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>См. также

- [Создание проекта: как это работает, часть 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
