---
title: Как программно создавать новые документы Visio
description: Узнайте, как программным способом создать новый документ документа Microsoft Visio и добавить его в коллекцию документов открытых документов Visio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4b12b7e94109391928ad7c83387917e5934ae1c7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825320"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Как программно создавать новые документы Visio
  При создании нового документа Microsoft Office Visio вы добавляете его в коллекцию `Microsoft.Office.Interop.Visio.Documents` открытых документов Visio. Соответственно, метод `Microsoft.Office.Interop.Visio.Documents.Add` создает новый документ Visio. Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) .

## <a name="create-new-blank-documents"></a>Создание новых пустых документов

### <a name="to-create-a-new-document"></a>Создание нового документа

- Используйте метод `Microsoft.Office.Interop.Visio.Documents.Add` для создания нового пустого документа не на основе шаблона.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="create-documents-copied-from-existing-documents"></a>Создание документов, скопированных из существующих документов
 Метод `Microsoft.Office.Interop.Visio.Documents.Add` может создать новый документ, который является копией существующего документа Visio. Вы должны указать имя файла и полный путь к диаграмме.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Создание нового документа, скопированного из существующего документа

- Вызовите метод `Microsoft.Office.Interop.Visio.Documents.Add` и укажите путь к диаграмме Visio.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet2":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="create-stencils-copied-from-existing-stencils"></a>Создание наборов элементов, скопированных из существующих наборов элементов
 Метод [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) может создать новый набор элементов, который является копией существующего набора элементов Visio. Вы должны указать имя файла и полный путь к набору элементов.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Создание нового набора элементов, скопированного из существующего набора элементов

- Вызовите метод `Microsoft.Office.Interop.Visio.Documents.Add` и укажите путь к набору элементов.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="create-documents-based-on-existing-templates"></a>Создание документов на основе существующих шаблонов
 `Microsoft.Office.Interop.Visio.Documents.Add`Метод может создать новый документ ( *VSD* -файл), основанный на существующем шаблоне Visio (файл *VST* ). Этот метод копирует наборы элементов, стили и параметры, которые являются частью рабочей области шаблона. Необходимо указать имя файла и полный путь к шаблону.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Создание нового документа на основе существующего шаблона

- Вызовите метод `Microsoft.Office.Interop.Visio.Documents.Add` и укажите путь к шаблону.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера кода требуется следующее.

- Документ Visio с именем `myDrawing.vsd` должен находиться в каталоге с именем `Test` в папке " *Мои документы* " (для Windows XP и более ранних версий) или в папке " *документы* " (для Windows Vista).

- Документ Visio с именем `myStencil.vss` должен находиться в каталоге с именем `Test` в папке " *Мои документы* " (для Windows XP и более ранних версий) или в папке " *документы* " (для Windows Vista).

- Документ Visio с именем `myTemplate.vst` должен находиться в каталоге с именем `Test` в папке " *Мои документы* " (для Windows XP и более ранних версий) или в папке " *документы* " (для Windows Vista).

## <a name="see-also"></a>См. также статью
- [Решения Visio](../vsto/visio-solutions.md)
- [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Руководство. Программное открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Руководство. программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Как программно сохранять документы Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)
