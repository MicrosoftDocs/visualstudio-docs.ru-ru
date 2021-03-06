---
title: Приступая к программированию настроек уровня документа для Word
description: Узнайте, что нужно знать, чтобы приступить к созданию настроек уровня документа для Microsoft Office Word с помощью Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ff19fd84b66b9d31ed806589044775e006ef7096
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860663"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Приступая к программированию настроек уровня документа для Word
  Если вы только приступите к созданию настроек уровня документа для Microsoft Office Word с помощью Visual Studio, вот что нужно знать.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Общие сведения о настройке уровня документа для работы с Word
 Каждая создаваемая настройка Word основана на одном документе. Чтобы начать работу с настройкой, конечный пользователь открывает документ или создает документ на основе шаблона Word. События в документе, например перемещение курсора в определенные области или нажатие кнопок и пунктов меню, могут вызывать методы обработки событий в сборке. После закрытия документа функции, предоставляемые этой настройкой, больше не будут доступны в Word.

 Дополнительные сведения см. в разделе [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Создание проектов на уровне документа для Word
 Чтобы создать настройку на уровне документа для Word, используйте шаблон проекта документ Word или шаблон Word в диалоговом окне **Новый проект** . Эти шаблоны включают в себя необходимые ссылки на сборки и файлы проекта.

 Дополнительные сведения о создании проекта уровня документа для Word см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Дополнительные сведения о шаблонах проектов см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Программирование документов Word с помощью элементов управления ведущего приложения
 *Ведущие элементы* и *элементы управления ведущего приложения* являются классами, предоставляющими модель программирования для настроек на уровне документа.

 Ведущие элементы предоставляют точку входа для кода, а также могут действовать как контейнеры для элементов управления ведущего приложения и Windows Forms элементов управления. В проектах уровня документа для Word ведущий элемент представлен `ThisDocument` классом.

 Элементы управления ведущего приложения основаны на собственных объектах Word, таких как элементы управления содержимым, закладки и узлы XML. Элементы управления ведущего приложения предоставляют аналогичные функции для собственных объектов Word, но они также имеют новые события, поддержку конструктора и возможность привязки данных. Они отображаются как объекты первого класса в коде проекта и IntelliSense, что упрощает обращение к конкретным объектам непосредственно в коде без необходимости перемещаться по объектной модели Word.

 Дополнительные сведения см. в следующих разделах:

- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)

- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)

- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Настройка пользовательского интерфейса Word
 Большинство Microsoft Office решений изменяют пользовательский интерфейс приложения Office, чтобы предоставить пользователям возможность взаимодействовать с решением. Существует множество способов изменения пользовательского интерфейса Word с помощью настройки уровня документа. Например, можно добавить элементы управления на ленту, а также отобразить панель действий. Дополнительные сведения см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

 Также можно открыть документ, связанный с проектом, непосредственно в Visual Studio. Документ, Открытый в Visual Studio, можно изменить с помощью пользовательского интерфейса Word. Можно также использовать документ в качестве области конструктора, который позволяет перетаскивать на него элементы управления. Дополнительные сведения см. [в статье проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Привязка элементов управления к данным
 Элементы управления содержимым и <xref:Microsoft.Office.Tools.Word.Bookmark> элемент управления находятся в списке элементов управления, которые можно перетаскивать из окна **Источники данных** . Добавление элементов управления содержимым и закладок таким образом автоматически привязывает их к источнику данных, настроенному с помощью окна. Без написания кода можно отображать данные из баз данных, служб и бизнес-объектов. Дополнительные сведения см. [в разделе Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Дальнейшие действия
 Сведения о создании настройки уровня документа для Word см. в разделе [Пошаговое руководство. Создание первой настройки уровня документа для Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). В этом пошаговом руководстве рассматриваются средства разработки Office в Visual Studio и модель программирования для настроек на уровне документа Word.

 Список разделов, в которых описаны некоторые распространенные задачи в проектах Word, см. [в разделе Общие задачи в программировании Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>См. также раздел
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)
- [Решения Word](../vsto/word-solutions.md)
- [Пошаговое руководство. Создание первой настройки уровня документа для Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)
- [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
