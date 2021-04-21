---
title: Пошаговое руководство. Создание шаблона с помощью элементов управления содержимым
description: Узнайте, как создать настройку на уровне документа, которая использует элементы управления содержимым для создания структурированного и повторно используемого содержимого в шаблоне Microsoft Word.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7f78ca406d19461de7fa8e2a8c147b1003c9c852
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826971"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Пошаговое руководство. Создание шаблона с помощью элементов управления содержимым
  В этом пошаговом руководстве показано, как создать настройку на уровне документа, использующую элементы управления содержимым, для создания структурированного и повторно используемого содержимого в шаблоне Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word позволяет создать коллекцию многократно используемых частей документа, именуемых *стандартными блоками*. В этом пошаговом руководстве демонстрируется создание двух таблиц в качестве стандартных блоков. Каждая из них содержит несколько элементов управления, которые могут включать разные типы содержимого, например обычный текст или даты. Одна из таблиц содержит информацию о сотруднике, а другая таблица содержит отзывы.

 После создания документа на основе шаблона можно добавить любую из таблиц в документ, используя несколько объектов <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, отображающих доступные стандартные блоки в шаблоне.

 В этом пошаговом руководстве описаны следующие задачи:

- создание таблиц с элементами управления содержимым в шаблоне Word во время разработки;

- заполнение элемента управления содержимым «Поле со списком» и элемента управления содержимым «Раскрывающийся список»;

- запрет редактирования указанной таблицы пользователями;

- добавление таблиц в коллекцию стандартных блоков шаблона;

- создание элемента управления содержимым, отображающего доступные стандартные блоки в шаблоне.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-template-project"></a>Создание нового проекта шаблона Word
 Создайте шаблон Word, чтобы пользователи могли легко создавать собственные копии.

### <a name="to-create-a-new-word-template-project"></a>Создание проекта шаблона Word

1. Создайте проект шаблона Word с именем **мибуилдингблокктемплате**. В мастере создайте документ в решении. Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает новый шаблон Word в конструкторе и добавляет проект **мибуилдингблокктемплате** в **Обозреватель решений**.

## <a name="create-the-employee-table"></a>Создание таблицы Employee
 Создайте таблицу, содержащую четыре различных типа элементов управления содержимым, в которой пользователь может ввести сведения о сотруднике.

### <a name="to-create-the-employee-table"></a>Создание таблицы сотрудников

1. В шаблоне Word, размещенном в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] конструкторе, на ленте щелкните вкладку **Вставка** .

2. В группе **таблицы** щелкните **Таблица** и вставьте таблицу с двумя столбцами и четырьмя строками.

3. Введите текст в первый столбец, как показано в следующем столбце:

   ||
   |-|
   |**Имя сотрудника**|
   |**Дата приема на работу**|
   |**Title**|
   |**Снимки**|

4. Щелкните первую ячейку во втором столбце (рядом с **именем сотрудника**).

