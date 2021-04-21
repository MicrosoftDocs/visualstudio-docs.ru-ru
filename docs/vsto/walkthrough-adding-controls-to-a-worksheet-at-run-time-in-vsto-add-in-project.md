---
title: Добавление элементов управления на лист во время выполнения в проекте надстройки VSTO
description: Узнайте, как использовать ленту, чтобы разрешить пользователям добавлять на лист кнопки, NamedRange и ListObject.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 178180e8c698ca56b15e46bcbe65877d68c6b2a1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824683"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>Пошаговое руководство. Добавление элементов управления на лист во время выполнения в проекте надстройки VSTO
  Вы можете добавить элементы управления на любой открытый лист с помощью надстройки VSTO для Excel. В этом пошаговом руководстве показано, как с помощью ленты предоставить пользователям возможность добавлять <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> и <xref:Microsoft.Office.Tools.Excel.ListObject> на лист. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

 **Применимо к:** Сведения в этом разделе относятся к проектам надстроек VSTO для Excel. Для получения дополнительной информации см. [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).

 В этом пошаговом руководстве описаны следующие задачи:

- предоставление пользовательского интерфейса для добавления элементов управления на лист;

- добавление элементов управления на лист;

- удаление элементов управления с листа.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Excel

## <a name="create-a-new-excel-vsto-add-in-project"></a>Создание нового проекта надстройки VSTO для Excel
 Для начала создайте проект надстройки VSTO для Excel.

### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Создание проекта надстройки VSTO для Excel

1. В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Создайте проект надстройки VSTO для Excel с именем **ексцелдинамикконтролс**. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Добавьте ссылку на сборку **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** . Эта ссылка потребуется для программного добавления элемента управления Windows Forms на лист далее в этом пошаговом руководстве.

## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Предоставление пользовательского интерфейса для добавления элементов управления на лист
 Добавьте настраиваемую вкладку на ленту Excel. Пользователи могут установить флажки на вкладке, чтобы добавить элементы управления на лист.

#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Предоставление пользовательского интерфейса для добавления элементов управления на лист

1. В меню **Проект** выберите **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите **Лента (визуальный конструктор)**, а затем нажмите кнопку **добавить**.

     В конструкторе лент откроется файл с именем **Ribbon1. CS** или **Ribbon1. vb** и отобразится вкладка и группа по умолчанию.

3. Перетащите элемент управления **CheckBox** с вкладки **Элементы управления ленты Office** панели элементов в группу **group1**.

4. Щелкните **CheckBox1** , чтобы выбрать его.

5. В окне **Свойства** измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**Button**|
    |**Label**|**Кнопка**|

6. Добавьте второй флажок в **group1**, а затем измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**NamedRange**|
    |**Label**|**NamedRange**|

7. Добавьте третий флажок в **group1**, а затем измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**ListObject**|
    |**Label**|**ListObject**|

## <a name="add-controls-to-the-worksheet"></a>Добавление элементов управления на лист
 Управляемые элементы управления можно добавить только в ведущие элементы, которые служат контейнерами. Поскольку проекты надстроек VSTO работают с любой открытой книгой, надстройка VSTO преобразует лист в ведущий элемент или получает существующий ведущий элемент перед добавлением элемента управления. Добавьте код в обработчик событий нажатием каждого элемента управления, чтобы создать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet>, основанный на открытом листе. Затем добавьте <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> и <xref:Microsoft.Office.Tools.Excel.ListObject> в выделенный фрагмент на листе.

### <a name="to-add-controls-to-a-worksheet"></a>Добавление элементов управления на лист

1. В конструкторе ленты дважды щелкните **кнопку.**

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>Обработчик событий флажка **кнопки** открывается в редакторе кода.

2. Замените обработчик событий `Button_Click` следующим кодом.

     Этот код использует метод `GetVstoObject` для получения ведущего элемента, представляющего первый лист в книге, а затем добавляет элемент управления <xref:Microsoft.Office.Tools.Excel.Controls.Button> в выбранную ячейку.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet2":::

3. В **Обозреватель решений** выберите *Ribbon1. CS* или *Ribbon1. vb*.

4. В меню **вид** выберите **конструктор**.

5. В конструкторе ленты дважды щелкните элемент **NamedRange**.

6. Замените обработчик событий `NamedRange_Click` следующим кодом.

     Этот код использует метод `GetVstoObject` для получения ведущего элемента, представляющего первый лист в книге, а затем определяет элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> для выбранных ячеек.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet3":::

7. В конструкторе ленты дважды щелкните элемент **ListObject**.

8. Замените обработчик событий `ListObject_Click` следующим кодом.

     Этот код использует метод `GetVstoObject` для получения ведущего элемента, представляющего первый лист в книге, а затем определяет элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> для выбранных ячеек.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet4":::

9. Добавьте следующие операторы в начало файла кода ленты.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet1":::

## <a name="remove-controls-from-the-worksheet"></a>Удаление элементов управления из листа
 Элементы управления не сохраняются при сохранении и закрытии листа. Все созданные элементы управления Windows Forms следует удалить программными средствами до сохранения листа, при этом только контур элемента управления появится при повторном открытии книги. Добавьте код в событие <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>, которое удаляет элементы управления Windows Forms из коллекции элементов управления созданного ведущего элемента управления. Дополнительные сведения см. [в разделе Сохранение динамических элементов управления в документах Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

### <a name="to-remove-controls-from-the-worksheet"></a>Удаление элементов управления с листа

1. В **Обозреватель решений** выберите *ThisAddIn. CS* или *ThisAddIn. vb*.

2. В меню **Вид** выберите пункт **Код**.

3. Добавьте следующий метод в класс `ThisAddIn`. Этот код получает первый лист в книге, а затем использует метод `HasVstoObject`, чтобы проверить, содержит ли лист созданный объект листа. Если созданный объект листа содержит элементы управления, код получает его и проходит по коллекции элементов управления, удаляя элементы управления.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet6":::

4. В C# необходимо создать обработчик для события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>. Этот код можно поместить в методе `ThisAddIn_Startup`. Дополнительные сведения о создании обработчиков событий см. в разделе [инструкции. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md). Замените метод `ThisAddIn_Startup` приведенным ниже кодом.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet5":::

## <a name="test-the-solution"></a>Тестирование решения
 Добавьте элементы управления на лист, выбрав их на пользовательской вкладке ленты. При сохранении листа эти элементы управления будут удалены.

### <a name="to-test-the-solution"></a>Тестирование решения

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Выберите любую ячейку на листе Sheet1.

3. Перейдите на вкладку **Надстройки** .

4. В группе **group1** нажмите кнопку **кнопка**.

     В выбранной ячейке появится кнопка.

5. Выберите другую ячейку на листе Sheet1.

6. В группе **group1** щелкните **NamedRange**.

     Именованный диапазон будет определен для выбранной ячейки.

7. Выберите ряд ячеек на листе Sheet1.

8. В группе **group1** щелкните элемент **ListObject**.

     Объект списка будет добавлен для выделенных ячеек.

9. Сохраните лист.

     Элементы управления, добавленные в Sheet1, больше не отображаются.

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения об элементах управления в проектах надстройки VSTO для Excel см. в следующем разделе:

- Дополнительные сведения о сохранении элементов управления на листе см. в разделе примеры динамических элементов управления надстройки VSTO для Excel в разделе [образцы разработки Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="see-also"></a>См. также статью
- [Решения Excel](../vsto/excel-solutions.md)
- [Общие сведения об элементах управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Элемент управления ListObject](../vsto/listobject-control.md)
