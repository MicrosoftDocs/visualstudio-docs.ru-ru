---
title: Добавление панели инструментов | Документация Майкрософт
description: Узнайте, как добавить панель инструментов, содержащую кнопки, привязанные к командам, в интегрированную среду разработки (IDE) Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e1b478041492bfb857c5497b6df5e2c4af9ad355
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094943"
---
# <a name="add-a-toolbar"></a>Добавление панели инструментов
В этом пошаговом руководстве показано, как добавить панель инструментов в интегрированную среду разработки Visual Studio.

 Панель инструментов представляет собой горизонтальную или вертикальную полосу, которая содержит кнопки, привязанные к командам. В зависимости от своей реализации панель инструментов в интегрированной среде разработки может быть перемещена, закреплена на любой стороне главного окна интегрированной среды разработки или находиться в начале других окон.

 Кроме того, пользователи могут добавлять команды на панель инструментов или удалять их из них с помощью диалогового окна « **Настройка** ». Как правило, панели в VSPackage могут настраиваться пользователем. Интегрированная среда разработки обрабатывает все настройки, а пакет VSPackage реагирует на команды. VSPackage не обязательно должен быть уверен в том, где физически находится команда.

 Дополнительные сведения о меню см. в разделе [команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Создание расширения с помощью панели инструментов
 Создайте проект VSIX с именем `IDEToolbar` . Добавьте шаблон пункта команды меню с именем **тулбартесткомманд**. Сведения о том, как это сделать, см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Создание панели инструментов для интегрированной среды разработки

1. В *тулбартесткоммандпаккаже. vsct* найдите раздел Symbols. В элементе GuidSymbol с именем Гуидтулбартесткоммандпаккажекмдсет добавьте объявления для панели инструментов и группы панелей инструментов, как показано ниже.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. В верхней части раздела команды создайте раздел меню. Добавьте элемент меню в раздел меню, чтобы определить панель инструментов.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     Панели инструментов не могут быть вложенными, как подменю. Поэтому нет необходимости назначать родительскую группу. Кроме того, не нужно задавать приоритет, так как пользователь может перемещать панели инструментов. Как правило, начальное размещение панели инструментов определяется программным способом, но последующие изменения, внесенные пользователем, сохраняются.

3. В разделе [группы](../extensibility/groups-element.md) после существующей записи группы определите элемент [группы](../extensibility/group-element.md) , содержащий команды для панели инструментов.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Нажмите кнопку, чтобы появилась кнопка на панели инструментов. В разделе кнопки замените родительский блок в кнопке на панель инструментов. Полученный блок кнопки должен выглядеть следующим образом:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     По умолчанию, если на панели инструментов нет команд, она не отображается.

5. Выполните сборку решения и запустите отладку. Должен отобразиться экспериментальный экземпляр.

6. Щелкните правой кнопкой мыши строку меню Visual Studio, чтобы получить список панелей инструментов. Выберите **панель инструментов для тестирования**.

7. Теперь панель инструментов должна отображаться в виде значка справа от значка найти в файлах. Щелкнув значок, вы увидите окно сообщения с текстом **тулбартесткоммандпаккаже. Внутри Идетулбар. Тулбартесткомманд. Менуитемкаллбакк ()**.

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
