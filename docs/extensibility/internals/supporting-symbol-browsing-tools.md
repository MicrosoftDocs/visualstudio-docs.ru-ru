---
title: Поддержка средств Symbol-Browsing | Документация Майкрософт
description: Visual Studio предоставляет возможности обзора символов в Visual Studio. Узнайте, как расширить эти возможности с помощью библиотек для символов в компонентах.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d54f56ae3bc5fd5956f67400d84edfd4c8c9e55c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080571"
---
# <a name="supporting-symbol-browsing-tools"></a>Вспомогательные средства просмотра символов
**Обозреватель объектов**, **представление классов**, **Обозреватель вызовов** и **Поиск результатов поиска символов** предоставляют возможности просмотра символов в Visual Studio. Эти средства отображают иерархические древовидные представления символов и отображают связи между символами в дереве. Символы могут представлять пространства имен, объекты, классы, члены классов и другие элементы языка, содержащиеся в различных компонентах. Компоненты включают в себя проекты Visual Studio, внешние платформа .NET Framework компонентов и типов (TLB) библиотеки. Дополнительные сведения см. [в разделе Просмотр структуры кода](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Библиотеки Symbol-Browsing
 Как разработчик языка можно расширять возможности просмотра символов в Visual Studio, создавая библиотеки, которые отписывают символы в компонентах и предоставляют списки символов для диспетчера объектов Visual Studio с помощью набора интерфейсов. Библиотека описывается <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> интерфейсом. Диспетчер объектов Visual Studio реагирует на запросы новых данных из средств обзора символов, получая данные из библиотек и упорядочивая их. Впоследствии он заполняет или обновляет средства с помощью запрошенных данных. Чтобы получить ссылку на диспетчер объектов Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> передайте <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> идентификатор службы в `GetService` метод.

 Каждая библиотека должна быть зарегистрирована в диспетчере объектов Visual Studio, которая собирает сведения обо всех библиотеках. Чтобы зарегистрировать библиотеку, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод. В зависимости от того, какой инструмент инициирует запрос, диспетчер объектов Visual Studio находит соответствующую библиотеку и запрашивает данные. Данные передаются между библиотеками и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчером объектов в списках символов, описываемых <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> интерфейсом.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Диспетчер объектов отвечает за периодическое обновление средств обзора символов для отражения самых актуальных данных, содержащихся в библиотеках.

 На приведенной ниже схеме показан пример ключевых элементов процесса обмена запросами и данными между библиотекой и диспетчером объектов Visual Studio. Интерфейсы на схеме являются частью приложения с управляемым кодом.

 ![Поток данных между библиотекой и менеджером объекта](../../extensibility/internals/media/callbrowserdiagram.gif "каллбровсердиаграм")

 Чтобы предоставить список символов для диспетчера объектов Visual Studio, необходимо сначала зарегистрировать библиотеку с помощью диспетчера объектов Visual Studio, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод. После регистрации библиотеки диспетчер объектов Visual Studio запрашивает определенные сведения о возможностях библиотеки. Например, он запрашивает флаги библиотеки и поддерживаемые категории, вызывая <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> методы и. В некоторый момент, когда один из средств запрашивает данные из этой библиотеки, диспетчер объектов запрашивает список символов верхнего уровня, вызывая <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> метод. В ответ библиотека создает список символов и предоставляет их диспетчеру объектов Visual Studio через <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> интерфейс. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Диспетчер объектов определяет, сколько элементов находится в списке, вызывая <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> метод. Все следующие запросы относятся к заданному элементу в списке и указывают номер индекса элемента в каждом запросе. Диспетчер объектов Visual Studio продолжает получать сведения о типе, доступе и других свойствах элемента, вызывая <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> метод.

 Он определяет имя элемента путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> метода и запрашивает сведения о значке, вызывая <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> метод. Значок отображается слева от имени элемента и показывает тип элемента, доступность и другие свойства.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Диспетчер объектов вызывает метод, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> чтобы определить, является ли заданный элемент списка расширяемым и наличием дочерних элементов. Если пользовательский интерфейс отправляет запрос на расширение элемента, диспетчер объектов запрашивает дочерний список символов, вызывая <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> метод. Процесс продолжится с различными частями дерева, построенными по запросу.

> [!NOTE]
> Для реализации собственного поставщика символов кода используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> интерфейсы и.

## <a name="see-also"></a>См. также
- [Практическое руководство. Регистрация библиотеки с помощью диспетчера объектов](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Практическое руководство. Предоставление списка символов, переданных из библиотеки в диспетчер объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Практическое руководство. Определение символов в библиотеке](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
