---
title: Руководство. Программный поиск в определенной папке
description: Узнайте, как можно использовать Visual Studio для программного поиска в определенной папке Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b25880420e23b82f6f63ab28ef5f1f93429bdd8c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824761"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Руководство. Программный поиск в определенной папке
  В этом примере кода используются `Find` `FindNext` методы и для поиска текста в поле subject сообщений электронной почты, которые находятся в **папке Входящие**. Этот метод использует фильтр строк для проверки буквы T в качестве начальной буквы `Subject` текста.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>См. также
- [Работа с папками](../vsto/working-with-folders.md)
- [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)
- [Как программно получить папку по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
