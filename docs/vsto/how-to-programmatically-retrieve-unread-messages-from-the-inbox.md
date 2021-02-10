---
title: Программно получать непрочитанные сообщения из папки "Входящие"
description: Узнайте, как можно использовать Visual Studio для программного получения непрочитанных сообщений из папки "Входящие" в Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], unread mail
- Outlook [Office development in Visual Studio], unread mail
- unread e-mail
- mail items [Office development in Visual Studio], unread mail
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 82bd595b76a03ee730995e546fd9c4e827c95a53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953855"
---
# <a name="how-to-programmatically-retrieve-unread-messages-from-the-inbox"></a>Руководство. Программное получение непрочитанных сообщений из папки "Входящие"
  В этом примере извлекаются непрочитанные сообщения электронной почты из **папки "Входящие"** Outlook и отображается количество элементов.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-vb[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_UnreadItems/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_UnreadItems/thisaddin.cs#1)]

## <a name="see-also"></a>См. также раздел
- [Работа с элементами почты](../vsto/working-with-mail-items.md)
- [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Руководство. Программное создание элемента электронной почты](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Руководство. Программная отправка электронной почты](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Руководство. программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
