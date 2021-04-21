---
title: Пошаговое руководство. Привязка элементов управления содержимым к пользовательским XML-частям
description: Узнайте, как привязать элементы управления содержимым в настройке уровня документа для Word к данным XML, хранящимся в документе.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6e4a10949f463cc769890b828ba39de30a9b4c1c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824579"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Пошаговое руководство. Привязка элементов управления содержимым к пользовательским XML-частям
  В этом пошаговом руководстве показано, как привязать элементы управления содержимым в настройке на уровне документа для Word к XML-данным, хранящимся в документе.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word позволяет хранить XML-данные, именованные *пользовательские XML-части*, в документе. Вы можете управлять отображением этих данных, привязывая элементы управления содержимым к элементам в пользовательской XML-части. Пример документа в этом пошаговом руководстве отображает данные о сотрудниках, которые хранятся в пользовательской XML-части. При открытии документа элементы управления содержимым показывают значения XML-элементов. Любые изменения, внесенные в текст в элементах управления содержимым, сохраняются в пользовательской XML-части.

 В этом пошаговом руководстве описаны следующие задачи:

- добавление элементов управления содержимым в документ Word в проекте на уровне документа во время разработки;

- создание файла XML-данных и XML-схемы, которая определяет элементы для привязки к элементам управления содержимым;

- добавление схемы XML к документу во время разработки;

- добавление содержимого XML-файла к пользовательской XML-части в документе во время выполнения;

- привязка элементов управления содержимым к элементам в пользовательской XML-части;

- привязка <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> к набору значений, определенных в схеме XML.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-document-project"></a>Создать новый проект документа Word
 Создайте документ Word, который будет использоваться в этом руководстве.

### <a name="to-create-a-new-word-document-project"></a>Создание проекта документа Word

1. Создайте проект документа Word с именем **емплойиконтролс**. Создайте документ для решения. Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает новый документ Word в конструкторе и добавляет проект **емплойиконтролс** в **Обозреватель решений**.

## <a name="add-content-controls-to-the-document"></a>Добавление элементов управления содержимым в документ
 Создайте таблицу, содержащую три различных типа элементов управления содержимым, в которой пользователь может просмотреть или изменить сведения о сотруднике.

### <a name="to-add-content-controls-to-the-document"></a>Порядок добавления элементов управления содержимым в документ

1. В документе Word, размещенном в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] конструкторе, на ленте выберите вкладку **Вставка** .

2. В группе **таблицы** выберите **Таблица** и вставьте таблицу с 2 столбцами и 3 строками.

3. Введите текст в первый столбец, как показано в следующем столбце:

   ||
   |-|
   |**Имя сотрудника**|
   |**Дата приема на работу**|
   |**Title**|

4. Во втором столбце таблицы выберите первую строку (рядом с **именем сотрудника**).

