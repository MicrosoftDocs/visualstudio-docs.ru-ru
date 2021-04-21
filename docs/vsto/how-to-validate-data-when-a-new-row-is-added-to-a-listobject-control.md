---
title: Проверять данные при добавлении новой строки в элемент управления ListObject
description: Узнайте, как можно использовать Visual Studio для проверки данных при добавлении новой строки в элемент управления ListObject.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a7002cdc0787850fc7be5a782f3cf3a2101d7593
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825723"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Как проверить данные при добавлении новой строки в элемент управления ListObject
  Пользователи могут добавлять новые строки в элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным. Вы можете проверять данные пользователя перед фиксацией изменений в источнике данных.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Проверка данных
 Каждый раз, когда строка добавляется в <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным, возникает событие <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> . Это событие можно обработать для выполнения проверки данных. Например, если приложению требуется, чтобы в источник данных можно было добавлять только сотрудников из 18 лет и 65, убедитесь, что введенный возраст находится в пределах диапазона перед добавлением строки.

> [!NOTE]
> Всегда следует проверять входные данные пользователя на сервере, как и на клиенте. Дополнительные сведения см. в разделе [безопасные клиентские приложения](/dotnet/framework/data/adonet/secure-client-applications).

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Проверка данных при добавлении новой строки в элемент управления ListObject с привязкой к данным

1. Создайте переменные для идентификатора и объекта <xref:System.Data.DataTable> на уровне класса.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet8":::

2. Создайте новый объект <xref:System.Data.DataTable> и добавьте в него образцы столбцов и данных в `Startup` обработчике событий `Sheet1` класса (в проекте уровня документа) или `ThisAddIn` в классе (в проекте надстройки VSTO).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet9":::

3. Добавьте код в обработчик событий `list1_BeforeAddDataBoundRow` , чтобы проверить, попадает ли возраст в допустимый диапазон.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet10":::

## <a name="compile-the-code"></a>Компиляция кода
 В этом примере кода предполагается, что в листе, в котором этот код появляется, имеется существующий элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `list1` .

## <a name="see-also"></a>См. также статью
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Элемент управления ListObject](../vsto/listobject-control.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Как сопоставлять столбцы ListObject с данными](../vsto/how-to-map-listobject-columns-to-data.md)
