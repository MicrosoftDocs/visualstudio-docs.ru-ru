---
title: Отложенная загрузка документов | Документация Майкрософт
description: Узнайте о задержке загрузки документов в Visual Studio и о том, как расширения кода, чтобы они не запрашивают элементы в документе перед его загрузкой.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 959af31f1986a4ff670adc5d74573cfb2bb850ce
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090987"
---
# <a name="delayed-document-loading"></a>Отложенная загрузка документов

Когда пользователь повторно открывает решение Visual Studio, большинство связанных документов не загружается немедленно. Фрейм окна документа создается в состоянии ожидания инициализации, а документ-заполнитель (называемый фреймом-заглушкой) помещается в таблицу выполняемых документов (РДТ).

Расширение может привести к тому, что документы проекта будут загружаться без необходимости путем запроса элементов в документах перед их загрузкой, что может увеличить общий объем памяти для Visual Studio.

## <a name="document-loading"></a>Загрузка документов

Фрейм заглушки и документ полностью инициализируются, когда пользователь обращается к документу, например, путем выбора вкладки рамки окна. Документ также может инициализироваться расширением, которое запрашивает данные документа, путем прямого доступа к РДТ для получения данных документа или доступа к РДТ косвенным образом, выполнив один из следующих вызовов:

- Метод фрейма окна <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .

- Метод рамки окна <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> для любого из следующих свойств:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Если расширение использует управляемый код, не следует вызывать метод, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> если только не уверены, что документ не находится в состоянии ожидания инициализации, или необходимо, чтобы документ был полностью инициализирован. Причина заключается в том, что метод всегда возвращает объект данных doc, создавая его при необходимости. Вместо этого следует вызывать один из методов `IVsRunningDocumentTable4` интерфейса.

- Если расширение использует C++, можно передать `null` ненужные параметры.

- Вы можете избежать ненужной загрузки документа, вызвав один из следующих методов, прежде чем запрашивать другие свойства.

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> использование [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Этот метод возвращает <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> объект, который содержит значение для [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) , если документ еще не инициализирован.

Узнать, когда документ был загружен, можно с помощью подписки на событие РДТ, которое возникает при полной инициализации документа. Существует две возможности:

- Если приемник событий реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , можно подписываться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,

- В противном случае можно подписываться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .

Следующий пример является гипотетическим сценарием доступа к документу: в расширении Visual Studio требуется отобразить некоторые сведения об открытых документах, например число блокировок редактирования и что-то о данных документа. Он перечисляет документы в РДТ с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> , затем вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> для каждого документа, чтобы получить сведения об изменении количества блокировок и данных документа. Если документ находится в состоянии ожидания инициализации, запрос данных документа приводит к необязательной инициализации.

Более эффективный способ доступа к документу заключается в использовании <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> для получения счетчика блокировки редактирования, а затем с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> для определения того, был ли документ инициализирован. Если флаги не содержат [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), документ уже инициализирован, и запрос данных документа с помощью не <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> приводит к ненужной инициализации. Если флаги включают [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), расширение не должно запрашивать данные документа до инициализации документа. Эта инициализация может быть обнаружена в `OnAfterAttributeChange(Ex)` обработчике событий.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Тестирование расширений для проверки принудительной инициализации

Отсутствует видимая подсказка, указывающая, был ли документ инициализирован, поэтому может быть трудно выяснить, что расширение является принудительной инициализацией. Можно задать раздел реестра, который упрощает проверку, поскольку в этом случае заголовок каждого документа, который не был полностью инициализирован, будет содержать текст *[заглушка]* в заголовке.

В **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad** задайте для **стубтабтитлеформатстринг** значение *{0} [заглушка]*.
