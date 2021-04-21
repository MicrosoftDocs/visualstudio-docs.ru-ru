---
title: Привязка к данным из службы в проекте надстройки VSTO
description: Узнайте, как добавлять элементы управления в документ Microsoft Word, привязывать элементы управления к данным, полученным из службы содержимого MSDN, и реагировать на события во время выполнения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b6993cb3eebc7641f4486bdc617ecb78e40aa05c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824532"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>Пошаговое руководство. привязка к данным из службы в проекте надстройки VSTO
  Вы можете привязывать данные к элементам управления ведущего приложения в проектах надстроек VSTO. В этом пошаговом руководстве демонстрируется добавление элементов управления в документ Microsoft Office Word, привязка элементов управления к данным, полученным из службы содержимого MSDN, и реагирование на события во время выполнения.

 **Применение.** Сведения этого раздела относятся к проектам уровня приложения для Word 2010. Для получения дополнительной информации см. [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).

 В этом пошаговом руководстве описаны следующие задачи:

- Добавление элемента управления <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в документ во время выполнения.

- Привязка <xref:Microsoft.Office.Tools.Word.RichTextContentControl> элемента управления к данным из веб-службы.

- Реагирование на событие <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> элемента управления <xref:Microsoft.Office.Tools.Word.RichTextContentControl> .

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-project"></a>Создание нового проекта
 Первым шагом является создание проекта надстройки Word VSTO.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект надстройки VSTO для Word с именем **Служба содержимого MTPS** в Visual Basic или C#.

     Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет файл `ThisAddIn.vb` или `ThisAddIn.cs` и добавит проект в **обозреватель решений**.

## <a name="add-a-web-service"></a>Добавление веб-службы
 В этом пошаговом руководстве используется веб-служба, которая называется службой содержимого MTPS. Эта веб-служба возвращает сведения из указанной статьи MSDN в виде XML-строки или обычного текста. Ниже показано, как отобразить возвращенные сведения в элементе управления содержимым.

### <a name="to-add-the-mtps-content-service-to-the-project"></a>Добавление службы содержимого MTPS в проект

1. В меню **Данные** выберите команду **Добавить новый источник данных**.

2. В **мастере настройки источника данных** щелкните элемент **Служба** и нажмите кнопку **Далее**.

3. В поле **Адрес** введите следующий URL-адрес:

   `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

4. Нажмите кнопку **Переход**.

5. В поле **Пространство имен** введите **ContentService** и нажмите кнопку **ОК**.

6. В диалоговом окне **Мастер добавления ссылок** нажмите кнопку **Готово**.

## <a name="add-a-content-control-and-bind-to-data-at-run-time"></a>Добавление элемента управления содержимым и привязка к данным во время выполнения
 В проектах надстроек VSTO вы можете добавлять и привязывать элементы управления во время выполнения. Для этого пошагового руководства настройте элемент управления содержимым, чтобы получать данные из веб-службы, когда пользователь щелкает внутри элемента управления.

### <a name="to-add-a-content-control-and-bind-to-data"></a>Добавление элемента управления содержимым и привязка к данным

1. В классе `ThisAddIn` объявите переменные для службы содержимого MTPS, элемента управления содержимым и привязки данных.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet2":::

2. Добавьте следующий метод в класс `ThisAddIn`. Этот метод создает элемент управления содержимым в начале активного документа.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet4":::

3. Добавьте следующий метод в класс `ThisAddIn`. Этот метод инициализирует объекты, необходимые для создания и отправки запроса веб-службе.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet6":::

4. Создайте обработчик событий, чтобы извлечь документ библиотеки MSDN об элементах управления содержимым, когда пользователь щелкает внутри элемента управления, и привяжите данные к элементу управления содержимым.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet5":::

5. Вызовите методы `AddRichTextControlAtRange` и `InitializeServiceObjects` из метода `ThisAddIn_Startup` . Программисты C# должны добавить обработчик событий.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet3":::

## <a name="test-the-add-in"></a>Тестирование надстройки
 При открытии Word появляется элемент управления <xref:Microsoft.Office.Tools.Word.RichTextContentControl> . Текст в этом элементе управления при щелчке внутри него.

### <a name="to-test-the-vsto-add-in"></a>Тестирование надстройки VSTO

1. Нажмите клавишу **F5**.

2. Щелкните внутри элемента управления содержимым.

     Информация загружается из службы содержимого MTPS и отображается внутри элемента управления содержимым.

## <a name="see-also"></a>См. также статью
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
