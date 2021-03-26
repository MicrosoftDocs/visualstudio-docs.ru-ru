---
title: Добавление меню в строку меню Visual Studio | Документация Майкрософт
description: Узнайте, как добавить меню в строку меню интегрированной среды разработки Visual Studio (IDE).
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 22ce9bc00f24278fd2c0533052d7bd5e944b1ebf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078348"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Добавление меню в строку меню Visual Studio

В этом пошаговом руководстве показано, как добавить меню в строку меню интегрированной среды разработки Visual Studio (IDE). Строка меню интегрированной среды разработки содержит категории меню, такие как **файл**, **Правка**, **вид**, **окно** и **Справка**.

Перед добавлением нового меню в строку меню Visual Studio рассмотрите возможность размещения команд в существующем меню. Дополнительные сведения о размещении команд см. в разделе [меню и команды для Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Меню объявляются в файле *vsct* проекта. Дополнительные сведения о меню и файлах *vsct* см. в разделе [команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md).

Выполнив это пошаговое руководство, можно создать меню **Test (тест** ), содержащее одну команду.

:::moniker range=">=vs-2019"
> [!NOTE]
> Начиная с Visual Studio 2019, меню верхнего уровня, задействованное расширениями, помещаются в меню **расширения** .
:::moniker-end

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Создание проекта VSIX с пользовательским шаблоном элемента команды

1. Создайте проект VSIX с именем `TopLevelMenu` . Шаблон проекта VSIX можно найти в диалоговом окне " **Новый проект** ", выполнив поиск по слову "VSIX".  Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

::: moniker range="vs-2017"

2. При открытии проекта добавьте пользовательский шаблон элемента команды с именем **тесткомманд**. В **Обозреватель решений** щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить**  >   **новый элемент**. В диалоговом окне **Добавление нового элемента** перейдите в раздел **Visual C#/Extensibility** и выберите пункт **пользовательская команда**. В поле **имя** в нижней части окна измените имя файла команд на *тесткомманд. CS*.

::: moniker-end

::: moniker range=">=vs-2019"

2. При открытии проекта добавьте пользовательский шаблон элемента команды с именем **тесткомманд**. В **Обозреватель решений** щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить**  >   **новый элемент**. В диалоговом окне **Добавление нового элемента** перейдите в раздел **Visual C#/Extensibility** и выберите **команду**. В поле **имя** в нижней части окна измените имя файла команд на *тесткомманд. CS*.

::: moniker-end

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Создание меню в строке меню интегрированной среды разработки

::: moniker range="vs-2017"

1. В **Обозреватель решений** откройте *тесткоммандпаккаже. vsct*.

    В конце файла находится `<Symbols>` узел, содержащий несколько `<GuidSymbol>` узлов. В узле с именем `guidTestCommandPackageCmdSet` добавьте новый символ, как показано ниже.

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Создайте пустой `<Menus>` узел в `<Commands>` узле непосредственно перед `<Groups>` . В `<Menus>` узле добавьте `<Menu>` узел, как показано ниже.

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`Значения и в `id` меню указывают набор команд и конкретное меню в наборе команд.

    `guid`Значения и `id` родительского положения меню в разделе строки меню Visual Studio, содержащей меню средства и надстройки.

    `<ButtonText>`Элемент указывает, что текст должен отображаться в пункте меню.

3. В `<Groups>` разделе найдите `<Group>` и измените `<Parent>` элемент, чтобы он указывал на только что добавленное меню:

   ```xml
   <Groups>
       <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    В результате группа становится частью нового меню.

::: moniker-end

::: moniker range=">=vs-2019"

1. В **Обозреватель решений** откройте *топлевелменупаккаже. vsct*.

    В конце файла находится `<Symbols>` узел, содержащий несколько `<GuidSymbol>` узлов. В узле с именем `guidTopLevelMenuPackageCmdSet` добавьте новый символ, как показано ниже.

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Создайте пустой `<Menus>` узел в `<Commands>` узле непосредственно перед `<Groups>` . В `<Menus>` узле добавьте `<Menu>` узел, как показано ниже.

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`Значения и в `id` меню указывают набор команд и конкретное меню в наборе команд.

    `guid`Значения и `id` родительского положения меню в разделе строки меню Visual Studio, содержащей меню средства и надстройки.

    `<ButtonText>`Элемент указывает, что текст должен отображаться в пункте меню.

3. В `<Groups>` разделе найдите `<Group>` и измените `<Parent>` элемент, чтобы он указывал на только что добавленное меню:

   ```xml
   <Groups>
       <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    В результате группа становится частью нового меню.

::: moniker-end

4. В `<Buttons>` разделе найдите `<Button>` узел. Затем в `<Strings>` узле измените `<ButtonText>` элемент на `Test Command` .

    Обратите внимание, что [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] шаблон пакета создал `Button` элемент, для которого его родительский объект имеет значение `MyMenuGroup` . В результате эта команда отображается в меню.

## <a name="build-and-test-the-extension"></a>Сборка и тестирование расширения

1. Выполните сборку решения и запустите отладку. Должен отобразиться экземпляр экспериментального экземпляра.

::: moniker range="vs-2017"

2. Строка меню в экспериментальном экземпляре должна содержать меню **тестов** .

::: moniker-end

::: moniker range=">=vs-2019"

2. Меню **расширения** в экспериментальном экземпляре должно содержать меню **тестов** .

::: moniker-end

3. В меню **тест** выберите пункт **команда теста**.

    Появится окно сообщения с сообщением "Тесткомманд in Топлевелмену. Тесткомманд. Менуитемкаллбакк ()".

## <a name="see-also"></a>См. также

- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