5. На ленте перейдите на вкладку **Разработчик** .

   > [!NOTE]
   > Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [инструкции. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. В группе **элементы управления** нажмите кнопку Text ![плаинтекстконтентконтрол](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") ( **текст** ), чтобы добавить в <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> первую ячейку.

7. Щелкните вторую ячейку во втором столбце (рядом с полем **Дата найма**).

8. В группе **элементы управления** нажмите кнопку **выбора даты** ![датепиккерконтентконтрол](../vsto/media/datepicker.gif "DatePickerContentControl") , чтобы добавить <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> к второй ячейке.

9. Щелкните третью ячейку во втором столбце (рядом с **заголовком**).

10. В группе **элементы управления** нажмите кнопку с **полем со списком** ![комбобоксконтентконтрол](../vsto/media/combobox.gif "ComboBoxContentControl") , чтобы добавить в <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> третью ячейку.

11. Щелкните последнюю ячейку во втором столбце (рядом с **изображением**).

12. В группе **элементы управления** нажмите кнопку с **изображением элемента управления содержимым** ![пиктуреконтентконтрол](../vsto/media/pictcontentcontrol.gif "PictureContentControl") , чтобы добавить <xref:Microsoft.Office.Tools.Word.PictureContentControl> к последней ячейке.

## <a name="create-the-customer-feedback-table"></a>Создание таблицы отзывов клиентов
 Создайте таблицу, содержащую три различных типа элементов управления содержимым, в которой пользователь может ввести отзывы клиентов.

### <a name="to-create-the-customer-feedback-table"></a>Создание таблицы отзывов клиентов

1. В шаблоне Word щелкните строку после добавленной ранее таблицы Employee и нажмите клавишу **Ввод** , чтобы добавить новый абзац.

2. На ленте щелкните вкладку **Вставка** .

3. В группе **таблицы** щелкните **Таблица** и вставьте таблицу с двумя столбцами и тремя строками.

4. Введите текст в первый столбец, как показано в следующем столбце:

   ||
   |-|
   |**Имя клиента**|
   |**Степень удовлетворенности**|
   |**Комментарии**|

5. Щелкните первую ячейку второго столбца (рядом с полем **имя клиента**).

6. На ленте перейдите на вкладку **Разработчик** .

7. В группе **элементы управления** нажмите кнопку Text ![плаинтекстконтентконтрол](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") ( **текст** ), чтобы добавить в <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> первую ячейку.

8. Щелкните во второй ячейке второго столбца (рядом с **рейтингом удовлетворенности**).

9. В группе **элементы управления** нажмите кнопку раскрывающегося **списка** ![дропдовнлистконтентконтрол](../vsto/media/dropdownlist.gif "DropDownListContentControl") , чтобы добавить <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> к второй ячейке.

10. Щелкните последнюю ячейку второго столбца (рядом с **комментариями**).

11. В группе **элементы управления** нажмите кнопку **форматированный текст** ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") , чтобы добавить <xref:Microsoft.Office.Tools.Word.RichTextContentControl> к последней ячейке.

## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Заполнение поля со списком и раскрывающегося списка программным способом
 Элементы управления содержимым можно инициализировать во время разработки с помощью окна **Свойства** в среде [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Также их можно инициализировать во время выполнения, что позволяет динамически задавать их начальное состояние. В этом пошаговом руководстве используется код для заполнения записей в <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> и <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> во время выполнения, чтобы можно было увидеть, как работают эти объекты.

### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Изменение пользовательского интерфейса элементов управления содержимым программным способом

1. В **Обозреватель решений** щелкните правой кнопкой мыши **ThisDocument. CS** или **ThisDocument. vb** и выберите пункт **Просмотреть код**.

2. Добавьте в класс `ThisDocument` приведенный далее код. В этом коде объявляются несколько объектов, которые вы будете использовать позже в этом пошаговом руководстве.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet1":::

3. Добавьте в метод `ThisDocument_Startup` класса `ThisDocument` следующий код. Этот код добавляет записи в таблицы <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> и <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> и задает замещающий текст, отображаемый в каждом из этих элементов управления, прежде чем пользователь изменяет их.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet2":::

## <a name="prevent-users-from-editing-the-employee-table"></a>Запретить пользователям изменять таблицу сотрудников
 Используйте объект <xref:Microsoft.Office.Tools.Word.GroupContentControl>, объявленный ранее, для защиты таблицы сотрудников. После применения защиты пользователи по-прежнему смогут редактировать элементы управления содержимым в таблице. Однако они не смогут изменять текст в первом столбце или изменять таблицу иным способом, например добавляя или удаляя строки и столбцы. Дополнительные сведения об использовании <xref:Microsoft.Office.Tools.Word.GroupContentControl> для защиты части документа см. в разделе [элементы управления содержимым](../vsto/content-controls.md).

### <a name="to-prevent-users-from-editing-the-employee-table"></a>Запрет редактирования указанной таблицы пользователями

1. Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код предотвращает изменение таблицы сотрудников, помещая таблицу внутри объекта <xref:Microsoft.Office.Tools.Word.GroupContentControl>, объявленного ранее.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet3":::

## <a name="add-the-tables-to-the-building-block-collection"></a>Добавление таблиц в коллекцию стандартных блоков
 Добавьте таблицы в коллекцию стандартных блоков документа в шаблоне, чтобы пользователи могли вставлять таблицы, созданные вами в документе. Дополнительные сведения о стандартных блоках документов см. в разделе [элементы управления содержимым](../vsto/content-controls.md).

### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Добавление таблиц в стандартные блоки в шаблоне

1. Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код добавляет новые стандартные блоки, содержащие таблицы, в коллекцию Microsoft. Office. Interop. Word. Буилдингблоккентриес, которая содержит все повторно используемые стандартные блоки в шаблоне. Новые стандартные блоки определяются в новой категории с именем **Employee и Customer** , и им назначается тип стандартного блока `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet4":::

2. Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код удаляет таблицы из шаблона. Таблицы более не нужны, поскольку вы добавили их в коллекцию повторно используемых стандартных блоков в шаблоне. Код сначала переводит документ в режим конструктора, чтобы можно было удалить защищенную таблицу сотрудников.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet5":::

## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Создание элемента управления содержимым, отображающего стандартные блоки
 Создайте элемент управления содержимым, предоставляющий доступ к стандартным блокам (таблицам), созданным ранее. Пользователи могут щелкнуть этот элемент управления, чтобы добавить таблицы в документ.

### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Создание элемента управления содержимым, отображающего доступные стандартные блоки

1. Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код инициализирует объект <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, объявленный ранее. Компонент <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> отображает все стандартные блоки, определенные в категории **Employee и Customer** , с типом стандартного блока `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet6":::

## <a name="test-the-project"></a>Тестирование проекта
 Пользователи могут щелкнуть элементы управления коллекции стандартных блоков в документе, чтобы вставить таблицу сотрудников или отзывов. Пользователи могут ввести или выбрать ответы в элементах управления содержимым в обеих таблицах. Пользователи могут изменять другие части таблицы отзывов, но они не смогут менять другие части таблицы сотрудников.

### <a name="to-test-the-employee-table"></a>Проверка таблицы сотрудников

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Щелкните **выбрать первый стандартный блок** , чтобы отобразить первый элемент управления содержимым коллекции стандартных блоков.

3. Щелкните стрелку раскрывающегося списка рядом с заголовком **настраиваемой коллекции 1** в элементе управления и выберите **таблица сотрудников**.

4. Щелкните ячейку справа от ячейки **имя сотрудника** и введите имя.

     Убедитесь, что в эту ячейку можно добавить только текст. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> позволяет пользователям добавлять только текст, но не другие типы содержимого, такие как изображения или таблицы.

5. Щелкните ячейку справа от ячейки **Дата найма** и выберите дату в элементе выбора даты.

6. Щелкните ячейку справа от ячейки **Title (заголовок** ) и выберите один из названий заданий в поле со списком.

     При необходимости введите имя должности, которого нет в списке. Это возможно, поскольку <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> позволяет пользователям выбрать из списка записей или ввести собственную запись.

7. Щелкните значок в ячейке справа от ячейки **изображения** и перейдите к изображению, чтобы отобразить его.

8. Попробуйте добавить строки или столбцы в таблицу и попытайтесь удалить строки и столбцы из нее. Убедитесь, что изменить таблицу нельзя. <xref:Microsoft.Office.Tools.Word.GroupContentControl> не позволяет вносить какие-либо изменения.

### <a name="to-test-the-customer-feedback-table"></a>Проверка таблицы отзывов клиентов

1. Щелкните **выбрать второй Стандартный блок** , чтобы отобразить второй элемент управления содержимым коллекции стандартных блоков.

2. Щелкните стрелку раскрывающегося списка рядом с заголовком **настраиваемой коллекции 1** в элементе управления и выберите **таблица Customer**.

3. Щелкните ячейку справа от ячейки **имя клиента** и введите имя.

4. Щелкните ячейку справа от ячейки **рейтинг удовлетворенности** и выберите один из доступных вариантов.

     Убедитесь, что нельзя вводить записи. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> позволяет пользователям только выбирать варианты из списка элементов.

5. Щелкните ячейку справа от ячейки **Примечания** и введите несколько комментариев.

     При необходимости добавьте содержимое, отличное от текста, например изображение или вложенную таблицу. Это возможно, поскольку <xref:Microsoft.Office.Tools.Word.RichTextContentControl> позволяет пользователям добавлять содержимое, отличное от текста.

6. Убедитесь, что вы можете добавить строки или столбцы в таблицу и удалить строки и столбцы из нее. Это возможно, поскольку вы не защитили таблицу, поместив ее в <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

7. Закройте шаблон.

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения об использовании элементов управления содержимым см. в следующем разделе:

- Привязка элементов управления содержимым к фрагментам XML-кода, которые также называют пользовательскими XML-частями, внедренным в документ. Дополнительные сведения см. [в разделе Пошаговое руководство. Привязка элементов управления содержимым к пользовательским XML-частям](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

## <a name="see-also"></a>См. также статью
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Элементы управления содержимым](../vsto/content-controls.md)
- [Как добавить элементы управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Пошаговое руководство. Защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
