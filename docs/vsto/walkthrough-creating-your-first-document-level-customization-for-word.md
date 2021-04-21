---
title: Создание первой настройки уровня документа для Word
description: Создание настройки на уровне документа для Microsoft Word. Функциональные возможности, создаваемые в таком решении, доступны только в том случае, когда открыт конкретный документ.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 71051c6255f9035079a7888fb3a4c7df2f5eab59
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827556"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>Пошаговое руководство. Создание первой настройки уровня документа для Word

  В этом вводном пошаговом руководстве показано, как создавать настройку на уровне документа для Microsoft Office Word. Функциональные возможности, создаваемые в таком решении, доступны только в том случае, когда открыт конкретный документ. Для внесения изменений в приложение настройку на уровне документа использовать нельзя (например, для отображения новой вкладки ленты, когда открыт любой документ).

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- Создание проекта документа Word.

- Добавление текста в документ, который размещен в конструкторе Visual Studio.

- Написание кода, использующего объектную модель Word для добавления текста в настраиваемый документ при его открытии.

- Построение и запуск проекта для тестирования.

- Очистка проекта для удаления ненужных файлов сборки и параметров безопасности на компьютере разработчика.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования

 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Создание проекта

### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Создание нового проекта документа Word в Visual Studio

1. Запустите среду [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.
::: moniker range="vs-2017"
3. В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.

4. В развернутом узле **Office/SharePoint** выберите узел **надстройки VSTO** .

5. В списке шаблонов проектов выберите проект документа VSTO для Word.

6. В поле **имя** введите **фирстдокументкустомизатион**.

7. Нажмите кнопку **ОК**.

8. Выберите **создать новый документ** в **мастере инструменты Visual Studio для проектов Office** и нажмите кнопку **ОК**.
::: moniker-end
::: moniker range=">=vs-2019"
3. В диалоговом окне **Создание нового проекта** выберите проект **документ VSTO Word** .

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Щелкните **Далее**.

5. Введите **фирстворкбуккустомизатион** в поле **имя** в диалоговом окне **Настройка нового проекта** и нажмите кнопку **создать**.

6. Выберите **создать новый документ** в **мастере инструменты Visual Studio для проектов Office** и нажмите кнопку **ОК**.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает проект **фирстдокументкустомизатион** и добавляет в проект документ **фирстдокументкустомизатион** и файл кода ThisDocument. Документ **фирстдокументкустомизатион** открывается в конструкторе автоматически.

## <a name="close-and-reopen-the-document-in-the-designer"></a>Закрытие и повторное открытие документа в конструкторе

 Если вы случайно или преднамеренно закрыли документ в конструкторе во время разработки проекта, его можно снова открыть.

### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Закрытие и повторное открытие документа в конструкторе

1. Закройте документ, нажав кнопку **Закрыть** (X) в окне конструктора.

2. В **Обозреватель решений** щелкните правой кнопкой мыши файл кода **ThisDocument** и выберите пункт **Конструктор представлений**.

     \- или -

     В **Обозреватель решений** дважды щелкните файл кода **ThisDocument** .

## <a name="add-text-to-the-document-in-the-designer"></a>Добавление текста в документ в конструкторе

 Для разработки пользовательского интерфейса настройки можно изменить документ, который открыт в конструкторе. Например, можно добавить текст, таблицы или элементы управления Word. Дополнительные сведения об использовании конструктора см. в статье [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Добавление текста в документ с помощью конструктора

1. В документе, который открыт в конструкторе, введите следующий текст.

     **Этот текст был добавлен с помощью конструктора.**

## <a name="add-text-to-the-document-programmatically"></a>Программный Добавление текста в документ

 Добавьте код в файл кода ThisDocument. Новый код использует объектную модель Word для добавления второго абзаца текста в документ. По умолчанию файл кода ThisDocument содержит следующий созданный код:

- Частичное определение класса `ThisDocument`, который представляет модель программирования документа и предоставляет доступ к объектной модели Word. Дополнительные сведения см. в статьях [ведущий элемент документа](../vsto/document-host-item.md) и [Общие сведения о объектной модели Word](../vsto/word-object-model-overview.md). Остальная часть класса `ThisDocument` определяется в скрытом файле кода, изменять который не следует.

- Обработчики событий `ThisDocument_Startup` и `ThisDocument_Shutdown` . Эти обработчики событий вызываются при открытии и закрытии документа. Эти обработчики событий следует использовать для инициализации своей настройки при открытии документа и для освобождения ресурсов, применяемых настройкой, при закрытии документа. Дополнительные сведения см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Добавление второго абзаца текста в документ с помощью кода

1. В **Обозреватель решений** щелкните правой кнопкой мыши **ThisDocument** и выберите пункт **Просмотреть код**.

     Файл кода открывается в Visual Studio.

2. Замените обработчик событий `ThisDocument_Startup` следующим кодом. При открытии документа этот код добавляет второй абзац текста в документ.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs" id="Snippet1":::

    > [!NOTE]
    > Этот код использует значение индекса 1 для доступа к первому абзацу в свойстве <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>. Хотя Visual Basic и Visual C# используют массивы, которые начинаются с 0, нижней границей массива для большинства коллекций в объектной модели Word является 1. Дополнительные сведения см. [в статье написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md).

## <a name="test-the-project"></a>Тестирование проекта

### <a name="to-test-your-document"></a>Проверка документа

1. Нажмите клавишу **F5** для построения и запуска проекта.

     При построении проекта код компилируется в сборку, которая связана с документом. Visual Studio помещает копию документа и сборку в выходную папку сборки для проекта и настраивает параметры безопасности на компьютере разработчика, чтобы разрешить выполнение настройки. Дополнительные сведения см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).

2. Убедитесь, что в документе отображается следующий текст.

     **Этот текст был добавлен с помощью конструктора.**

     **Этот текст добавляется с помощью кода.**

3. Закройте документ.

## <a name="clean-up-the-project"></a>Очистить проект

 После завершения разработки проекта следует удалить файлы в выходной папке сборки и параметры безопасности, созданные в процессе сборки.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Очистка завершенного проекта на компьютере разработчика

1. В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.

## <a name="next-steps"></a>Дальнейшие действия

 Теперь после создания базовой настройки на уровне документа для Word в следующих разделах можно ознакомиться с процессом разработки настроек:

- Общие задачи программирования, которые можно выполнять в настройках уровня документа: [программы настройки на уровне документа](../vsto/programming-document-level-customizations.md).

- Задачи программирования, относящиеся к настройкам на уровне документа для Word: [решения Word](../vsto/word-solutions.md).

- Использование объектной модели Word: [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md).

- Настройка пользовательского интерфейса Word, например добавление настраиваемой вкладки на ленту или создание собственной панели действий: [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

- Использование расширенных объектов Word, предоставляемых решениями Office в Visual Studio, для выполнения задач, которые невозможно выполнить с помощью объектной модели Word (например, размещение управляемых элементов управления в документах и привязка элементов управления Word к данным с помощью Windows Forms модели привязки данных): [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md).

- Построение и отладка настроек на уровне документа для Word: [Создание решений Office](../vsto/building-office-solutions.md).

- Развертывание настроек уровня документа для Word: [развертывание решения Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>См. также статью

- [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Решения Word](../vsto/word-solutions.md)
- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)
- [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Создание решений Office](../vsto/building-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)
