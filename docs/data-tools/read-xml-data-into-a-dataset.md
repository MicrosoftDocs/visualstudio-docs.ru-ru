---
title: Считывание XML-данных в набор данных
description: Чтение XML-данных в наборе данных. В этом пошаговом руководстве вы создадите приложение Windows, которое загружает XML-данные в набор данных.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b3a238bf325819b340b983618b5aac8f723184f4
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216193"
---
# <a name="read-xml-data-into-a-dataset"></a>Считывание XML-данных в набор данных

ADO.NET предоставляет простые методы для работы с XML-данными. В этом пошаговом руководстве вы создадите приложение Windows, которое загружает XML-данные в набор данных. Затем набор данных отображается в <xref:System.Windows.Forms.DataGridView> элементе управления. Наконец, схема XML, основанная на содержимом XML-файла, отображается в текстовом поле.

## <a name="create-a-new-project"></a>Создание нового проекта

Создайте новый проект **Windows Forms приложения** для C# или Visual Basic. Назовите проект **реадингксмл**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Создать XML-файл для чтения в наборе данных

Поскольку в этом пошаговом руководстве рассматривается чтение XML-данных в наборе данных, предоставляется содержимое XML-файла.

1. В меню **Проект** выберите команду **Добавить новый элемент**.

2. Выберите **XML-файл**, присвойте файлу имя **authors.xml**, а затем нажмите кнопку **добавить**.

   XML-файл загружается в конструктор и готов к редактированию.

3. Вставьте следующие XML-данные в редактор под XML-объявлением:

   ```xml
   <Authors_Table>
     <authors>
       <au_id>172-32-1176</au_id>
       <au_lname>White</au_lname>
       <au_fname>Johnson</au_fname>
       <phone>408 496-7223</phone>
       <address>10932 Bigge Rd.</address>
       <city>Menlo Park</city>
       <state>CA</state>
       <zip>94025</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>213-46-8915</au_id>
       <au_lname>Green</au_lname>
       <au_fname>Margie</au_fname>
       <phone>415 986-7020</phone>
       <address>309 63rd St. #411</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94618</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>238-95-7766</au_id>
       <au_lname>Carson</au_lname>
       <au_fname>Cheryl</au_fname>
       <phone>415 548-7723</phone>
       <address>589 Darwin Ln.</address>
       <city>Berkeley</city>
       <state>CA</state>
       <zip>94705</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>267-41-2394</au_id>
       <au_lname>Hunter</au_lname>
       <au_fname>Anne</au_fname>
       <phone>408 286-2428</phone>
       <address>22 Cleveland Av. #14</address>
       <city>San Jose</city>
       <state>CA</state>
       <zip>95128</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>274-80-9391</au_id>
       <au_lname>Straight</au_lname>
       <au_fname>Dean</au_fname>
       <phone>415 834-2919</phone>
       <address>5420 College Av.</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94609</zip>
       <contract>true</contract>
     </authors>
   </Authors_Table>
   ```

4. В меню **файл** выберите команду **сохранить authors.xml**.

## <a name="create-the-user-interface"></a>Создание пользовательского интерфейса

Пользовательский интерфейс для этого приложения состоит из следующих компонентов:

- <xref:System.Windows.Forms.DataGridView>Элемент управления, отображающий содержимое XML-файла в виде данных.

- <xref:System.Windows.Forms.TextBox>Элемент управления, отображающий XML-схему для XML-файла.

- Два <xref:System.Windows.Forms.Button> элемента управления.

  - Одна кнопка считывает XML-файл в набор данных и отображает его в <xref:System.Windows.Forms.DataGridView> элементе управления.

  - Вторая кнопка извлекает схему из набора данных, а затем <xref:System.IO.StringWriter> отображает ее в <xref:System.Windows.Forms.TextBox> элементе управления.

### <a name="to-add-controls-to-the-form"></a>Для добавления элементов управления в форму

1. Откройте `Form1` в режиме конструктора.

2. Перетащите следующие элементы управления из **области элементов** в форму:

    - Один <xref:System.Windows.Forms.DataGridView> элемент управления

    - Один <xref:System.Windows.Forms.TextBox> элемент управления

    - Два <xref:System.Windows.Forms.Button> элемента управления

3. Задайте следующие свойства.

    |Control|Свойство.|Параметр|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**ScrollBars**|**По вертикали**|
    |`Button1`|**имя**;|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**имя**;|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Создание набора данных, который получает XML-данные

На этом шаге вы создадите новый набор данных с именем `authors` . Дополнительные сведения о наборах данных см. [в разделе Инструменты набора DataSet в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. В **Обозреватель решений** выберите исходный файл для **формы Form1**, а затем нажмите кнопку **конструктор представлений** на панели инструментов **Обозреватель решений** .

2. Перетащите **набор данных** из [панели элементов на вкладку "данные"](../ide/reference/toolbox-data-tab.md)на **форму Form1**.

3. В диалоговом окне **Добавление набора данных** выберите параметр **нетипизированный набор данных**, а затем нажмите кнопку **ОК**.

     **DataSet1** добавляется в область компонентов.

4. В окне **Свойства** задайте **имя** и <xref:System.Data.DataSet.DataSetName%2A> свойства для `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Создание обработчика событий для чтения XML-файла в наборе данных

Кнопка " **прочитать XML** " считывает XML-файл в наборе данных. Затем в нем устанавливаются свойства <xref:System.Windows.Forms.DataGridView> элемента управления, который привязывает его к набору данных.

1. В **Обозреватель решений** выберите **Form1**, а затем нажмите кнопку **конструктор представлений** на панели инструментов **Обозреватель решений** .

2. Нажмите кнопку **чтение XML** .

     **Редактор кода** откроется в `ReadXmlButton_Click` обработчике событий.

3. Введите следующий код в `ReadXmlButton_Click` обработчик событий:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb" id="Snippet2":::

4. В `ReadXMLButton_Click` коде обработчика событий измените `filepath =` запись на правильный путь.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Создание обработчика событий для вывода схемы в текстовое поле

Кнопка **Показать схему** создает <xref:System.IO.StringWriter> объект, который заполняется схемой и отображается в <xref:System.Windows.Forms.TextBox> элементе управления.

1. В **Обозреватель решений** выберите **Form1**, а затем нажмите кнопку **Конструктор представлений** .

2. Нажмите кнопку **отобразить схему** .

     **Редактор кода** откроется в `ShowSchemaButton_Click` обработчике событий.

3. Вставьте в обработчик события `ShowSchemaButton_Click` следующий код.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb" id="Snippet3":::

## <a name="test-the-form"></a>Тестирование формы

Теперь можно проверить форму, чтобы убедиться, что она ведет себя так, как ожидалось.

1. Нажмите **клавишу F5** , чтобы запустить приложение.

2. Нажмите кнопку **чтение XML** .

     Элемент DataGridView отображает содержимое XML-файла.

3. Нажмите кнопку **отобразить схему** .

     В текстовом поле отображается схема XML для XML-файла.

## <a name="next-steps"></a>Дальнейшие действия

В этом пошаговом руководстве рассматриваются основы чтения XML-файла в наборе данных, а также создание схемы на основе содержимого XML-файла. Ниже приведены некоторые задачи, которые можно выполнить далее.

- Изменить данные в наборе данных и записать их обратно в формате XML. Дополнительные сведения см. в разделе <xref:System.Data.DataSet.WriteXml%2A>.

- Измените данные в наборе данных и запишите их в базу данных.

## <a name="see-also"></a>См. также

- [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
