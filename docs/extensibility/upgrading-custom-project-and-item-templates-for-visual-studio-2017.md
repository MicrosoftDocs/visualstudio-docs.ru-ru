---
title: Обновление пользовательских шаблонов проектов и элементов для Visual Studio 2017
titleSuffix: ''
description: Узнайте, как обновить пользовательский проект и шаблон элемента из предыдущих версий пакета SDK для Visual Studio для использования с Visual Studio 2017 и более поздними версиями.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 0d07af0a00ab840df8a9af437bcddc427f606948
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903064"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Обновление пользовательского шаблоны проектов и элементов для Visual Studio 2017

Начиная с Visual Studio 2017, Visual Studio обнаруживает шаблоны проектов и элементов, которые были установлены с расширением VSIX, или .msi по-другому в предыдущих версиях Visual Studio. Если вы владеете расширениями, использующими настраиваемые шаблоны проектов или элементов, необходимо обновить расширения. В этой статье объясняется, что необходимо сделать.

Это изменение затрагивает только Visual Studio 2017. Он не влияет на предыдущие версии Visual Studio.

Если вы хотите создать проект или шаблон элемента как часть расширения VSIX, см. раздел [Создание пользовательских шаблонов проектов и элементов](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Сканирование шаблона

В предыдущих версиях Visual Studio **devenv/setup** или **devenv/installvstemplates** проверил локальный диск для поиска шаблонов проектов и элементов. Начиная с Visual Studio 2017, сканирование выполняется только для расположения на уровне пользователя. Расположение на уровне пользователя по умолчанию — **%усерпрофиле%\документс \\<Visual Studio \> версии \\ \темплатес**. Это расположение используется для шаблонов, создаваемых командой **проект**  >  **Экспорт шаблонов...** , если в мастере выбран параметр **автоматически импортировать шаблон в Visual Studio** .

Для других (не пользователей) расположений необходимо включить файл манифеста (. встман), указывающий расположение и другие характеристики шаблона. Файл. встман создается вместе с VSTEMPLATE-файлом, используемым для шаблонов. Если вы устанавливаете расширение с помощью. VSIX, это можно сделать, выполнив повторную компиляцию расширения в Visual Studio 2017. Но если вы используете .msi, необходимо внести изменения вручную. Список действий, которые необходимо выполнить для внесения этих изменений, см. в разделе  **обновления для расширений, установленных с помощью .MSI** далее на этой странице.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Обновление расширения VSIX с помощью шаблонов проектов или элементов

1. Откройте решение в Visual Studio 2017. Вам будет предложено обновить код. Нажмите кнопку **OK**.

2. После завершения обновления может потребоваться изменить версию целевого объекта установки. В проекте VSIX откройте файл Source. extension. vsixmanifest и выберите вкладку **установки конечных объектов** . Если поле **диапазона версий** имеет значение **[14,0]**, щелкните **изменить** и измените его, включив Visual Studio 2017. Например, можно задать для него значение **[с диагональю 15,0]** , чтобы установить расширение для visual Studio 2015 или visual Studio 2017 либо до **[15,0]** , чтобы установить его только в Visual Studio 2017.

3. Выполните повторную компиляцию кода.

4. Закройте Visual Studio.

5. Установите VSIX.

6. Вы можете проверить обновление, выполнив следующие действия.

    1. Изменение сканирования файла активируется следующим ключом реестра:

         **REG Add hklm\software\microsoft\visualstudio\15.0\VSTemplate/v Дисаблетемплатесканнинг/t REG_DWORD/d 1/рег: 32**

    2. После добавления ключа выполните команду **devenv/installvstemplates**.

    3. Снова откройте Visual Studio. Шаблон должен находиться в ожидаемом расположении.

    > [!NOTE]
    > Шаблоны проектов расширяемости Visual Studio недоступны при наличии раздела реестра. Необходимо удалить раздел реестра (и повторно запустить **devenv/installvstemplates**), чтобы использовать его.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Другие рекомендации по развертыванию шаблонов проектов и элементов

- Старайтесь не использовать ZIP-файлы шаблонов. Сжатые ZIP-файлы шаблонов необходимо распаковать, чтобы извлечь ресурсы и содержимое, поэтому они будут тем обходятся для использования. Вместо этого следует развертывать шаблоны проектов и элементов в виде отдельных файлов в собственном каталоге для ускорения инициализации шаблона. Для расширений VSIX задачи сборки пакета SDK будут автоматически распаковать любой ZIP-шаблон при создании VSIX-файла.

- Не используйте записи идентификатора пакета или ресурса для имени шаблона, описания, значка или предварительной версии, чтобы избежать загрузки ненужной сборки ресурсов во время обнаружения шаблона. Вместо этого можно использовать локализованные манифесты для создания записи шаблона для каждого языкового стандарта, использующего локализованные имена или свойства.

- Если вы включаете шаблоны в качестве файловых элементов, то создание манифеста может не дать ожидаемых результатов. В этом случае потребуется добавить созданный вручную манифест в проект VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Изменения в файлах в шаблонах проектов и элементов
Мы покажем различия между версиями файлов шаблонов Visual Studio 2015 и Visual Studio 2017, чтобы можно было правильно создать файлы.

 Ниже приведен файл Project. vstemplate по умолчанию, созданный Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 Ниже приведен встман-файл (его можно найти в каталоге манифеста проекта VSIX), который привел к перестроению проекта VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Сведения, предоставленные элементом [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) , остаются неизменными. **\<VSTemplateContainer>** Элемент указывает на VSTEMPLATE файл для связанного шаблона.

 Ниже приведен файл Default. vstemplate элемента, созданный Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 Ниже приведен встман-файл (его можно найти в каталоге манифеста проекта VSIX), который привел к перестроению проекта VSIX:

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

 Информация, предоставленная **\<TemplateData>** элементом, остается неизменной. **\<VSTemplateContainer>** Элемент указывает на VSTEMPLATE файл для связанного шаблона.

 Дополнительные сведения о различных элементах встман-файла см. в разделе [Справочник по схеме манифеста шаблона Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Обновления расширений, установленных с помощью .MSI

Некоторые расширения на основе MSI развертывают шаблоны в общих расположениях шаблонов, например в следующих каталогах:

- **\<Visual Studio installation directory>\Common7\IDE \\<прожекттемплатес/ItemTemplate\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<ExtensionName \> \\<проект/ItemTemplate\>**

Если расширение выполняет развертывание на основе MSI, необходимо создать манифест шаблона вручную и убедиться, что он включен в установку расширения. Сравните приведенные выше примеры встман и ссылку на [схему манифеста шаблона Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

Создайте отдельные манифесты для шаблонов проектов и элементов, и они должны указывать на каталог корневого шаблона, как указано выше. Создайте один манифест для каждого расширения и языкового стандарта.

## <a name="see-also"></a>См. также

- [Устранение неполадок обнаружения шаблонов](troubleshooting-template-discovery.md)
- [Создание пользовательских шаблонов проектов и элементов](creating-custom-project-and-item-templates.md)