5. На ленте выберите вкладку **разработчик** .

   > [!NOTE]
   > Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [инструкции. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. В группе **элементы управления** нажмите кнопку с **текстом** ![плаинтекстконтентконтрол](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") , чтобы добавить в <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> первую ячейку.

7. Во втором столбце таблицы выберите вторую строку (рядом с полем **Дата найма**).

8. В группе **элементы управления** нажмите кнопку **выбора даты** ![датепиккерконтентконтрол](../vsto/media/datepicker.gif "DatePickerContentControl") , чтобы добавить <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> к второй ячейке.

9. Во втором столбце таблицы выберите третью строку (рядом с **заголовком**).

10. В группе **элементы управления** нажмите кнопку раскрывающегося **списка** ![дропдовнлистконтентконтрол](../vsto/media/dropdownlist.gif "DropDownListContentControl") , чтобы добавить в <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> последнюю ячейку.

    Вот и весь пользовательский интерфейс для этого проекта. При запуске проекта можно ввести текст в первой строке и выбрать дату во второй строке. Следующий шаг — присоединение данных, которые будут отображаться в документе, к XML-файлу.

## <a name="create-the-xml-data-file"></a>Создание XML-файла данных
 Как правило, вы будете получать XML-данные для хранения в пользовательской XML-части из внешнего источника, например файла или базы данных. В этом пошаговом руководстве создается XML-файл, содержащий данные о сотрудниках, помеченные элементами, которые необходимо привязать к элементам управления содержимым в документе. Чтобы данные были доступны во время выполнения, внедрите XML-файл как ресурс в сборку настройки.

#### <a name="to-create-the-data-file"></a>Создание файла данных

1. В меню **Проект** выберите пункт **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

2. В области **шаблоны** выберите **XML-файл**.

3. Присвойте файлу имя **employees.xml**, а затем нажмите кнопку **Добавить** .

     Файл **employees.xml** откроется в редакторе кода.

4. Замените содержимое файла **employees.xml** следующим текстом.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">
      <employee>
        <name>Karina Leal</name>
        <hireDate>1999-04-01</hireDate>
        <title>Manager</title>
      </employee>
    </employees>
    ```

5. В **Обозреватель решений** выберите файл **employees.xml** .

6. В окне **Свойства** выберите свойство **действие сборки** , а затем измените значение на **внедренный ресурс**.

     Этот шаг внедряет XML-файл в качестве ресурса в сборку при построении проекта. Так вы получите возможность доступа к содержимому XML-файла во время выполнения.

## <a name="create-an-xml-schema"></a>Создание XML-схемы
 Если вам необходимо привязать элемент управления содержимым к одному элементу в пользовательской XML-части, необязательно использовать схему XML. Однако для привязки <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> к набору значений необходимо создать схему XML, которая проверяет созданный ранее файл XML-данных. Схема XML определяет возможные значения для элемента `title`. Вы привяжете <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> к этому элементу далее в этом пошаговом руководстве.

#### <a name="to-create-an-xml-schema"></a>Порядок создания схемы XML

1. В меню **Проект** выберите пункт **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

2. В области **шаблоны** выберите **XML-схема**.

3. Присвойте схеме имя **Employees. xsd** и нажмите кнопку **Добавить** .

     Открывается конструктор схем.

4. В **Обозреватель решений** откройте контекстное меню  **Employees. xsd** и выберите пункт  **Просмотреть код**.

5. Замените содержимое файла **Employees. xsd** следующей схемой.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"
        targetNamespace="http://schemas.microsoft.com/vsto/samples"
        xmlns:xs="http://www.w3.org/2001/XMLSchema"
        elementFormDefault="qualified">
      <xs:element name="employees" type="EmployeesType"></xs:element>
      <xs:complexType name="EmployeesType">
        <xs:all>
          <xs:element name="employee" type="EmployeeType"/>
        </xs:all>
      </xs:complexType>
      <xs:complexType name="EmployeeType">
        <xs:sequence>
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>
        </xs:sequence>
      </xs:complexType>
      <xs:simpleType name="TitleType">
        <xs:restriction base="xs:string">
          <xs:enumeration value ="Engineer"/>
          <xs:enumeration value ="Designer"/>
          <xs:enumeration value ="Manager"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:schema>
    ```

6. В меню **файл** выберите команду **сохранить все** , чтобы сохранить изменения в **employees.xml** и в файлах **Employees. xsd** .

## <a name="attach-the-xml-schema-to-the-document"></a>Присоединение схемы XML к документу
 XML-схему необходимо присоединить к документу, чтобы привязать <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> к допустимым значениям элемента `title`.

### <a name="to-attach-the-xml-schema-to-the-document--word_15_short"></a>Присоединение схемы XML к документу ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] )

1. Активируйте **EmployeeControls.docx** в конструкторе.

2. На ленте выберите вкладку **разработчик** и нажмите кнопку **надстройки** .

3. В диалоговом окне **шаблоны и надстройки** перейдите на вкладку **XML-схема** и нажмите кнопку **Добавить схему** .

4. Перейдите к созданной ранее схеме **Employees. xsd** , которая находится в каталоге проекта, а затем нажмите кнопку **Открыть** .

5. Нажмите кнопку **ОК** в диалоговом окне **Параметры схемы** .

6. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **шаблоны и надстройки** .

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Добавление схемы XML к документу (Word 2010)

1. Активируйте **EmployeeControls.docx** в конструкторе.

2. На ленте выберите вкладку **разработчик** .

3. В группе **XML** нажмите кнопку **схема** .

4. В диалоговом окне **шаблоны и надстройки** перейдите на вкладку **XML-схема** и нажмите кнопку **Добавить схему** .

5. Перейдите к созданной ранее схеме **Employees. xsd** , которая находится в каталоге проекта, и нажмите кнопку **Открыть** .

6. Нажмите кнопку **ОК** в диалоговом окне **Параметры схемы** .

7. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **шаблоны и надстройки** .

     Откроется область задач **Структура XML** .

8. Закройте область задач **Структура XML** .

## <a name="add-a-custom-xml-part-to-the-document"></a>Добавление пользовательской XML-части в документ
 Перед привязкой элементов управления содержимым к элементам в XML-файле необходимо добавить содержимое XML-файла в новую пользовательскую XML-часть в документе.

### <a name="to-add-a-custom-xml-part-to-the-document"></a>Порядок добавления пользовательской XML-части в документ

1. В **Обозреватель решений** откройте контекстное меню для  **ThisDocument. CS** или **ThisDocument. vb**, а затем выберите **Просмотреть код**.

2. Добавьте в класс `ThisDocument` следующие объявления. В этом коде объявляются несколько объектов, которые будут использоваться для добавления пользовательской XML-части в документ.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet1":::

3. Добавьте следующий метод в класс `ThisDocument`. Этот метод получает содержимое файла данных XML, внедренного в сборку в качестве ресурса, и возвращает содержимое в виде XML-строки.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet3":::

4. Добавьте следующий метод в класс `ThisDocument`. Метод `AddCustomXmlPart` создает пользовательскую XML-часть, которая содержит XML-строку, передаваемую в метод.

     Чтобы пользовательская XML-часть создавалась всего один раз, метод создает ее, только если пользовательская XML-часть с соответствующим идентификатором GUID еще не существует в документе. При первом вызове этого метода он сохраняет значение свойства <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> в строке `employeeXMLPartID`. Значение `employeeXMLPartID` строки хранится в документе, поскольку он был объявлен с помощью атрибута <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet4":::

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Привязка элементов управления содержимым к элементам в пользовательской XML-части
 Привяжите каждый элемент управления содержимым к элементу в пользовательской XML-части с помощью свойства **XmlMapping** каждого элемента управления содержимым.

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Порядок привязки элементов управления содержимым к элементам в пользовательской XML-части

1. Добавьте следующий метод в класс `ThisDocument`. Он привязывает каждый элемент управления содержимым к элементу в пользовательской XML-части и задает формат отображения даты <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet5":::

## <a name="run-your-code-when-the-document-is-opened"></a>Выполнение кода при открытии документа
 Создайте пользовательскую XML-часть и привяжите пользовательские элементы управления к данным при открытии документа.

### <a name="to-run-your-code-when-the-document-is-opened"></a>Порядок выполнения кода после открытия документа

1. Добавьте в метод `ThisDocument_Startup` класса `ThisDocument` следующий код. Этот код получает XML-строку из файла **employees.xml** , добавляет XML-строку в новую пользовательскую часть XML в документе и привязывает элементы управления содержимым к элементам в пользовательской XML-части.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet2":::

## <a name="test-the-project"></a>Тестирование проекта
 При открытии документа элементы управления содержимым отображают данные из элементов в пользовательской XML-части. Можно щелкнуть, <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> чтобы выбрать одно из трех допустимых значений для `title` элемента, определенных в файле **Employees. xsd** . Если изменить данные в любом из элементов управления содержимым, новые значения сохраняются в пользовательской XML-части в документе.

### <a name="to-test-the-content-controls"></a>Проверка элементов управления содержимым

1. Нажмите клавишу **F5** , чтобы запустить проект.

2. Убедитесь, что таблица в документе похожа на следующую таблицу. Каждая строка во втором столбце извлекается из элемента в пользовательской XML-части в документе.

    |Столбец|Значение|
    |-|-|
    |**Имя сотрудника**|**Karina Leal**|
    |**Дата приема на работу**|**1 апреля 1999 г.**|
    |**Title**|**Менеджер**|

3. Щелкните ячейку справа от ячейки **имя сотрудника** и введите другое имя.

4. Выберите ячейку справа от ячейки " **Дата найма** " и выберите другую дату в элементе выбора даты.

5. Выберите ячейку справа от ячейки **заголовка** и выберите новый элемент из раскрывающегося списка.

6. Сохраните и закройте документ.

7. В проводнике откройте папку *\bin\Debug* в расположении проекта.

8. Откройте контекстное меню для **EmployeeControls.docx** и выберите **Переименовать**.

9. Присвойте файлу имя **EmployeeControls.docx.zip**.

     Документ **EmployeeControls.docx** сохраняется в формате Open XML. Переименование этого документа с помощью расширения имени *ZIP* -файла позволяет проверить содержимое документа. Дополнительные сведения об Open XML см. в технической статье [Знакомство с форматами файлов Office (2007) Open XML](/previous-versions/office/developer/office-2007/aa338205(v=office.12)).

10. Откройте файл **EmployeeControls.docx.zip** .

11. Откройте папку **customXml** .

12. Откройте контекстное меню для **item2.xml** и выберите **Открыть**.

     Этот файл содержит пользовательскую XML-часть, которая была добавлена в документ.

13. Убедитесь, что элементы `name`, `hireDate` и `title` содержат новые значения, введенные в элементы управления содержимым в документе.

14. Закройте файл **item2.xml** .

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения об использовании элементов управления содержимым см. в следующих разделах.

- Использование всех доступных элементов управления содержимым для создания шаблона. Дополнительные сведения см. в разделе [Пошаговое руководство. Создание шаблона с помощью элементов управления содержимым](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).

- Изменение данных в пользовательских XML-частях при закрытии документа. При следующем открытии документа пользователем элементы управления содержимым, привязанные к XML-элементам, покажут новые данные.

- Использование элементов управления содержимым для защиты частей документов. Дополнительные сведения см. [в разделе руководство. Защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="see-also"></a>См. также статью
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Элементы управления содержимым](../vsto/content-controls.md)
- [Как добавить элементы управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Пошаговое руководство. Защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
