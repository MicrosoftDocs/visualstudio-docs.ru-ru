---
title: Как добавить элементы управления ListObject на листы
description: Узнайте, как можно добавлять элементы управления ListObject в Microsoft Office лист Excel во время разработки и во время выполнения в проектах уровня документа.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 077ff2e92455df283dfcaeddd7171e1f86698e6b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827894"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Как добавить элементы управления ListObject на листы
  Элементы управления <xref:Microsoft.Office.Tools.Excel.ListObject> можно добавлять в лист Microsoft Office Excel во время разработки и во время выполнения в проектах на уровне документа.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Элементы управления <xref:Microsoft.Office.Tools.Excel.ListObject> также можно добавлять во время выполнения в проектах надстроек VSTO.

 В этом разделе описываются следующие задачи.

- [Добавление элементов управления ListObject во время разработки](#designtime)

- [Добавление элементов управления ListObject во время выполнения в проекте уровня документа](#runtimedoclevel)

- [Добавление элементов управления ListObject во время выполнения в проекте надстройки VSTO](#runtimeaddin)

  Дополнительные сведения об элементах <xref:Microsoft.Office.Tools.Excel.ListObject> управления см. в разделе [элемент управления ListObject](../vsto/listobject-control.md).

## <a name="add-listobject-controls-at-design-time"></a><a name="designtime"></a> Добавление элементов управления ListObject во время разработки
 Существует несколько способов добавления <xref:Microsoft.Office.Tools.Excel.ListObject> элементов управления на лист в проекте уровня документа во время разработки: из Excel, из **панели элементов** Visual Studio и из окна **Источники данных** .

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-use-the-ribbon-in-excel"></a>Использование ленты в Excel

1. На вкладке **Вставка** в группе **Таблицы** щелкните элемент **Таблица**.

2. Выделите ячейки, которые хотите включить в список, и нажмите кнопку **ОК**.

#### <a name="to-use-the-toolbox"></a>Использование панели элементов

1. Из вкладки **Элементы управления Excel** на **панели элементов** перетащите <xref:Microsoft.Office.Tools.Excel.ListObject> в лист.

     Откроется диалоговое окно **Добавление элемента управления ListObject** .

2. Выделите ячейки, которые хотите включить в список, и нажмите кнопку **ОК**.

     Если вы не хотите использовать имя по умолчанию, измените его в окне **Свойства** .

#### <a name="to-use-the-data-sources-window"></a>Использование окна "Источники данных".

1. Откройте окно **Источники данных** и создайте источник данных для проекта. Дополнительные сведения см. в разделе [Добавление новых соединений](../data-tools/add-new-connections.md).

2. Перетащите таблицу из окна **Источники данных** в лист.

     Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным добавится в лист. Дополнительные сведения см. в разделе [Привязка данных и Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="add-listobject-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Добавление элементов управления ListObject во время выполнения в проекте уровня документа
 Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> можно добавлять динамически во время выполнения. Это позволяет создавать элементы управления ведущего приложения при возникновении определенных событий. При закрытии листа динамически созданные объекты списка не сохраняются на листе как элементы управления ведущего приложения. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Добавление элемента управления ListObject в лист программными средствами

1. В обработчике событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> для `Sheet1`вставьте следующий код, чтобы добавить элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> в ячейки с **A1** до **A4**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet2":::

## <a name="add-listobject-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Добавление элементов управления ListObject во время выполнения в проекте надстройки VSTO
 Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> можно добавить программным образом на любой открытый лист в проекте надстройки VSTO. При сохранении и закрытии листа динамически созданные объекты списка не сохраняются на листе как элементы управления ведущего приложения. Дополнительные сведения см. [в разделе Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Добавление элемента управления ListObject в лист программными средствами

1. Следующий код создает ведущий элемент листа, который основан на открытом листе, а затем добавляет элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> в ячейки с **A1** до **A4**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet8":::

## <a name="see-also"></a>См. также статью
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Элемент управления ListObject](../vsto/listobject-control.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Как изменить размер элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
