---
title: Незафиксированные изменения
description: Фиксация в процессе изменений в элементах управления Windows Forms, привязанных к данным, перед сохранением данных. Вызовите EndEdit для всех компонентов BindingSource в форме.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 53101505230a51f109ace904c2f8322659733b4b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216323"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных

При изменении значений в элементах управления с привязкой к данным пользователи должны переходить от текущей записи для фиксации обновленного значения в базовом источнике данных, к которому привязан элемент управления. При перетаскивании элементов из [окна «Источники данных](add-new-data-sources.md) » на форму первый элемент, который удаляется, создает код для события нажатия кнопки « **сохранить** » <xref:System.Windows.Forms.BindingNavigator> . Этот код вызывает <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод класса <xref:System.Windows.Forms.BindingSource> . Поэтому вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метода создается только для первого <xref:System.Windows.Forms.BindingSource> , добавленного в форму.

Вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> фиксирует все актуальные изменения для всех редактируемых в настоящее время элементов управления с привязкой к данным. Таким образом, если элемент управления с привязкой к данным все еще находится в фокусе и вы нажимаете кнопку **Сохранить**, все ожидающие правки в этом элементе управления фиксируются до фактического сохранения (метод `TableAdapterManager.UpdateAll`).

Можно настроить приложение на автоматическую фиксацию изменений, даже если пользователь пытается сохранить данные без фиксации изменений в ходе процесса сохранения.

> [!NOTE]
> Конструктор добавляет `BindingSource.EndEdit` код только для первого элемента, помещенного в форму. Поэтому необходимо добавить строку кода для вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метода для каждой <xref:System.Windows.Forms.BindingSource> формы. Можно вручную добавить строку кода для вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метода для каждого из них <xref:System.Windows.Forms.BindingSource> . Кроме того, можно добавить `EndEditOnAllBindingSources` метод в форму и вызвать его перед выполнением сохранения.

В следующем коде используется запрос [LINQ (интегрированный в язык запросов)](/dotnet/csharp/linq/) для прохода по всем <xref:System.Windows.Forms.BindingSource> компонентам и вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метода для каждого из них <xref:System.Windows.Forms.BindingSource> в форме.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Вызов EndEdit для всех компонентов BindingSource в форме

1. Добавьте следующий код в форму, содержащую <xref:System.Windows.Forms.BindingSource> компоненты.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet1":::

2. Добавьте следующую строку кода непосредственно перед вызовами, чтобы сохранить данные формы ( `TableAdapterManager.UpdateAll()` метод):

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet2":::

## <a name="see-also"></a>См. также раздел

- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Иерархическое обновление](../data-tools/hierarchical-update.md)
