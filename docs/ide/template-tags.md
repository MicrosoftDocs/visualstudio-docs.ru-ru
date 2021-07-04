---
title: Добавление или изменение тегов в шаблонах проектов
description: Узнайте, как добавлять и изменять теги в шаблонах проектов в Visual Studio.
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jmartens
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: ac4757464d720ca50632833b3911f0d594e1becb
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222985"
---
# <a name="add-tags-to-project-templates"></a>Добавление тегов к шаблонам проектов

Начиная с версии 16.1 предварительной версии 2, в [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) можно добавлять теги языка, платформы и типа проекта к шаблонам проектов. 

Теги используются в двух местах в диалоговом окне **Новый проект**:

- Теги отображаются под описанием шаблона.

   ![Шаблон проекта с тегами в диалоговом окне "Новый проект"](media/npd-item-with-template-tags.png)

- По тегам можно выполнять поиск шаблонов и фильтрацию результатов поиска.

   ![Выполнение поиска и фильтрации в диалоговом окне "Новый проект"](media/npd-search-and-filter.png)

Теги можно добавить, обновив XML-файл с расширением *.vstemplate*. Можно использовать встроенные в Visual Studio теги шаблонов или создать пользовательские. Теги шаблонов доступны только в диалоговом окне **Новый проект** в Visual Studio 2019. Теги шаблонов не влияют на отображение шаблонов в прежних версиях Visual Studio.

## <a name="add-or-edit-tags"></a>Добавление или изменение тегов

Вы можете добавлять теги в XML-файл шаблона проекта с расширением *.vstemplate* или изменять их при выполнении следующих действий:

* [создавая шаблон проекта](how-to-create-project-templates.md) с помощью мастера экспорта шаблонов;
* [обновляя шаблон проекта](how-to-update-existing-templates.md);
* [создавая шаблон проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="syntax"></a>Синтаксис

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Атрибуты

Можно использовать следующие необязательные атрибуты в сложных пользовательских сценариях.

|Атрибут|Описание|
|---------------|-----------------|
|`Package`|Идентификатор GUID, определяющий идентификатор пакета Visual Studio.|
|`ID`|Определяет идентификатор ресурса Visual Studio.|

Синтаксис:

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>Элементы

### <a name="child-elements"></a>Дочерние элементы

Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Обязательный.) Определяет категорию шаблона и то, как он отображается в диалоговом окне **Новый проект** или **Добавление нового элемента**.|

## <a name="text-value"></a>Текстовое значение

Текстовое значение является обязательным, если не используются атрибуты `Package` и `ID`.

Текстом передается имя шаблона.

## <a name="built-in-tags"></a>Встроенные теги

В Visual Studio доступны встроенные теги. При добавлении встроенного тега он позволяет отобразить локализованный ресурс. 

Ниже перечислены встроенные теги, доступные в Visual Studio. Соответствующие значения приводятся в скобках.

| Тег языка | Тег платформы | Тег типа проекта |
| -- | -- | -- |
| C++ (`cpp`) | Android (`android`) | Облако (`cloud`) |
| C# (`csharp`) | Azure (`azure`) | Консоль (`console`) |
| F# (`fsharp`) | iOS (`ios`) | Классическое приложение (`desktop`) |
| Java (`java`) | Linux (`linux`) | Расширения (`extension`) |
| JavaScript (`javascript`) | macOS (`macos`) | Игры (`games`) |
| Python (`python`) | tvOS (`tvos`) | Интернет вещей (`iot`) |
| Язык запросов (`querylanguage`) | Windows (`windows`) | Библиотека (`library`) |
| TypeScript (`typescript`) | Xbox (`xbox`) | Машинное обучение (`machinelearning`) |
| Visual Basic (`visualbasic`) | | Мобильное приложение (`mobile`) |
| | | Office (`office`) |
| | | Другое (`other`) |
| | | Служба (`service`) |
| | | Тест (`test`) |
| | | UWP (`uwp`) |
| | | Интернет (`web`) |

## <a name="example"></a>Пример

В следующем примере показаны метаданные шаблона проекта для приложения Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>csharp</ProjectType>
        <LanguageTag>csharp</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также

- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](creating-project-and-item-templates.md)
- [Настройка шаблонов проектов и элементов](customizing-project-and-item-templates.md)
- [Начало работы с шаблоном проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
