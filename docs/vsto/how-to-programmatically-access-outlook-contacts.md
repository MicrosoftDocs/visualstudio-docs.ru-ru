---
title: Руководство. программный доступ к контактам Outlook
description: Узнайте, как получить доступ к контактам Outlook программным способом. В этом примере выполняется поиск всех контактов, последние имена которых содержат указанную строку поиска.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 08e9d9ea69985a26a9688152f5c3b028caf75300
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828908"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Руководство. программный доступ к контактам Outlook
  В этом примере выполняется поиск всех контактов, последние имена которых содержат указанную строку поиска.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb" id="Snippet1":::


## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Контакты, последние имена которых содержат строку «**НД»** (например, Тзипи Бутнару) в папке « **Контакты** ».

## <a name="see-also"></a>См. также статью
- [Работа с элементами контактов](../vsto/working-with-contact-items.md)
- [Руководство. Программное добавление записи в контакты Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Руководство. Программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Руководство. Программный поиск адреса электронной почты в контактах](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Руководство. Программное удаление контактов Outlook](../vsto/how-to-programmatically-delete-outlook-contacts.md)
