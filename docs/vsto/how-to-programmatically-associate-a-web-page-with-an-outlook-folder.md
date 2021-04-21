---
title: Связывание веб-страницы с папкой Outlook
description: Узнайте, как связать веб-страницу с Microsoft Office папке Outlook. В этом примере проверяется наличие папки с именем Хтмлвиев в Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3f022deca9b8cd1b8f00bf847ab0bfdc7882a45f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828271"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Связывание веб-страницы с папкой Outlook

  В этом примере проверяется наличие папки с именем `HtmlView` в Microsoft Office Outlook. Если папка не существует, код создает папку и назначает ей веб-страницу. Если папка существует, в коде отображается содержимое папки.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>См. также
- [Работа с папками](../vsto/working-with-folders.md)
- [Как программно получить папку по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Руководство. Программное создание пользовательских элементов папки](../vsto/how-to-programmatically-create-custom-folder-items.md)
