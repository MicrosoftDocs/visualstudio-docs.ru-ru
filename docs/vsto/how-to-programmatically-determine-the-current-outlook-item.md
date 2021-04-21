---
title: Руководство. Программное определение текущего элемента Outlook
description: Узнайте, как программным способом определить текущий элемент Microsoft Outlook. В этом примере используется событие Explorer. SelectionChange.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9cddc4bdc99e97c12a04e57639f990a1484c6581
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823933"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Руководство. Программное определение текущего элемента Outlook
  В этом примере используется `Explorer.SelectionChange` событие для вывода имени текущей папки и некоторых сведений о выбранном элементе. Затем код отображает выбранный элемент.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Встречи, контакты и элементы электронной почты в Microsoft Office Outlook.

## <a name="see-also"></a>См. также статью
- [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)
- [Как программно получить папку по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Руководство. Программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
