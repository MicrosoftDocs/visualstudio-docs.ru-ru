---
title: Локализация пакетов VSIX | Документация Майкрософт
description: Узнайте, как локализовать пакет VSIX, создав файл Extension. всикслангпакк для каждого целевого языка и поместив их в соответствующую папку.
ms.custom: SEO-VS-2020
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d2e297484e89f1ae2cfb9f2be7af25f1fe92714
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073226"
---
# <a name="localizing-vsix-packages"></a>Локализация пакетов VSIX

Вы можете локализовать пакет VSIX, создав файл *Extension. всикслангпакк* для каждого целевого языка и поместив их в соответствующую папку. При установке локализованного пакета локализованное имя расширения отображается вместе с локализованным описанием. Если указать локализованный файл лицензии или URL-адрес, указывающий на локализованные сведения, они также будут отображаться.

Если содержимое пакета VSIX содержит пакет VSPackage, который добавляет команды меню или другой пользовательский интерфейс, см. раздел [команды меню Localize](../extensibility/localizing-menu-commands.md) для получения сведений о локализации новых элементов пользовательского интерфейса.

## <a name="directory-structure"></a>Структура каталогов

 Когда пользователь устанавливает расширение, **расширения и обновления** проверяют верхний уровень пакета VSIX для папки, имя которой соответствует языковому стандарту Visual Studio конечного компьютера. Если **расширения и обновления** обнаруживают *всикслангпакк* -файл в папке, он заменяет локализованные значения в этом файле соответствующими значениями в *vsixmanifest* -файле. Эти значения отображаются при установке расширения. В следующем примере показана структура каталогов для пакета VSIX, который локализован на Испанский (ES-ES) и французский (fr-FR).

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> Поддерживаемые VSIX шаблоны проектов в [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Создайте манифест VSIX и назовите его *source. extension. vsixmanifest*. Когда Visual Studio выполняет сборку проекта, он копирует содержимое этого файла в Extension. VsixManifest в пакете VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Файл Extension. всикслангпакк

Файл *Extension. всикслангпакк* соответствует [схеме языкового пакета VSIX 2,0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Эта схема имеет объект `PackageLanguagePackManifest` , за которым сразу следует `Metadata` дочерний элемент. Элемент Metadata может содержать до 6 дочерних элементов,,,,, `DisplayName` `Description` `MoreInfo` `License` `ReleaseNotes` и `Icon` . Эти дочерние элементы соответствуют `DisplayName` `Description` `MoreInfo` `License` `ReleaseNotes` дочерним элементам,,,, и для `Icon` `Metadata` элемента файла *Extension. vsixmanifest* .

При создании файла всикслангпакк необходимо задать `Include in Vsix` для свойства значение `true` . В противном случае локализованный текст установки будет проигнорирован.

### <a name="to-set-the-include-in-vsix-property"></a>Задание свойства include в VSIX

1. В **Обозреватель решений** щелкните правой кнопкой мыши файл Extension. всикслангпакк и выберите пункт **свойства**.

2. В **сетке свойств** щелкните **включить в VSIX** и присвойте ему значение `true` .

## <a name="example"></a>Пример

### <a name="description"></a>Описание

В следующем примере показаны соответствующие части файла *Extension. vsixmanifest* . Файл также содержит соответствующий файл *Extension. всикслангпакк* для испанского языка. Значения из языкового пакета заменяют значения из манифеста, если для языка Visual Studio целевого компьютера задано значение испанский.

### <a name="code"></a>Код

- [*Extension. vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*Extension. всикслангпакк*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Справочник по схеме языкового пакета VSIX 2,0](vsix-language-pack-schema-2-0-reference.md)|Языковой пакет VSIX описывает сведения о локализации VSIX-файла развертывания.|
|[Анатомия пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Описывает структуру и содержимое пакета VSIX.|
|[Команды меню "локализовать"](../extensibility/localizing-menu-commands.md)|Показывает, как локализовать другие текстовые ресурсы в расширении.|
