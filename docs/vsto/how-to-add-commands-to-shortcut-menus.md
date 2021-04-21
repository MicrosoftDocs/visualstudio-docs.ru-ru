---
title: Как добавить команды в контекстные меню
description: Узнайте, как добавлять команды в контекстное меню в приложении Office с помощью надстройки VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 276dc7b8094c495a1b3896a4a93a068b1005c8d5
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828453"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Как добавить команды в контекстные меню
  В этом разделе показано, как добавлять команды в контекстное меню в приложении Office с помощью надстройки VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Добавление команд в контекстные меню в Office

1. Добавьте элемент **Лента (XML)** в проект уровня документа или надстройки VSTO. Дополнительные сведения см. [в разделе инструкции. Приступая к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md). В

2. В **обозревателе решений** выберите файл **ThisAddIn.cs** или **ThisAddIn.vb**.

3. В строке меню выберите **Вид** > **Код**.

     Этот файл класса **ThisAddin** откроется в редакторе кода.

4. Добавьте следующий код в класс **ThisAddin** . Этот код переопределяет метод `CreateRibbonExtensibilityObject` и возвращает XML-класс ленты в приложение Office.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb" id="Snippet1":::

5. В **обозревателе решений** выберите XML-файл ленты. По умолчанию XML-файл ленты имеет имя *Ribbon1.xml*.

6. В строке меню выберите **Вид** > **Код**.

     XML-файл ленты открывается в редакторе кода.

7. В редакторе кода добавьте XML, описывающий контекстное меню и элемент управления, который требуется добавить в контекстное меню.

     В следующем примере элементы управления "кнопка", "меню" и "коллекция" добавляются в контекстное меню для документа Word. Идентификатор элемента управления этого контекстного меню — ContextMenuText. Полный список ИДЕНТИФИКАТОРов элементов управления ярлыков Office 2010 см. в разделе [файлы справки office 2010: идентификаторы элементов управления пользовательского интерфейса Fluent Office](https://www.microsoft.com/download/details.aspx?id=6627).

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />
          <menu id="MySubMenu" label="My Submenu" >
            <button id="MyButton2" label="Button on submenu" />
          </menu>
          <gallery id="galleryOne" label="My Gallery">
            <item id="item1" imageMso="HappyFace" />
            <item id="item2" imageMso="HappyFace" />
            <item id="item3" imageMso="HappyFace" />
            <item id="item4" imageMso="HappyFace" />
          </gallery>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

8. В **обозревателе решений**, выберите файл **MyRibbon.cs** или **MyRibbon.vb**.

9. Добавьте метод обратного вызова в `Ribbon1` класс для каждого элемента управления, который требуется обменять.

     Следующий метод обратного вызова обрабатывает кнопку **My Button** . Этот код добавляет строку в активный документ в текущем положении курсора.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs" id="Snippet2":::

## <a name="see-also"></a>См. также статью
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Пошаговое руководство. создание контекстных меню для закладок](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Настройка контекстных меню в Office 2010](/previous-versions/office/developer/office-2010/ee691832(v=office.14))
