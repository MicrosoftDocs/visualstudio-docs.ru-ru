---
title: Кэширование источника данных в документе Office программным способом
description: Узнайте, как программным способом добавить объект данных в кэш данных в документе путем вызова метода Старткачинг ведущего элемента.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 070253fb7ec57bedad628e116ce193fa2d9cf50b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827595"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Руководство. программный кэш источника данных в документе Office
  Можно программно добавить объект данных в кэш данных в документе, вызвав `StartCaching` метод ведущего элемента, например <xref:Microsoft.Office.Tools.Word.Document> , <xref:Microsoft.Office.Tools.Excel.Workbook> или <xref:Microsoft.Office.Tools.Excel.Worksheet> . Удалите объект данных из кэша данных, вызвав `StopCaching` метод ведущего элемента.

 `StartCaching`Метод и `StopCaching` метод являются частными, но они отображаются в IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 При использовании `StartCaching` метода для добавления объекта данных в кэш данных объект данных не должен объявляться с <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> атрибутом. Однако объект данных должен соответствовать определенным требованиям для добавления в кэш данных. Дополнительные сведения см. в разделе [кэширование данных](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Кэширование объекта данных программными средствами

1. Объявите объект данных на уровне класса, а не внутри метода. В этом примере предполагается, что вы объявили <xref:System.Data.DataSet> именованный объект `dataSet1` , который требуется кэшировать программно.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet12":::

2. Создайте экземпляр объекта данных, а затем вызовите `StartCaching` метод документа или экземпляра листа и передайте имя объекта данных.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet13":::

## <a name="to-stop-caching-a-data-object"></a>Отмена кэширования объекта данных

1. Вызовите `StopCaching` метод документа или экземпляра листа и передайте имя объекта данных. В этом примере предполагается, что у вас есть <xref:System.Data.DataSet> имя `dataSet1` , для которого необходимо прерывать кэширование.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet14":::

    > [!NOTE]
    > Не вызывайте `StopCaching` из обработчика событий для `Shutdown` события документа или листа. К моменту `Shutdown` возникновения события слишком поздно изменять кэш данных. Дополнительные сведения о `Shutdown` событии см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>См. также статью

- [Кэширование данных](../vsto/caching-data.md)
- [Как кэшировать данные для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Пошаговое руководство. кэширование данных в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md)
- [Сохранение данных](../data-tools/save-data-back-to-the-database.md)
