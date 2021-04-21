---
title: Пошаговое руководство. Создание первой надстройки VSTO для Excel
description: Создание надстройки уровня приложения для Microsoft Excel. Создаваемые функции доступны для самого приложения независимо от того, какие книги открыты.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fcb2bcc91eb1d19309904caae16701b814113089
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824410"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Пошаговое руководство. Создание первой надстройки VSTO для Excel
  В этом вводном пошаговом руководстве показано, как создавать надстройки уровня приложения для Microsoft Office Excel. Функции, создаваемые в подобном решении, доступны для приложения независимо от того, какие книги открыты.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- Создание проекта надстройки VSTO Excel для Excel.

- Написание кода с использованием объектной модели Excel, которая при сохранении книги добавляет в нее текст.

- Построение и запуск проекта для тестирования.

- Удаление завершенного проекта для прекращения автоматического запуска надстройки VSTO на компьютере разработчика.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Создание проекта

#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Создание проекта надстройки VSTO Excel в Visual Studio

1. Запустите среду [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

3. В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.

4. В развернутом узле **Office/SharePoint** выберите узел **Надстройки Office** .

5. В списке шаблонов проектов выберите **Надстройку Excel 2010** или **Надстройку Excel 2013**.

6. В поле **Имя** введите **FirstExcelAddIn**.

7. Нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает проект **проект firstexceladdin** и открывает файл кода ThisAddIn в редакторе.

## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Написание кода для добавления текста в сохраненную книгу
 Затем добавьте код в файл ThisAddIn. Новый код использует объектную модель Excel для вставки стандартного текста в первую строку активного листа. Активным является лист, открытый в момент сохранения книги пользователем. По умолчанию файл кода ThisAddIn содержит следующий созданный код:

- Частичное определение класса `ThisAddIn` . Этот класс предоставляет точку входа для кода и обеспечивает доступ к объектной модели Excel. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Оставшаяся часть `ThisAddIn` класса определяется в скрытом файле кода, который не следует изменять.

- Обработчики событий `ThisAddIn_Startup` и `ThisAddIn_Shutdown` . Эти обработчики событий вызываются, когда Excel загружает и выгружает надстройку VSTO. Их можно использовать для инициализации надстройки VSTO в процессе ее загрузки, а также для освобождения используемых надбавкой ресурсов при ее выгрузке. Дополнительные сведения см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Добавление строки текста в сохраненную книгу

1. В файл кода ThisAddIn добавьте в класс `ThisAddIn` указанный ниже код. Новый код определяет обработчик событий для события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> , которое возникает при сохранении книги.

    Когда пользователь сохраняет книгу, обработчик событий добавляет новый текст в начало активного листа.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. Если используется C#, добавьте в обработчик событий `ThisAddIn_Startup` указанный ниже код. Он используется для подключения обработчика событий `Application_WorkbookBeforeSave` к событию <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet2":::

   Для изменения книги при ее сохранении в приведенных выше примерах кода используются следующие объекты:

- Поле `Application` класса `ThisAddIn` . Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.Excel.Application> , который представляет текущий экземпляр Excel.

- Параметр `Wb` обработчика событий для события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> . Параметр `Wb` является объектом <xref:Microsoft.Office.Interop.Excel.Workbook> , который представляет сохраняемую книгу. Дополнительные сведения см. в разделе [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md).

## <a name="test-the-project"></a>Тестирование проекта

### <a name="to-test-the-project"></a>Тестирование проекта

1. Нажмите клавишу **F5** для построения и запуска проекта.

     При построении проекта код компилируется в сборку, которая включается в выходную папку сборки для проекта. Visual Studio также создает ряд записей реестра, которые позволяют Excel обнаружить и загрузить надстройку VSTO, и настраивает параметры безопасности на компьютере разработчика, разрешая запуск надстройки VSTO. Дополнительные сведения см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).

2. Сохраните книгу в Excel.

3. Убедитесь, что в книгу добавляется указанный ниже текст.

     **Этот текст добавляется с помощью кода.**

4. Закройте Excel.

## <a name="clean-up-the-project"></a>Очистить проект
 Завершив разработку проекта, удалите с компьютера сборку надстройки VSTO, записи реестра и параметры безопасности. В противном случае надстройка VSTO будет запускаться при каждом открытии программы Excel на компьютере разработчика.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Очистка завершенного проекта на компьютере разработчика

1. В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.

## <a name="next-steps"></a>Дальнейшие действия
 Теперь, когда вы создали базовую надстройку VSTO для Excel, изучите более подробную информацию о разработке надстроек VSTO в следующих разделах.

- Общие задачи программирования, которые можно выполнять в надстройках VSTO: [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md).

- Задачи программирования, характерные для надстроек VSTO для Excel: [решения Excel](../vsto/excel-solutions.md).

- Использование объектной модели Excel: [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md).

- Настройка пользовательского интерфейса Excel, например добавление настраиваемой вкладки на ленту или создание собственной настраиваемой области задач: [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

- Построение и отладка надстроек VSTO для Excel. [Создание решений Office](../vsto/building-office-solutions.md).

- Развертывание надстроек VSTO для Excel: [развертывание решения Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>См. также статью
- [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Решения Excel](../vsto/excel-solutions.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Создание решений Office](../vsto/building-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)
