---
title: Сохранение динамических элементов управления в документах Office
description: Узнайте, как добавить в решение код для повторного создания постоянных динамических элементов управления, когда пользователь повторно открывает закрытый документ.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9d42aa2d8594ed44e4fd4edbac8a0d64c4dc16da
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826152"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Сохранение динамических элементов управления в документах Office

Элементы управления, добавленные во время выполнения, не сохраняются при сохранении и закрытии документа или книги. Точное поведение элементов управления ведущего приложения и Windows Forms различается. В обоих случаях можно добавить в решение код для повторного создания элементов управления при повторном открытии документа.

Элементы управления, добавляемые в документы во время выполнения, называются *динамическими элементами управления*. Дополнительные сведения о динамических элементах управления см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Сохранение элементов управления ведущего приложения в документе

Если сохранить и закрыть документ, все динамические элементы управления ведущего приложения будут удалены из документа. Останутся только базовые собственные объекты Office. Например, элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> превращается в <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName>. Собственные объекты Office не подключены к событиям элементов управления ведущего приложения и не имеют функций привязки к данным элемента управления ведущего приложения.

В следующей таблице перечислены собственные объекты Office, которые остаются в документе после всех типов элементов управления ведущего приложения.

|Тип элемента управления ведущего приложения|Тип собственного объекта Office|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Повторное создание динамических элементов управления ведущего приложения при открытии документов

Динамические элементы управления ведущего приложения можно повторно создавать вместо существующих собственных элементов управления при каждом открытии документа пользователем. Создание элементов управления ведущего приложения при открытии документа имитирует поведение, на которое могут рассчитывать пользователи.

Чтобы повторно создать элемент управления ведущего приложения для Word, или <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> элемент управления ведущего приложения для Excel, используйте `Add` \<*control class*> метод <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> объекта или. Используйте метод, имеющий параметр для собственного объекта Office.

Например, если вы хотите создать элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> из существующего собственного <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> при открытии документа, используйте метод <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> и передайте существующий <xref:Microsoft.Office.Interop.Excel.ListObject>. В следующем примере кода показано, как сделать это в проекте уровня документа для Excel. Код повторно создает динамический <xref:Microsoft.Office.Tools.Excel.ListObject> , основанный на существующем <xref:Microsoft.Office.Interop.Excel.ListObject> с именем `MyListObject` в классе `Sheet1` .

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs" id="Snippet6":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb" id="Snippet6":::

### <a name="re-create-chart"></a>Повторное создание диаграммы

Чтобы повторно создать <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> элемент управления ведущего приложения, сначала необходимо удалить машинный код <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> , а затем повторно создать с <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> помощью <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> метода. Нет `Add` \<*control class*> метода, который позволяет создать новый <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> на основе существующего <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> .

Если не удалить собственный объект <xref:Microsoft.Office.Interop.Excel.Chart> , то при повторном создании диаграммы будет создана вторая Повторяющаяся диаграмма <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> .

## <a name="persist-windows-forms-controls-in-documents"></a>Сохранение Windows Forms элементов управления в документах

Если сохранить и закрыть документ, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] автоматически удалит все динамически созданные элементы управления Windows Forms из документа. При этом на уровне проектов уровня документа и надстроек VSTO поведение отличается.

В настройках уровня документа элементы управления и их базовые оболочки ActiveX (которые используются для размещения элементов управления в документе) удаляются при следующем открытии документа. Признаков присутствия элементов управления не остается.

В надстройках VSTO элементы управления удаляются, но оболочки ActiveX остаются в документе. Когда пользователь откроет документ в следующий раз, оболочки ActiveX останутся видны. В Excel оболочки ActiveX содержат изображения элементов управления в том виде, как они выглядели в момент последнего сохранения документа. В Word оболочки ActiveX невидимы, пока пользователь не щелкнет их. После этого в них отображается пунктирная линия, представляющая границы элементов управления. Существует несколько способов удаления оболочек ActiveX. Дополнительные сведения см. [в разделе Удаление оболочек ActiveX в надстройке](#removingActiveX).

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Повторное создание Windows Forms элементов управления при открытии документов

Удаленные элементы управления Windows Forms можно повторно создать при повторном открытии документа. Для этого в решении следует выполнять следующие задачи.

1. Сохранять информацию о размере, расположении и состоянии элементов управления при сохранении или закрытии документа. В настройке на уровне документа данные можно сохранить в кэше данных в документе. В надстройке VSTO данные можно сохранить в пользовательской XML-части документа.

2. Повторно создавать элементы управления в событии, которое возникает при открытии документа. В проектах уровня документа это можно сделать в `Sheet`  `_Startup` `ThisDocument_Startup` обработчиках событий n или. В проекте надстройки VSTO это можно сделать в обработчиках событий <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> или <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

### <a name="remove-activex-wrappers-in-an-add-in"></a><a name="removingActiveX"></a> Удаление оболочек ActiveX в надстройке

При добавлении в документы динамических Windows Forms элементов управления с помощью надстройки VSTO можно запретить отображение оболочек ActiveX для элементов управления в документе при следующем его открытии следующим образом.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>Удаление оболочек ActiveX при открытии документа

Чтобы удалить все оболочки ActiveX, вызовите метод `GetVstoObject` для создания ведущего элемента <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Workbook>, который представляет открытый документ. Например, чтобы удалить все оболочки ActiveX из документа Word, можно вызвать метод `GetVstoObject` для создания ведущего элемента объекта <xref:Microsoft.Office.Interop.Word.Document>, который передается в обработчик событий для события <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.

Эта процедура полезна, когда известно, что документ будет открываться только на компьютерах, где установлена надстройка VSTO. Если документ может быть передан другим пользователям, у которых не установлена надстройка VSTO, рекомендуется удалять элементы управления перед закрытием документа.

В следующем примере кода показано, как вызвать метод `GetVstoObject` при открытии документа.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet11":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet11":::

Хотя `GetVstoObject` метод используется в основном для создания нового ведущего элемента во время выполнения, этот метод также удаляет все оболочки ActiveX из документа при первом вызове для конкретного документа. Дополнительные сведения об использовании `GetVstoObject` метода см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

Если надстройка VSTO создает динамические элементы управления при открытии документа, Надстройка VSTO уже вызовет `GetVstoObject` метод как часть процесса создания элементов управления. В этом случае не нужно добавлять отдельный вызов метода `GetVstoObject`, чтобы удалить все оболочки ActiveX.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Удалить динамические элементы управления перед закрытием документа

Надстройка VSTO может явным образом удалить все динамические элементы управления из документа до его закрытия. Эта процедура полезна для документов, передаваемых другим пользователям, у которых не установлена надстройка VSTO.

В следующем примере кода демонстрируется удаление всех элементов управления Windows Forms из документа Word при его закрытии.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet10":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet10":::

## <a name="see-also"></a>См. также статью

- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
