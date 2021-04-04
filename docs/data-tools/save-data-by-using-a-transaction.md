---
title: Практическое руководство. Сохранение данных с помощью транзакции
description: Узнайте, как сохранить данные с помощью транзакции с инструментами набора данных в Visual Studio. Данные сохраняются в транзакции с помощью пространства имен System. Transactions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c22a0cc9b0b9d37a4d725aa8ce494646e7779f0f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216076"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Практическое руководство. Сохранение данных с помощью транзакции

Данные сохраняются в транзакции с помощью <xref:System.Transactions> пространства имен. Используйте <xref:System.Transactions.TransactionScope> объект для участия в транзакции, которая автоматически управляется.

Проекты не создаются со ссылкой на сборку *System. Transactions* , поэтому необходимо вручную добавить ссылку на проекты, использующие транзакции.

Самый простой способ реализовать транзакцию — создать экземпляр <xref:System.Transactions.TransactionScope> объекта в `using` операторе. (Дополнительные сведения см. в разделе [оператор using](/dotnet/visual-basic/language-reference/statements/using-statement)и [оператор using](/dotnet/csharp/language-reference/keywords/using-statement).) Код, выполняемый внутри `using` инструкции, участвует в транзакции.

Чтобы зафиксировать транзакцию, вызовите <xref:System.Transactions.TransactionScope.Complete%2A> метод в качестве последней инструкции в блоке using.

Чтобы выполнить откат транзакции, вызовите исключение перед вызовом <xref:System.Transactions.TransactionScope.Complete%2A> метода.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Добавление ссылки на System.Transactions.dll

1. В меню **Проект** выберите пункт **Добавить ссылку**.

2. На вкладке **.NET** (вкладка "**SQL Server** " для SQL Server проектов) выберите **System. Transactions** и нажмите кнопку **ОК**.

     Ссылка на *System.Transactions.dll* добавляется в проект.

## <a name="to-save-data-in-a-transaction"></a>Сохранение данных в транзакции

- Добавьте код для сохранения данных в инструкции using, содержащей транзакцию. В следующем коде показано, как создать объект и создать его экземпляр <xref:System.Transactions.TransactionScope> в операторе using:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet11":::

## <a name="see-also"></a>См. также раздел

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
- [Пошаговое руководство. Сохранение данных в транзакции](../data-tools/save-data-in-a-transaction.md)
