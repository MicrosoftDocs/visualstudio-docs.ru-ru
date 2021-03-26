---
title: Создание многократно используемых групп кнопок | Документация Майкрософт
description: Узнайте, как создать группу команд, которая представляет собой набор команд, которые отображаются вместе в меню или на панели инструментов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6b9c0bd759083a0d0d053133cc9f2d4d03a52389
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055743"
---
# <a name="create-reusable-groups-of-buttons"></a>Создание многократно используемых групп кнопок
Группа команд — это набор команд, которые всегда отображаются вместе в меню или на панели инструментов. Любую группу команд можно использовать повторно, назначив ее другим родительским меню в разделе CommandPlacements файла *vsct* .

 Группы команд обычно содержат кнопки, но они также могут содержать другие меню или поля со списком.

## <a name="to-create-a-reusable-group-of-buttons"></a>Создание многократно используемой группы кнопок

1. Создайте проект VSIX с именем `ReusableButtons` . Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. При открытии проекта добавьте пользовательский шаблон элемента команды с именем **реусаблекомманд**. В **Обозреватель решений** щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить**  >  **новый элемент**. В диалоговом окне **Добавление нового элемента** перейдите в раздел расширяемость **Visual C#**  >   и выберите пункт **пользовательская команда**. В поле **имя** в нижней части окна измените имя файла команд на *реусаблекомманд. CS*.

3. В файле *vsct* перейдите к разделу символы и найдите элемент GuidSymbol, содержащий группы и команды для проекта. Он должен называться Гуидреусаблекоммандпаккажекмдсет.

4. Добавьте IDSymbol для каждой кнопки, которая будет добавлена в группу, как показано в следующем примере.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     По умолчанию шаблон элемента команды создает группу с именем **мименуграуп** и кнопку с указанным именем, а также запись IDSymbol для каждого из них.

5. В разделе Groups (группы) создайте элемент Group с теми же идентификаторами GUID и ID, что и в разделе символы. Можно также использовать существующую группу или использовать запись, предоставленную шаблоном команды, как показано в следующем примере. Эта группа отображается в меню " **Сервис** "

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Создание группы кнопок для повторного использования

1. Вы можете поместить команду или меню в группу либо с помощью группы в качестве родителя в определении команды или меню, либо путем помещения команды или меню в группу с помощью раздела CommandPlacements.

     В разделе кнопки определите кнопку, которая имеет свою родительскую группу, или используйте кнопку, предоставленную шаблоном пакета, как показано в следующем примере.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Если кнопка должна появляться в нескольких группах, создайте запись для нее в разделе CommandPlacements, который должен быть помещен после раздела Commands. Задайте атрибуты GUID и ID элемента CommandPlacement, чтобы они соответствовали параметрам кнопки, которую требуется разместить, а затем задайте идентификатор GUID и идентификатор родительского элемента для целевой группы, как показано в следующем примере.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Значение поля Priority определяет расположение команды в новой группе команд. Приоритеты, заданные в элементе CommandPlacement, переопределяют эти наборы в определении элемента. Команды с более низкими значениями приоритета отображаются перед командами, имеющими более высокие значения приоритета. Дублирование значений приоритета разрешено, но относительное расположение команд с одинаковым значением приоритета не гарантируется, так как порядок, в котором команда **devenv/setup** создает окончательный интерфейс из реестра, может быть неединообразным.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Помещение многократно используемой группы кнопок в меню

1. Создайте запись в `CommandPlacements` разделе. Задайте идентификатор GUID и идентификатор `CommandPlacement` элемента для своей группы и задайте родительский идентификатор GUID и идентификатор для целевого расположения.

    Раздел CommandPlacements следует поместить сразу после раздела Commands:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Группу команд можно включить в несколько меню. Родительское меню может быть созданным, одним из которых является [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (как описано в *шеллкмддеф. vsct* или *шаредкмддеф. vsct*) или одним, определенным в другом пакете VSPackage. Количество родительских слоев не ограничено, пока родительское меню в конечном итоге подключается к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или к контекстному меню, которое отображается пакетом VSPackage.

    В следующем примере группа помещается на панель инструментов **Обозреватель решений** , справа от других кнопок.

   ```xml
   <CommandPlacements>
       <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">
         <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
       </CommandPlacement>
   </CommandPlacements>
   ```

   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"
         priority="0x605">
       <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />
     </CommandPlacement>
   </CommandPlacements>

   ```
