---
title: Руководство. Программное открытие текстовых файлов в виде книг
description: Узнайте, как можно использовать Visual Studio для программного открытия текстового файла в виде книги Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14a73d7a06c3d79c15df5b823b38efc9ddceb846
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824176"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Руководство. Программное открытие текстовых файлов в виде книг
  Можно открыть текстовый файл в виде книги. Необходимо передать имя текстового файла, который необходимо открыть. Можно указать несколько необязательных параметров, например номер строки для начала синтаксического анализа и формат столбцов данных в файле.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Пример
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet80":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet80":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются следующие компоненты:

- Текстовый файл с разделителями-запятыми `Test.txt` , содержащий по крайней мере три строки текста.

- Текстовый файл `Test.txt` , который будет сохранен на диске C.

## <a name="see-also"></a>См. также статью
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Руководство. Программное открытие книг](../vsto/how-to-programmatically-open-workbooks.md)
- [Как создать новые книги программным способом](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Как программно сохранять книги](../vsto/how-to-programmatically-save-workbooks.md)
- [Руководство. программное закрытие книг](../vsto/how-to-programmatically-close-workbooks.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
