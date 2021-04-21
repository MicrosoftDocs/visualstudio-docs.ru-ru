---
title: Пошаговое руководство. создание контекстных меню для закладок
description: Узнайте, как создавать контекстные меню для элементов управления Bookmark в настройке уровня документа для Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 48381d452b0c67a34581092a47896aba60e7125c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826308"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Пошаговое руководство. создание контекстных меню для закладок
  В этом пошаговом руководстве показано, как создать контекстное меню для <xref:Microsoft.Office.Tools.Word.Bookmark> элементов управления в настройке уровня документа для Word. Когда пользователь щелкает правой кнопкой мыши текст закладки, появляется контекстное меню с параметрами пользователя для форматирования текста.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- [Создайте проект](#BKMK_CreateProject).

- [Добавление текста и закладок в документ](#BKMK_addtextandbookmarks).

- [Добавьте команды в контекстное меню](#BKMK_AddCmndsShortMenu).

- [Форматирование текста в закладке](#BKMK_formattextbkmk).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a><a name="BKMK_CreateProject"></a> Создание проекта
 Первым шагом является создание проекта документа Word в Visual Studio.

### <a name="to-create-a-new-project"></a>Создание нового проекта

- Создайте проект документа Word с именем **Мое контекстное меню закладки**. В мастере выберите **создать новый документ**. Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет новый документ Word в конструкторе и добавит проект **контекстного меню "Мои закладки** " в **Обозреватель решений**.

## <a name="add-text-and-bookmarks-to-the-document"></a><a name="BKMK_addtextandbookmarks"></a> Добавление текста и закладок в документ
 Добавьте в документ некоторый текст, а затем добавьте две перекрывающиеся закладки.

### <a name="to-add-text-to-your-document"></a>Добавление текста в документ

- В документе, который отображается в конструкторе проекта, введите следующий текст.

     **Это пример создания контекстного меню при щелчке правой кнопкой мыши по тексту в закладке.**

### <a name="to-add-a-bookmark-control-to-your-document"></a>Добавление элемента управления Bookmark в документ

1. В **области элементов** на вкладке **элементы управления Word** перетащите <xref:Microsoft.Office.Tools.Word.Bookmark> элемент управления в документ.

    Откроется диалоговое окно **Добавление элемента управления Bookmark** .

2. Выберите слова «Создание контекстного меню при щелчке текста правой кнопкой мыши» и нажмите кнопку « **ОК**».

    `bookmark1` добавляется в документ.

3. Добавьте еще один <xref:Microsoft.Office.Tools.Word.Bookmark> элемент управления в слова «щелкните правой кнопкой мыши текст закладки».

    `bookmark2` добавляется в документ.

   > [!NOTE]
   > Слова "щелкните текст правой кнопкой мыши" находятся в `bookmark1` и `bookmark2` .

   При добавлении закладки в документ во время разработки <xref:Microsoft.Office.Tools.Word.Bookmark> создается элемент управления. Можно программировать для нескольких событий закладки. Можно написать код в <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> событии закладки, чтобы при щелчке правой кнопкой мыши по тексту в закладке появляется контекстное меню.

## <a name="add-commands-to-a-shortcut-menu"></a><a name="BKMK_AddCmndsShortMenu"></a> Добавление команд в контекстное меню
 Добавьте кнопки в контекстное меню, которое появляется при щелчке правой кнопкой мыши по документу.

### <a name="to-add-commands-to-a-shortcut-menu"></a>Добавление команд в контекстное меню

1. Добавьте в проект элемент **XML ленты** . Дополнительные сведения см. [в разделе инструкции. Приступая к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. В **Обозреватель решений** выберите **ThisDocument. CS** или **ThisDocument. vb**.

3. В строке меню выберите **Вид** > **Код**.

     В редакторе кода откроется файл класса **ThisDocument** .

4. Добавьте следующий код в класс **ThisDocument** . Этот код переопределяет метод Креатериббонекстенсибилитйобжект и возвращает класс XML ленты в приложение Office.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet1":::

5. В **обозревателе решений** выберите XML-файл ленты. По умолчанию XML-файл ленты называется Ribbon1.xml.

6. В строке меню выберите **Вид** > **Код**.

     XML-файл ленты открывается в редакторе кода.

7. В редакторе кода замените содержимое XML-файла ленты следующим кодом.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="BoldButton" label="Bold" onAction="ButtonClick"
               getVisible="GetVisible" />
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"
              getVisible="GetVisible"/>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

     Этот код добавляет две кнопки в контекстное меню, которое появляется при щелчке правой кнопкой мыши по документу.

8. В **Обозреватель решений** щелкните правой кнопкой мыши `ThisDocument` и выберите пункт **Просмотреть код**.

9. Объявите следующие переменные и переменную закладки на уровне класса.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet2":::

10. В **Обозреватель решений** выберите файл кода ленты. По умолчанию файл кода ленты называется **Ribbon1. CS** или **Ribbon1. vb**.

11. В строке меню выберите **Вид** > **Код**.

     Файл кода ленты открывается в редакторе кода.

12. В файле кода ленты добавьте следующий метод. Это метод обратного вызова для двух кнопок, добавленных в контекстное меню документа. Этот метод определяет, отображаются ли эти кнопки в контекстном меню. Кнопки Полужирный и курсив отображаются, только если щелкнуть правой кнопкой мыши текст в закладке.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb" id="Snippet5":::

## <a name="format-the-text-in-the-bookmark"></a><a name="BKMK_formattextbkmk"></a> Форматирование текста в закладке

### <a name="to-format-the-text-in-the-bookmark"></a>Форматирование текста закладки

1. В файле кода ленты добавьте `ButtonClick` обработчик событий, чтобы применить форматирование к закладке.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb" id="Snippet6":::

2. **Обозреватель решений** выберите **ThisDocument. CS** или **ThisDocument. vb**.

3. В строке меню выберите **Вид** > **Код**.

     В редакторе кода откроется файл класса **ThisDocument** .

4. Добавьте следующий код в класс **ThisDocument** .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet3":::

    > [!NOTE]
    > Необходимо написать код, обрабатывающий случаи, когда закладки перекрываются. Если нет, по умолчанию код будет вызываться для всех закладок в выделенном фрагменте.

5. В C# необходимо добавить обработчики событий для элементов управления Bookmark в <xref:Microsoft.Office.Tools.Word.Document.Startup> событие. Дополнительные сведения о создании обработчиков событий см. в разделе [как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet4":::

## <a name="test-the-application"></a>Тестирование приложения
 Протестируйте документ, чтобы убедиться, что пункты меню полужирный и курсив отображаются в контекстном меню при щелчке правой кнопкой мыши по тексту в закладке и что текст имеет правильный формат.

### <a name="to-test-your-document"></a>Проверка документа

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Щелкните правой кнопкой мыши первую закладку и выберите пункт **полужирный**.

3. Убедитесь, что весь текст в `bookmark1` отформатирован полужирным шрифтом.

4. Щелкните правой кнопкой мыши текст, в котором разкрываются закладки, и выберите пункт **курсив**.

5. Убедитесь, что весь текст в `bookmark2` задается курсивом, а только часть текста в `bookmark1` этой области пересекается `bookmark2` курсивом.

## <a name="next-steps"></a>Дальнейшие действия
 Ниже приводятся некоторые из возможных последующих задач.

- Напишите код для реагирования на события элементов управления ведущего приложения в Excel. Дополнительные сведения см. в разделе [Пошаговое руководство. Программирование для событий элемента управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

- Используйте флажок, чтобы изменить форматирование закладки. Дополнительные сведения см. в разделе [Пошаговое руководство. изменение форматирования документа с помощью элементов управления CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>См. также статью
- [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Элемент управления Bookmark](../vsto/bookmark-control.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
