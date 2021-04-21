---
title: Как программно получить папку по имени
description: Узнайте, как можно использовать Visual Studio для программного извлечения папки по имени и последующего отображения содержимого папки.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c947395b67fca15e06e1164dc25ab2dc8fa3209d
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823952"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>Как программно получить папку по имени
  В этом примере возвращается ссылка на именованную пользовательскую папку, а затем отображается ее содержимое.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Папка с именем TestFolder.

## <a name="see-also"></a>См. также статью
- [Работа с папками](../vsto/working-with-folders.md)
- [Руководство. Программный поиск в определенной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Руководство. Программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Руководство. Программное создание пользовательских элементов папки](../vsto/how-to-programmatically-create-custom-folder-items.md)
