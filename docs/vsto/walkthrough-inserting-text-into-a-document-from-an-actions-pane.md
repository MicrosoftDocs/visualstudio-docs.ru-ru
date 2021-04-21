---
title: Пошаговое руководство. Вставка текста в документ из панели действий
description: Создание панели действий в документе Microsoft Word. Сведения о том, что панель действий содержит два элемента управления, которые собираются входные данные и затем отправляют текст в документ.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1ac42954e32b30a293abbe031218213948fb103a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824982"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Пошаговое руководство. Вставка текста в документ из панели действий
  В этом пошаговом руководстве показано, как создать панель действий в Microsoft Office документе Word. Панель действий содержит два элемента управления, которые собираются входные данные и затем отправляют текст в документ.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- Разработка интерфейса с помощью элементов управления Windows Forms в элементе управления панели действий.

- Отображать панель действий при открытии приложения.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Создание проекта
 Первым шагом является создание документа Word.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект документа Word с именем **Моя базовая панель действий**. В мастере выберите **создать новый документ**. Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет новый документ Word в конструкторе и добавит в **Обозреватель решений** проект **панели "Мои базовые действия** ".

## <a name="add-text-and-bookmarks-to-the-document"></a>Добавление текста и закладок в документ
 Панель действий будет передавать текст в закладки в документе. Чтобы разработать документ, введите текст для создания базовой формы.

### <a name="to-add-text-to-your-document"></a>Добавление текста в документ

1. Введите следующий текст в документ Word:

    **21 марта 2008 г.**

    **Имя**

    **Адрес**

    **Это пример базовой панели действий в Word.**

   В документ можно добавить <xref:Microsoft.Office.Tools.Word.Bookmark> элемент управления, перетащив его из **панели элементов** в Visual Studio или с помощью диалогового окна « **Закладка** » в Word.

### <a name="to-add-a-bookmark-control-to-your-document"></a>Добавление элемента управления Bookmark в документ

1. Перетащите элемент управления из вкладки **элементы управления Word** **панели элементов** в <xref:Microsoft.Office.Tools.Word.Bookmark> документ.

     Откроется диалоговое окно **Добавление элемента управления Bookmark** .

2. Выберите **имя** слова, не выбрав знак абзаца, и нажмите кнопку **ОК**.

    > [!NOTE]
    > Знак абзаца должен находиться за пределами закладки. Если в документе не видны знаки абзаца, в меню **Сервис** наведите указатель на пункт **Microsoft Office Word Tools** и выберите пункт **Параметры**. Перейдите на вкладку **вид** и установите флажок **знаки абзаца** в разделе **знаки форматирования** диалогового окна **Параметры** .

3. В окне **Свойства** измените значение свойства **Name** параметра **Bookmark1** на **шовнаме**.

4. Выделите слово **адрес**, не выбирая знак абзаца.

5. На вкладке ленты **Вставка** в группе **ссылки** щелкните **Закладка**.

6. В диалоговом окне **Закладка** введите **Шоваддресс** в поле **имя закладки** и нажмите кнопку **Добавить**.

## <a name="add-controls-to-the-actions-pane"></a>Добавление элементов управления на панель «действия»
 Чтобы создать интерфейс панели действий, добавьте в проект элемент управления панели действий, а затем добавьте Windows Forms элементы управления в элемент управления панели действий.

### <a name="to-add-an-actions-pane-control"></a>Добавление элемента управления панели действий

1. Выберите проект **панели "Мои базовые действия** " в **Обозреватель решений**.

2. В меню **Проект** выберите **Добавить новый элемент**.

3. В диалоговом окне **Добавление нового элемента** щелкните **элемент Управление панелью действий**, назовите элемент управления **инсерттекстконтрол** и нажмите кнопку **Добавить**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Добавление элементов управления Windows Forms в элемент управления панели действий

1. Если элемент управления панели действий не отображается в конструкторе, дважды щелкните **инсерттекстконтрол**.

2. На вкладке **Общие элементы управления** **панели элементов** перетащите элемент управления **Метка** в элемент управления панель действий.

3. Измените свойство **Text** элемента управления Метка на **имя**.

4. Добавьте элемент управления **TextBox** в элемент управления панель действий и измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**getName**|
    |**Размер**|**130, 20**|

5. Добавьте второй элемент управления **Label** в элемент управления панели действий и измените свойство **Text** на **Address**.

6. Добавьте второй элемент управления **TextBox** в элемент управления панели действий и измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**выадресовать**|
    |**Принимает возврат**|**True**|
    |**Multiline**|**True**|
    |**Размер**|**130, 40**|

7. Добавьте элемент управления **"Кнопка"** в элемент управления панели действий и измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**addText**|
    |**Text**|**Вставить**|

## <a name="add-code-to-insert-text-into-the-document"></a>Добавление кода для вставки текста в документ
 В области действия напишите код, который вставляет текст из текстовых полей в соответствующие <xref:Microsoft.Office.Tools.Word.Bookmark> элементы управления в документе. Класс можно использовать `Globals` для доступа к элементам управления в документе из элементов управления на панели действия. Дополнительные сведения см. [в разделе Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Вставка текста из панели «действия» в закладке в документе

1. Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий кнопки **addText** .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb" id="Snippet8":::

2. В C# необходимо добавить обработчик событий для нажатия кнопки. Этот код можно поместить в `InsertTextControl` конструктор после вызова `InitializeComponent` . Дополнительные сведения о создании обработчиков событий см. в разделе [как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet9":::

## <a name="add-code-to-show-the-actions-pane"></a>Добавление кода для отображения панели действий
 Чтобы отобразить панель действий, добавьте созданный элемент управления в коллекцию элементов управления.

### <a name="to-show-the-actions-pane"></a>Отображение панели «действия»

1. Создайте новый экземпляр элемента управления панели действий в `ThisDocument` классе.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet10":::

2. Добавьте следующий код в <xref:Microsoft.Office.Tools.Word.Document.Startup> обработчик событий `ThisDocument` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet11":::

## <a name="test-the-application"></a>Тестирование приложения
 Протестируйте документ, чтобы убедиться, что панель действий открывается при открытии документа и текст, введенный в текстовые поля, вставляется в закладки при нажатии кнопки.

### <a name="to-test-your-document"></a>Проверка документа

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Убедитесь, что панель действия видна.

3. Введите свое имя и адрес в текстовые поля на панели действия и нажмите кнопку **Вставить**.

## <a name="next-steps"></a>Дальнейшие действия
 Ниже приводятся некоторые из возможных последующих задач.

- Создание панели действий в Excel. Дополнительные сведения см. [в разделе руководство. Добавление панели действий в книги Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).

- Привязка данных к элементам управления на панели действий. Дополнительные сведения см. в разделе [Пошаговое руководство. Привязка данных к элементам управления на панели действий Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

## <a name="see-also"></a>См. также статью
- [Обзор панели действий](../vsto/actions-pane-overview.md)
- [Как добавить панель действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Как добавить панель действий в книги Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Руководство. Управление макетом элементов управления на панелях действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Элемент управления Bookmark](../vsto/bookmark-control.md)
