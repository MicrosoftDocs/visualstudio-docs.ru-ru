---
title: Сохранение набора данных в формате XML
description: Сохранение набора данных в формате XML. Доступ к XML-данным в наборе данных осуществляется путем вызова доступных методов XML для набора данных, например GetXml или WriteXml.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 42974852a3051fd3473b6b23d880eeb38b966b95
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216206"
---
# <a name="save-a-dataset-as-xml"></a>Сохранение набора данных в формате XML

Доступ к XML-данным в наборе данных осуществляется путем вызова доступных методов XML в наборе данных. Чтобы сохранить данные в формате XML, можно вызвать либо <xref:System.Data.DataSet.GetXml%2A> метод, либо <xref:System.Data.DataSet.WriteXml%2A> метод объекта <xref:System.Data.DataSet> .

При вызове <xref:System.Data.DataSet.GetXml%2A> метода возвращается строка, содержащая данные из всех таблиц данных в наборе данных, отформатированном как XML.

При вызове <xref:System.Data.DataSet.WriteXml%2A> метода данные в формате XML отправляются в указанный файл.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Сохранение данных в наборе данных в виде XML-файла в переменную

- Метод <xref:System.Data.DataSet.GetXml%2A> возвращает <xref:System.String>. Объявите переменную типа <xref:System.String> и присвойте ей результаты <xref:System.Data.DataSet.GetXml%2A> метода.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet12":::

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Сохранение данных в наборе данных в виде XML-файла

- <xref:System.Data.DataSet.WriteXml%2A>Метод имеет несколько перегрузок. Объявите переменную и присвойте ей допустимый путь для сохранения файла. В следующем примере кода показано, как сохранить данные в файл:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet13":::

## <a name="see-also"></a>См. также раздел

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
