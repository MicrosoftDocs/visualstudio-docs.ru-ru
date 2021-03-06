---
title: Конструктор действий TransactionScope конструктор рабочих процессов
description: Узнайте, как можно использовать конструктор операций TransactionScope для создания и настройки действия TransactionScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 234e6c2d0349cf610d9ba22d53ce59e3768ad64e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838013"
---
# <a name="transactionscope-activity-designer"></a>Конструктор действия TransactionScope

Конструктор действий **TransactionScope** используется для создания и настройки <xref:System.Activities.Statements.TransactionScope> действия.

## <a name="the-transactionscope-activity"></a>Действие TransactionScope

Действие <xref:System.Activities.Statements.TransactionScope> выполняет вложенное действие за одну транзакцию. Транзакция фиксируется, после того как действие <xref:System.Activities.Statements.TransactionScope.Body%2A> и все другие участники транзакции успешно завершаются.

### <a name="using-the-transactionscope-activity-designer"></a>Использование конструктора операций TransactionScope

Доступ к конструктору операций **TransactionScope** в категории " **транзакция** " **панели элементов**. Конструктор операций **TransactionScope** можно перетащить из **панели элементов** в конструктор рабочих процессов область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . Будет создано действие <xref:System.Activities.Statements.TransactionScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TransactionScope. <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора операций **TransactionScope** или в поле **DisplayName** сетки свойств.

### <a name="the-transactionscope-properties"></a>Свойства TransactionScope

В следующей таблице показаны свойства <xref:System.Activities.Statements.TransactionScope> и описано их использование в конструкторе. <xref:System.Activities.Activity.DisplayName%2A>Свойства и <xref:System.Activities.Statements.TransactionScope.Body%2A> можно изменить на поверхности конструктор рабочих процессов. Но другие свойства следует изменять в таблице свойств.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.TransactionScope>. По умолчанию выбрано значение TransactionScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Указывает действие, которое следует выполнить за одну транзакцию. Чтобы добавить <xref:System.Activities.Statements.TransactionScope.Body%2A> действие, перетащите действие из **области элементов** в поле **текст** в конструкторе операций **TransactionScope** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Задает <xref:System.Transactions.IsolationLevel> для объекта <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Задает интервал времени (в формате 00:00:00, что означает часы:минуты:секунды), в течение которого транзакция должна завершиться. Значение по умолчанию - 1 минута (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure*>|True|Задает значение, которое указывает, следует ли прерывать рабочий процесс, если прервана транзакция.|

## <a name="see-also"></a>См. также раздел

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Уточнит](../workflow-designer/confirm-activity-designer.md)
