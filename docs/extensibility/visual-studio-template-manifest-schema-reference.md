---
title: Справочник по схеме манифеста шаблона Visual Studio | Документация Майкрософт
description: Эта ссылка на схему описывает формат файлов манифеста шаблона Visual Studio, созданных для шаблонов проектов и элементов Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 259d2dd050f4681053f331bfd4ec39dd7b214059
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905388"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Справочник по схеме манифеста шаблона Visual Studio
Эта схема описывает формат файлов манифеста шаблона Visual Studio (*. встман*), которые создаются для шаблонов проектов и элементов Visual Studio. Схема также описывает расположение и другие релевантные сведения о шаблоне.

 . Поскольку существуют отдельные каталоги элементов и шаблонов проектов, манифесты элементов и проектов никогда не должны быть смешанными.

> [!IMPORTANT]
> Этот манифест доступен начиная с Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Встемплатеманифест, элемент
 Корневой элемент манифеста.

### <a name="attributes"></a>Атрибуты

- **Версия**: строка, представляющая версию манифеста шаблона. Обязательный.

- **Языковой стандарт**: строка, представляющая языковой стандарт или языковые стандарты манифеста шаблона. Значение языкового стандарта применяется ко всем шаблонам. Для каждого языкового стандарта необходимо использовать отдельный манифест. Необязательный элемент.

### <a name="child-elements"></a>Дочерние элементы

- **Встемплатеконтаинер** Используемых.

- **Встемплатедир** Используемых.

### <a name="parent-element"></a>Родительский элемент
 Отсутствует.

## <a name="vstemplatecontainer"></a>встемплатеконтаинер
 Контейнер элементов манифеста шаблона. Манифест содержит один контейнер шаблона для каждого определяемого им шаблона.

### <a name="attributes"></a>Атрибуты
 **Встемплатетипе**: строковое значение, указывающее тип шаблона ( `"Project"` , `"Item"` или `"ProjectGroup"` ). Обязательно

### <a name="child-elements"></a>Дочерние элементы

- **Релативепасондиск**: относительный путь к файлу шаблона на диске. Это расположение также определяет расположение шаблона в дереве шаблонов, которое отображается в диалоговом окне **Новый проект** или **новый элемент** . Для шаблонов, развертываемых как каталог и отдельные файлы, этот путь относится к каталогу, содержащему файлы шаблонов. Для шаблонов, развернутых в виде файла *.zip* , этот путь должен быть путем к файлу *.zip* .

- * * Встемплатехеадер: элемент [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) , описывающий заголовок.

### <a name="parent-element"></a>Родительский элемент
 **встемплатеманифест**

## <a name="vstemplatedir"></a>встемплатедир
 Описывает каталог, в котором находится шаблон. Манифест может содержать несколько записей **встемплатедир** для предоставления локализованного имени и порядка сортировки для каталогов, чтобы управлять их внешним видом в дереве категорий шаблонов.

 Из-за их разработки записи **встемплатедир** должны отображаться только в манифестах, заданных не заданным языковым стандартом.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

- **RelativePath**: путь к шаблону. В пути может быть только одна запись, поэтому первый из них будет выиграть для всех манифестов.

- **LocalizedName**: элемент **намедескриптионикон** , указывающий локализованное имя. Необязательный элемент.

- **SortOrder**: строка, указывающая порядок сортировки. Необязательный элемент.

- **Парентфолдероверриденаме**: переопределенное имя родительской папки. Необязательный элемент. Этот элемент имеет атрибут **Name** , который представляет собой строковое значение, указывающее имя.

### <a name="parent-element"></a>Родительский элемент
 **встемплатеманифест**

## <a name="namedescriptionicon"></a>намедескриптионикон
 Задает имя и описание, возможно, для локализованных шаблонов. См. **LocalizedName** выше.

### <a name="attributes"></a>Атрибуты

- **Package**— строковое значение, указывающее пакет. Необязательный элемент.

- **ID**: строковое значение, указывающее идентификатор. Необязательный элемент.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-element"></a>Родительский элемент
 **LocalizedName**

## <a name="examples"></a>Примеры
 Ниже приведен пример кода проекта template *. встман* .

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Следующий код является примером файла шаблона элемента *. встман* .

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```
