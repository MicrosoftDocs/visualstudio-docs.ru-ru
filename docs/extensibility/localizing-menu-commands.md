---
title: Команды меню "локализация" | Документация Майкрософт
description: Узнайте, как предоставить локализованный текст для команд меню и панели инструментов, создав локализованные файлы vsct и локализованные файлы. resx для пакета VSPackage.
ms.custom: SEO-VS-2020
ms.date: 10/08/2019
ms.topic: how-to
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 141fb0d8ba6746e7d299984461fb3ca739d931d4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073265"
---
# <a name="localize-menu-commands"></a>Команды меню "локализовать"

Вы можете предоставить локализованный текст для команд меню и панели инструментов, создав локализованные файлы *. vsct* и локализованные файлы *. resx* для пакета VSPackage, а затем обновив файлы проекта, чтобы внести изменения.

Сведения о локализации процесса установки см. в разделе [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Локализация имен команд

В пакетах VSPackage команды меню и кнопки панели инструментов определены в файле *. vsct* .

1. В **Обозреватель решений** измените имя файла *vsct* с *filename. vsct* на *filename. en-US. vsct*.

2. Создайте копию *файла filename. en-US. vsct* для каждого локализованного языка.

    Назовите каждую копию *имя файла. { Locale}. vsct*, где *{locale}* — это конкретное имя языка и региональных параметров. Список значений имени языка и региональных параметров см. в разделе [идентификаторы языков, назначенные корпорацией Майкрософт](/windows/uwp/publish/supported-languages).

    Эти *имена файлов. Файлы locale. vsct* будут содержать локализованный текст меню для пакета.

3. Откройте каждое *имя файла. Файл locale. vsct* для локализации текста.

   1. Измените значения элементов [ButtonText](../extensibility/buttontext-element.md) в соответствии с конкретным языком.

   2. Если вы будете предоставлять локализованные значки, измените значения [растровых изображений](../extensibility/bitmap-element.md) , чтобы они указывали на целевые файлы.

      В следующем примере текст кнопки на английском и испанском языках отображается для команды, чтобы открыть окно инструментов обозревателя семейного дерева.

      [*FamilyTree. en-US. vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-ES. vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>
   ```

## <a name="localize-other-text-resources"></a>Локализация других текстовых ресурсов

Текстовые ресурсы, отличные от имен команд, определяются в файлах ресурсов (*RESX*).

1. Переименуйте *VSPackage. resx* в *VSPackage. en-US. resx*.

2. Создайте копию файла *VSPackage. en-US. resx* для каждого локализованного языка.

     Назовите каждую копию *VSPackage. { Locale}. resx*, где *{locale}* — конкретное имя языка и региональных параметров.

3. Переименуйте *Resources. resx* в *Resources. en-US. resx*.

4. Создайте копию файла *Resources. en-US. resx* для каждого локализованного языка.

     Назовите каждую копию *ресурсов. { Locale}. resx*, где *{locale}* — конкретное имя языка и региональных параметров.

5. Откройте каждый файл *. resx* , чтобы изменить строковые значения в соответствии с определенным языком и культурой. В следующем примере показано локализованное определение ресурса для заголовка окна инструментов.

     [*Resources. en-US. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Внедрение локализованных ресурсов в проект

Необходимо изменить файл *AssemblyInfo. CS* и файл проекта, чтобы включить локализованные ресурсы.

1. Из узла **Свойства** в **Обозреватель решений** откройте *AssemblyInfo. CS* или *AssemblyInfo. vb* в редакторе.

2. Добавьте следующую запись.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     При этом в качестве языка по умолчанию устанавливается английский язык (США).

3. Выгрузить проект.

4. Откройте файл проекта в редакторе.

5. В корневом `Project` элементе добавьте `PropertyGroup` элемент с `UICulture` элементом, который соответствует вашему языку по умолчанию.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     При этом в качестве языка и региональных параметров пользовательского интерфейса по умолчанию для элементов управления Windows Presentation Foundation (WPF) устанавливается английский язык США.

6. Нахождение `ItemGroup` элемента, содержащего `EmbeddedResource` элементы.

7. В `EmbeddedResource` элементе, который вызывает пакет *VSPackage. en-US. resx*, замените `ManifestResourceName` элемент на элемент, `LogicalName` для которого задано значение `VSPackage.en-US.Resources` , следующим образом:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Для каждого локализованного языка скопируйте  `EmbeddedResource` элемент для `VsPackage.en-US` и задайте атрибут **include** и элемент **LogicalName** копии в целевом языковом стандарте.

9. К каждому локализованному `VSCTCompile` элементу добавьте `ResourceName` элемент, указывающий на `Menus.ctmenu` , как показано в следующем примере:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Сохраните файл проекта и перезагрузите проект.

11. Выполните построение проекта.

     При этом создается Главная сборка и сборки ресурсов для каждого языка. Сведения о локализации процесса развертывания см. в разделе [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md) .

## <a name="see-also"></a>См. также

- [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)
- [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)
