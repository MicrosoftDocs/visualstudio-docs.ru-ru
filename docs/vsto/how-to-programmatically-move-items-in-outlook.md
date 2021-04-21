---
title: Руководство. Программное перемещение элементов в Outlook
description: Сведения о программном перемещении элементов в Microsoft Outlook. В этом примере из папки "Входящие" перемещаются непрочитанные сообщения электронной почты в папку с именем Test.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b8e951ab393d09506ad4f2d593962ea1826eff09
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826737"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Руководство. Программное перемещение элементов в Outlook
  В этом примере из папки **"Входящие"** перемещаются непрочитанные сообщения электронной почты в папку с именем **Test**. В этом примере в поле перемещаются только те сообщения, которые содержат слово **Test** `Subject` .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Папка почты Outlook с именем **Test**.

- Сообщение электронной почты, поступающие по слову **Test** в `Subject` поле.

## <a name="see-also"></a>См. также статью
- [Работа с папками](../vsto/working-with-folders.md)
- [Как программно получить папку по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Руководство. Программный поиск в определенной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Руководство. программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
