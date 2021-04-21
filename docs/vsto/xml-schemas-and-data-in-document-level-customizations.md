---
title: XML-схемы и данные в настройках уровня документа
description: Microsoft Excel и Word предоставляют возможность сопоставлять схемы с документами, а также упрощают импорт и экспорт XML-данных в документ и из него.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 54e993f41787cfa44bb0aaa78cc7aff8fbad53d8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826594"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>XML-схемы и данные в настройках уровня документа
  **Важно!** Сведения, приведенные в этом разделе о Microsoft Word, предоставляются исключительно для использования в качестве преимуществ и применения частных лиц и организаций, которые находятся за пределами США и его территорий, а также для разработки программ, работающих на платформе Microsoft Word, которые были лицензированы корпорацией Майкрософт до января 2010, когда корпорация Майкрософт удалила реализацию определенных функций, связанных с пользовательским XML-кодом из Microsoft Word Эти сведения, касающиеся Microsoft Word, могут быть не прочитаны или использованы людьми или организациями в США или на ее территориях, которые используют или разрабатывают программные продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г. Эти продукты не будут работать так же, как продукты, лицензированные до этой даты или приобретенные и лицензированные для использования за пределами США.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel и Microsoft Office Word предоставляют возможность сопоставлять схемы с документами. Эта функция может упростить импорт и экспорт XML-данных в документ и из него.

 Visual Studio предоставляет сопоставленные элементы схемы в настройках уровня документа в виде элементов управления в модели программирования. Для Excel в Visual Studio добавлена поддержка привязки элементов управления к данным в базах данных, веб-службах и объектах. Для Word и Excel в Visual Studio добавлена поддержка панелей действий, которые можно использовать с документом, сопоставленным с схемами, чтобы создать усовершенствованное взаимодействие с конечным пользователем для ваших решений. Дополнительные сведения см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md).

> [!NOTE]
> В решениях Excel нельзя использовать составные XML-схемы.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Объекты, созданные при присоединении схем к книгам Excel
 При присоединении схемы к книге Visual Studio автоматически создает несколько объектов и добавляет их в проект. Эти объекты не следует удалять с помощью инструментов Visual Studio, так как они управляются Excel. Чтобы удалить их, удалите сопоставленные элементы с листа или отключите схему с помощью средств Excel.

 Существует два основных объекта:

- Схема XML (XSD-файл). Для каждой схемы в книге Visual Studio добавляет в проект схему. Он отображается как элемент проекта с расширением XSD в **Обозреватель решений**.

- Типизированный класс <xref:System.Data.DataSet>. Этот класс создается на основе схемы. Этот класс набора данных отображается в **представление классов**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Объекты, созданные при сопоставлении элементов схемы с листами Excel
 При сопоставлении элемента схемы из области задач **Источник XML** с листом Visual Studio автоматически создает несколько объектов и добавляет их в проект:

- Элементы управления. Для каждого сопоставленного объекта в книге в <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> модели программирования создается элемент управления (для неповторяющихся элементов схемы) или <xref:Microsoft.Office.Tools.Excel.ListObject> элемент управления (для повторяющихся элементов схемы). <xref:Microsoft.Office.Tools.Excel.ListObject>Элемент управления может быть удален только путем удаления сопоставлений и сопоставленных объектов из книги. Дополнительные сведения об элементах управления см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).

- Источников. При создании <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> с помощью сопоставления неповторяющегося элемента схемы с листом <xref:System.Windows.Forms.BindingSource> создается, а <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элемент управления привязывается к <xref:System.Windows.Forms.BindingSource> . Необходимо привязать <xref:System.Windows.Forms.BindingSource> к экземпляру источника данных, который соответствует схеме, сопоставленной с документом, например экземпляр типизированного <xref:System.Data.DataSet> класса, который был создан. Создайте привязку, задав <xref:System.Windows.Forms.BindingSource.DataSource%2A> Свойства и <xref:System.Windows.Forms.BindingSource.DataMember%2A> , которые отображаются в окне **Свойства** .

    > [!NOTE]
    > Объект <xref:System.Windows.Forms.BindingSource> не создается для <xref:Microsoft.Office.Tools.Excel.ListObject> объектов. Необходимо вручную привязать <xref:Microsoft.Office.Tools.Excel.ListObject> к источнику данных, задав <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> Свойства и в окне " **Свойства** ".

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Сопоставленные схемы Office и окно "источники данных" Visual Studio
 Функции сопоставленной схемы Office и окна **источников данных** Visual Studio позволяют представлять данные на листе Excel для создания отчетов или редактирования. В обоих случаях элементы данных можно перетаскивать на лист Excel. Оба метода создают элементы управления, которые являются данными, привязанными через, <xref:System.Windows.Forms.BindingSource> к источнику данных, например к <xref:System.Data.DataSet> или веб-службе.

> [!NOTE]
> При сопоставлении повторяющегося элемента схемы с листом Visual Studio создает <xref:Microsoft.Office.Tools.Excel.ListObject> . <xref:Microsoft.Office.Tools.Excel.ListObject>Не привязывается автоматически к данным через <xref:System.Windows.Forms.BindingSource> . Необходимо вручную привязать <xref:Microsoft.Office.Tools.Excel.ListObject> к источнику данных, задав <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> Свойства и в окне " **Свойства** ".

 В следующей таблице показаны некоторые различия между двумя методами.

|схема XML|Источники данных - окно|
|----------------|-------------------------|
|Использует интерфейс Office.|Использует окно **Источники данных** в Visual Studio.|
|Включает встроенные функции Office для импорта и экспорта данных из XML-файлов.|Функции импорта и экспорта необходимо предоставлять программно.|
|Необходимо написать код для заполнения созданных элементов управления данными.|Элементы управления, добавленные из окна **Источники данных** , автоматически генерируют код для их заполнения, а также необходимые строки подключения при использовании серверов баз данных.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Поведение при присоединении схем к документам Word
 Объекты данных не создаются при присоединении схемы к документу Word, который используется в проекте Office на уровне документа. Однако при сопоставлении элемента схемы с документом создаются элементы управления. Тип элемента управления зависит от типа сопоставляемого элемента; повторяющиеся элементы создают <xref:Microsoft.Office.Tools.Word.XMLNodes> элементы управления и неповторяющиеся элементы создают <xref:Microsoft.Office.Tools.Word.XMLNode> элементы управления. Дополнительные сведения см. в разделе [элементы управления XMLNodes](../vsto/xmlnodes-control.md) и [XmlNode](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Развертывание решений, включающих XML-схемы
 Необходимо создать установщик для развертывания решения, использующего схему XML, сопоставленную с документом. Установщик должен зарегистрировать схему в библиотеке схем на компьютере пользователя. Если схема не зарегистрирована, решение по-прежнему будет работать, поскольку Word создает временную схему на основе элементов, которые находятся в документе при его открытии пользователем. Однако пользователь не сможет выполнить проверку или сохранить схему, которая использовалась для создания проекта. Дополнительные сведения об установщиках см. в разделе [развертывание приложений, служб и компонентов](../deployment/deploying-applications-services-and-components.md).

 Можно также добавить код в проект, чтобы проверить, находится ли схема в библиотеке и зарегистрирована. Если это не так, можно предупредить пользователя.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs" id="Snippet1":::

## <a name="see-also"></a>См. также статью

- [Как сопоставлять схемы с документами Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Как сопоставлять схемы с листами в Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
