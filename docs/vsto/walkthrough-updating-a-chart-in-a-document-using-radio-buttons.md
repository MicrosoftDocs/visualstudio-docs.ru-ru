---
title: Пошаговое руководство. Обновление диаграммы в документе с помощью переключателей
description: Узнайте, как можно использовать переключатели в настройке уровня документа для Microsoft Word, чтобы предоставить пользователям возможность выбора стилей диаграммы в документе.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4d6689d82051ef5f8c887c19ec91cbb6d513b8b8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828206"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>Пошаговое руководство. Обновление диаграммы в документе с помощью переключателей
  В данном пошаговом руководстве описывается использование переключателей в настройке уровня документа для Microsoft Office Word, позволяющих пользователям выбирать стили диаграмм в документе.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- добавление диаграммы в документ проекта на уровне документа во время разработки;

- группировка переключателей путем их добавления в пользовательский элемент управления;

- изменение стиля диаграммы при выбранном параметре.

  Чтобы увидеть результат как завершенный пример, см. Примеры элементов управления Word в примерах [разработки Office и пошаговых руководствах](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Создание проекта
 Первым шагом является создание документа Word.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект документа Word с именем **Мои параметры диаграммы**. В мастере выберите **создать новый документ**. Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio откроет новый документ Word в конструкторе и добавит проект **параметров диаграммы** в **Обозреватель решений**.

## <a name="add-a-chart-to-the-document"></a>Добавление диаграммы в документ

### <a name="to-add-a-chart"></a>Добавление диаграммы

1. В документе Word, размещенном в конструкторе Visual Studio, на ленте щелкните вкладку **Вставка** .

2. В **текстовой** группе нажмите кнопку с раскрывающимся списком **Вставка объекта** и выберите пункт **объект**.

     Откроется диалоговое окно **объект** .

3. В списке **тип объекта** на вкладке **создать** выберите **Microsoft Graph диаграмма** и нажмите кнопку **ОК**.

     В документ в точке вставки будет добавлена диаграмма, а в окне **таблицы** отобразятся данные по умолчанию.

4. Закройте окно **таблицы** , чтобы принять значения по умолчанию на диаграмме, и щелкните внутри документа, чтобы переместить фокус с диаграммы.

5. Щелкните правой кнопкой мыши диаграмму и выберите пункт **Формат объекта**.

6. На вкладке **Макет** диалогового окна **Формат объекта** выберите пункт **квадрат** и нажмите кнопку **ОК**.

## <a name="add-a-user-control-to-the-project"></a>Добавление пользовательского элемента управления в проект
 Переключатели в документе не являются взаимоисключающими по умолчанию. Их работу можно сделать правильной, добавив их в пользовательский элемент управления и написав код для управления выбором.

### <a name="to-add-a-user-control"></a>Добавление пользовательского элемента управления

1. Выберите проект " **Мои параметры диаграммы** " в **Обозреватель решений**.

2. В меню **Проект** выберите **Добавить новый элемент**.

3. В диалоговом окне **Добавление нового элемента** щелкните **Пользовательский элемент управления**, назовите элемент управления **чартоптионс** и нажмите кнопку **Добавить**.

### <a name="to-add-windows-form-controls-to-the-user-control"></a>Добавление элементов управления формы Windows в пользовательский элемент управления

1. Если пользовательский элемент управления не отображается в конструкторе, дважды щелкните **чартоптионс** в **Обозреватель решений**.

2. На вкладке **Общие элементы управления** **панели элементов** перетащите первый элемент управления **"переключатель"** в пользовательский элемент управления и измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**columnChart**|
    |**Text**|**Гистограмма**|

3. Добавьте второй **переключатель** в пользовательский элемент управления и измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**barChart**|
    |**Text**|**Линейчатая диаграмма**|

4. Добавьте третий **переключатель** в пользовательский элемент управления и измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**lineChart**|
    |**Text**|**График**|

5. Добавьте четвертый **переключатель** в пользовательский элемент управления и измените следующие свойства.

    |Свойство|Значение|
    |--------------|-----------|
    |**Имя**|**areaBlockChart**|
    |**Text**|**Диаграмма с областями**|

## <a name="add-references"></a>Добавление ссылок
 Чтобы получить доступ к диаграмме из пользовательского элемента управления в документе, необходимо иметь ссылку на `Microsoft.Office.Interop.Graph` сборку в проекте.

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Добавление ссылки на сборку Microsoft.Office.Interop.Graph

1. В меню **Проект** выберите пункт **Добавить ссылку**.

     Откроется диалоговое окно **Добавление ссылки**.

2. На вкладке **.NET** выберите **Microsoft. Office. Interop. Graph** и нажмите кнопку **ОК**. Выберите версию сборки 14.0.0.0.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Изменить стиль диаграммы при выборе переключателя
 Чтобы кнопки работали правильно, создайте открытое событие для пользовательского элемента управления, добавьте свойство, чтобы установить тип выбора, и создайте процедуру для события `CheckedChanged` по каждому переключателю.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Создание события и свойства по пользовательскому элементу управления

1. В **Обозреватель решений** щелкните правой кнопкой мыши пользовательский элемент управления и выберите пункт **Просмотреть код**.

2. Добавьте код, чтобы создать событие `SelectionChanged` и свойство `Selection` в классе `ChartOptions`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet9":::

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Обработка события переключателей CheckedChange

1. Установите тип диаграммы в обработчике событий `CheckedChanged` переключателя `areaBlockChart`, а затем породите событие.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet10":::

2. Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `barChart`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet11":::

3. Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `columnChart`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet12":::

4. Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `lineChart`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet13":::

5. В языке программирования C# для переключателей должны быть добавлены обработчики событий. Код можно добавить в конструктор `ChartOptions` под вызовом `InitializeComponent`. Дополнительные сведения о создании обработчиков событий см. в разделе [как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet14":::

## <a name="add-the-user-control-to-the-document"></a>Добавление пользовательского элемента управления в документ
 При построении решения новый пользовательский элемент управления автоматически добавляется на **панель элементов**. Затем можно перетащить элемент управления из **области элементов** в документ.

### <a name="to-add-the-user-control-your-document"></a>Добавление пользовательского элемента управления в документ

1. В меню **Сборка** выберите **Собрать решение**.

     Пользовательский элемент управления **чартоптионс** добавляется на **панель элементов**.

2. В **Обозреватель решений** щелкните правой кнопкой мыши **ThisDocument. vb** или **ThisDocument. CS** и выберите пункт **Конструктор представлений**.

3. Перетащите `ChartOptions` элемент управления из **области элементов** в документ.

     В окне **Свойства** присвойте элементу управления имя, которое было только что Добавлено в документ  `ChartOptions1` .

## <a name="change-the-chart-type"></a>Изменение типа диаграммы
 Создайте обработчик событий, чтобы изменить тип диаграммы в соответствии с параметром, выбранным в пользовательском элементе управления.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Изменение типа диаграммы, отображаемой в документе

1. Добавьте следующий обработчик событий в класс `ThisDocument`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet15":::

2. В языке программирования C# в событие <xref:Microsoft.Office.Tools.Word.Document.Startup> должен быть добавлен обработчик события для пользовательского элемента управления.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet16":::

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно проверить документ и убедиться, что при выборе переключателя стиль диаграммы обновляется правильно.

### <a name="to-test-your-document"></a>Проверка документа

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Выберите различные переключатели.

3. Подтвердите, что изменения стиля диаграммы соответствуют выбору.

## <a name="next-steps"></a>Дальнейшие действия
 Ниже приводятся некоторые из возможных последующих задач.

- Использование кнопки для заполнения текстового поля. Дополнительные сведения см. [в разделе Пошаговое руководство. Отображение текста в текстовом поле документа с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Изменение форматирования путем выбора стиля из поля со списком. Дополнительные сведения см. в разделе [Пошаговое руководство. изменение форматирования документа с помощью элементов управления CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>См. также статью
- [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)
- [Примеры и пошаговые руководства по разработке решений Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Ограничения элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
