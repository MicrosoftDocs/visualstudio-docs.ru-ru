---
title: Фильтрация и сортировка данных в приложении Windows Forms
description: Фильтрация и сортировка данных в приложении Windows Forms. Задайте для свойства фильтра строковое выражение, возвращающее нужные записи.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 045da0ade1ce60e2a8d21c24238c8e2b061e8612
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215829"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Фильтрация и сортировка данных в приложении Windows Forms

Данные фильтруются путем присвоения <xref:System.Windows.Forms.BindingSource.Filter%2A> свойству строкового выражения, возвращающего нужные записи.

Данные сортируются путем присвоения <xref:System.Windows.Forms.BindingSource.Sort%2A> свойству имени столбца, по которому нужно выполнить сортировку; добавление `DESC` в сортировку в убывающем порядке или добавление `ASC` к сортировке по возрастанию.

> [!NOTE]
> Если приложение не использует <xref:System.Windows.Forms.BindingSource> компоненты, можно фильтровать и сортировать данные с помощью <xref:System.Data.DataView> объектов. Дополнительные сведения см. в разделе " [представления](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)данных".

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Фильтрация данных с помощью компонента BindingSource

- Задайте <xref:System.Windows.Forms.BindingSource.Filter%2A> для свойства выражение, которое требуется вернуть. Например, следующий код возвращает клиентов с `CompanyName` , который начинается с "B":

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet6":::

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Сортировка данных с помощью компонента BindingSource

- Задайте <xref:System.Windows.Forms.BindingSource.Sort%2A> для свойства столбец, по которому необходимо выполнить сортировку. Например, следующий код сортирует клиентов по `CompanyName` столбцу в убывающем порядке:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>См. также раздел

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
