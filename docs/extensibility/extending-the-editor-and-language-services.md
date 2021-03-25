---
title: Расширение редактора и языковых служб | Документация Майкрософт
description: Вы можете добавить функции языковой службы в редактор и расширить возможности редактора кода Visual Studio. Дополнительные сведения о Managed Extensibility Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d85b018b4e0ea7d5ed1c91e617afcb2759d49b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070119"
---
# <a name="extend-the-editor-and-language-services"></a>Расширение редактора и языковых служб
Вы можете добавить функции языковой службы (например, IntelliSense) в собственный редактор и расширить большинство функций редактора кода Visual Studio.  Полный список возможностей, которые можно расширить, см. в разделе [точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md).

 Большинство функций редактора расширяется с помощью Managed Extensibility Framework (MEF). Например, если расширяемая функция редактора является цветовым выделением синтаксиса, можно написать *часть компонента* MEF, определяющую классификации, для которых необходимо выделить различные цвета и способ их обработки. Редактор также поддерживает несколько расширений одной и той же функции.

 Уровень представления редактора основан на Windows Presentation Framework (WPF). WPF предоставляет графическую библиотеку для гибкого форматирования текста, а также предоставляет визуализации, такие как графика и анимации.

 Пакет SDK для Visual Studio предоставляет адаптеры, называемые *оболочками совместимости* , для поддержки пакетов VSPackage, написанных для более ранних версий. Тем не менее, если у вас уже есть пакет VSPackage, рекомендуется обновить его до новой технологии, чтобы получить лучшую производительность и надежность.

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Приступая к работе с расширениями языковой службы и редактора](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Объясняет, как создать расширение для редактора.|
|[Внутри редактора](../extensibility/inside-the-editor.md)|Описание общей структуры редактора и список некоторых его функций.|
|[Managed Extensibility Framework в редакторе](../extensibility/managed-extensibility-framework-in-the-editor.md)|Объясняется, как использовать Managed Extensibility Framework (MEF) с редактором.|
|[Точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md)|Перечисляет точки расширения редактора. Точки расширения представляют функции редактора, которые можно расширять.|
|[Пошаговое руководство. Создание элемента оформления, команд и параметров представления (направляющие столбцов)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Пошаговые инструкции и описание создания элемента оформления представления, который рисует направляющие столбцов, чтобы обеспечить отображение в коде определенной ширины отображения.  Также демонстрируется чтение и запись параметров, а также объявление и реализация команд, которые можно вызывать из командного окна.|
|[Импорт в редактор](../extensibility/editor-imports.md)|Список служб, которые может импортировать расширение.|
|[Адаптация устаревшего кода к редактору](/previous-versions/visualstudio/visual-studio-2015/extensibility/adapting-legacy-code-to-the-editor?preserve-view=true&view=vs-2015)|Описание различных способов адаптации устаревшего кода (до Visual Studio 2010) для расширения редактора.|
|[Миграция языковой службы прежних версий](../extensibility/internals/migrating-a-legacy-language-service.md)|Объясняется, как выполнить миграцию языковой службы на основе VSPackage.|
|[Пошаговое руководство. Связывание типа содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Показывает, как связать тип содержимого с расширением имени файла.|
|[Пошаговое руководство. Создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md)|Показывает, как добавить значок в поле.|
|[Пошаговое руководство. выделение текста](../extensibility/walkthrough-highlighting-text.md)|Показывает, как использовать *теги* для выделения текста.|
|[Пошаговое руководство. Добавление структуры](../extensibility/walkthrough-outlining.md)|Показывает, как добавить структуризацию для определенных типов фигурных скобок.|
|[Пошаговое руководство. Отображение парных скобок](../extensibility/walkthrough-displaying-matching-braces.md)|Показывает, как выделить Парные фигурные скобки.|
|[Пошаговое руководство. Отображение подсказок краткие сведения](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Показывает, как отображать всплывающие окна краткие сведения, описывающие элементы кода, такие как свойства, методы и события.|
|[Пошаговое руководство. Отображение справки по сигнатурам](../extensibility/walkthrough-displaying-signature-help.md)|Показывает, как отображать всплывающие окна, предоставляющие сведения о количестве и типах параметров в сигнатуре.|
|[Пошаговое руководство: отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)|Показывает, как реализовать завершение операторов.|
|[Пошаговое руководство. Реализация фрагментов кода](../extensibility/walkthrough-implementing-code-snippets.md)|Показывает, как реализовать расширение фрагментов кода.|
|[Пошаговое руководство. Отображение предложений лампочки](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Показывает, как отображать лампочки для предложений кода.|
|[Пошаговое руководство. Использование команды оболочки с расширением редактора](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Показывает, как связать команду меню в VSPackage с компонентом MEF.|
|[Пошаговое руководство. Использование сочетания клавиш с расширением редактора](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Показывает, как связать ярлык меню в VSPackage с компонентом MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Содержит сведения о Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Предоставляет сведения о Windows Presentation Foundation (WPF).|

## <a name="reference"></a>Справочник
 Редактор Visual Studio включает следующие пространства имен.

 <xref:Microsoft.VisualStudio.Language.Intellisense>

 <xref:Microsoft.VisualStudio.Language.StandardClassification>

 <xref:Microsoft.VisualStudio.Editor>

 <xref:Microsoft.VisualStudio.Text>

 <xref:Microsoft.VisualStudio.Text.Adornments>

 <xref:Microsoft.VisualStudio.Text.Classification>

 <xref:Microsoft.VisualStudio.Text.Differencing>

 <xref:Microsoft.VisualStudio.Text.Document>

 <xref:Microsoft.VisualStudio.Text.Editor>

 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>

 <xref:Microsoft.VisualStudio.Text.Formatting>

 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>

 <xref:Microsoft.VisualStudio.Text.Operations>

 <xref:Microsoft.VisualStudio.Text.Outlining>

 <xref:Microsoft.VisualStudio.Text.Projection>

 <xref:Microsoft.VisualStudio.Text.Tagging>

 <xref:Microsoft.VisualStudio.Utilities>