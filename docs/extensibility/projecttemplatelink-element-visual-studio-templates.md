---
title: Элемент ProjectTemplateLink (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об <element> элементе и о том, как он указывает путь к VSTEMPLATE-файлу одного проекта в многопроектном шаблоне.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8f1dc03239481e59d26445161dcd7c0137b18d75
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068665"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>Элемент ProjectTemplateLink (шаблоны Visual Studio)
Указывает путь к *VSTEMPLATE* -файлу одного проекта в многопроектном шаблоне.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>
 \<ProjectTemplateLink>
ни \<VSTemplate>
 \<TemplateContent>
 \<ProjectCollection>
 \<SolutionFolder>
 \<ProjectTemplateLink>

## <a name="syntax"></a>Синтаксис

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`ProjectName`|Необязательный атрибут.<br /><br /> Задает имя каждого отдельного проекта в многопроектном шаблоне. Диалоговое окно " **Новый проект** " не может назначать имена отдельным проектам.|
|`CopyParameters`|Включает копирование всех переменных в шаблоне основной группы в каждый из связанных шаблонов.<br /><br /> Параметры в связанных шаблонах имеют префикс `"$ext_*$"`. Например, если в шаблоне родительской группы параметр `$projectname$` имеет значение **ExampleProject1**, то когда связанный шаблон станет выполненным, он получает параметр `$ext_projectname$` , который является копией `$projectname$` параметра из шаблона родительской группы.<br /><br /> Это позволяет связанным шаблонам совместно использовать некоторые общие параметры, которые можно удобным образом создавать в шаблоне родительской группы.<br /><br /> Этот атрибут является необязательным и для него автоматически устанавливается значение по умолчанию `false`, если он не включен.<br /><br /> Представлено в обновлении 2 для Visual Studio 2013. Сведения о правильной версии продукта см. [в разделе ссылочные сборки, поставляемые в составе пакета SDK для Visual Studio 2013 с обновлением 2](/previous-versions/dn632168(v=vs.120)).|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Указывает организацию и содержимое многопроектных шаблонов.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Группирует проекты в многопроектных шаблонах.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Этот текст указывает путь к *VSTEMPLATE* – файлу шаблона.

## <a name="remarks"></a>Remarks
 Многопроектные шаблоны используются в качестве контейнера для двух или нескольких проектов. `ProjectTemplateLink`Элемент используется для указания расположения *VSTEMPLATE* -файла для одного из проектов в шаблоне. *VSTEMPLATE* -файл многопроектного шаблона содержит `ProjectTemplateLink` по одному элементу для каждого проекта в шаблоне. Дополнительные сведения о многопроектных шаблонах см. [в разделе как создавать Многопроектные шаблоны](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Пример
 В этом примере показан простой корневой *VSTEMPLATE* -файл с несколькими проектами. В этом примере шаблон содержит два проекта `My Windows Application` и `My Class Library`. Атрибут `ProjectName` элемента `ProjectTemplateLink` задает имя, которое [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] назначает данному проекту. Если `ProjectName` атрибут не существует, в качестве имени проекта используется имя *VSTEMPLATE* -файла.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Практическое руководство. Создание многопроектных шаблонов](../ide/how-to-create-multi-project-templates.md)