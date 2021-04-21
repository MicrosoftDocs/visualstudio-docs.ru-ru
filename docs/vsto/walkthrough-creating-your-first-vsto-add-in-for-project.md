---
title: Пошаговое руководство. Создание первой надстройки VSTO для Project
description: Создайте надстройку уровня приложения для Microsoft Project. Эта функция доступна для самого приложения, независимо от того, какие проекты открыты.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 48d7baf9605947818ffd79eb7312c0dbefe581ac
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824267"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>Пошаговое руководство. Создание первой надстройки VSTO для Project
  В этом пошаговом руководстве показано, как создать надстройку VSTO для проекта Microsoft Office. Функции, создаваемые в таком решении, доступны для самого приложения независимо от того, какие проекты открыты. Дополнительные сведения см. в статье [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- создание проекта надстройки VSTO для Project;

- написание кода, использующего объектную модель Project для добавления задачи в новый проект;

- Построение и запуск проекта для тестирования.

- Удаление завершенного проекта для прекращения автоматического запуска надстройки VSTO на компьютере разработчика.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] или [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].

## <a name="create-the-project"></a>Создание проекта

### <a name="to-create-a-new-project-in-visual-studio"></a>Создание проекта в Visual Studio

1. Запустите среду [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

3. В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.

4. В развернутом узле **Office/SharePoint** выберите узел **Надстройки Office** .

5. В списке шаблонов проекта выберите шаблон **Надстройка Project 2010** или **Надстройка Project 2013**.

6. В поле **Имя** введите **FirstProjectAddIn**.

7. Нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает проект **FirstProjectAddIn** и открывает файл кода **ThisAddIn** в редакторе.

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Написание кода, добавляющего в проект новую задачу
 Затем добавьте код в файл ThisAddIn. В этом коде для добавления новой задачи в проект используется объектная модель Project. По умолчанию файл кода ThisAddIn содержит следующий созданный код:

- Частичное определение класса `ThisAddIn` . Этот класс предоставляет точку входа для кода и обеспечивает доступ к объектной модели Project. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Оставшаяся часть `ThisAddIn` класса определяется в скрытом файле кода, который не следует изменять.

- Обработчики событий `ThisAddIn_Startup` и `ThisAddIn_Shutdown` . Эти обработчики событий вызываются, когда Project загружает и выгружает надстройку VSTO. Их можно использовать для инициализации надстройки VSTO в процессе ее загрузки, а также для освобождения ресурсов, используемых вашей надстройкой VSTO при ее выгрузке. Дополнительные сведения см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-task-to-a-new-project"></a>Добавление задачи в новый проект

1. В файл кода ThisAddIn добавьте в класс `ThisAddIn` указанный ниже код. В коде определяется обработчик события `NewProject` класса `Microsoft.Office.Interop.MSProject.Application`.

    Когда пользователь создает проект, этот обработчик событий добавляет в него задачу.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs" id="Snippet1":::

   Чтобы изменить проект, в этом примере кода используются следующие объекты:

- Поле `Application` класса `ThisAddIn` . Поле `Application` возвращает объект `Microsoft.Office.Interop.MSProject.Application`, который представляет текущий экземпляр Project.

- `pj`Параметр обработчика событий для события NewProject. Параметр `pj` — это объект `Microsoft.Office.Interop.MSProject.Project`, который представляет проект. Дополнительные сведения см. в разделе [Project Solutions](../vsto/project-solutions.md).

1. Если используется C#, добавьте в обработчик событий `ThisAddIn_Startup` указанный ниже код. Этот код соединяет `Application_Newproject` обработчик событий с событием NewProject.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs" id="Snippet2":::

## <a name="test-the-project"></a>Тестирование проекта
 Во время сборки и выполнения проекта убедитесь в том, что новая задача отображается в новом проекте.

### <a name="to-test-the-project"></a>Тестирование проекта

1. Нажмите клавишу **F5** для построения и запуска проекта. Запускается Microsoft Project, и при этом автоматически открывается пустой проект.

     При построении проекта код компилируется в сборку, которая включается в выходную папку сборки для проекта. Visual Studio также создает ряд записей реестра, которые позволяют Project обнаружить и загрузить надстройку VSTO, и настраивает параметры безопасности на компьютере разработчика, разрешая запуск надстройки VSTO. Дополнительные сведения см. в статье [Обзор процесса сборки решения Office](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100)).

2. Убедитесь в том, что новая задача добавлена в пустой проект.

3. Убедитесь в том, что в поле **Имя задачи** виден следующий текст:

     **Этот текст добавляется с помощью кода.**

4. Закройте Microsoft Project.

## <a name="clean-up-the-project"></a>Очистить проект
 Завершив разработку проекта, удалите с компьютера сборку надстройки VSTO, записи реестра и параметры безопасности. В противном случае надстройка VSTO будет запускаться при каждом открытии Microsoft Project на компьютере разработчика.

### <a name="to-clean-up-your-project"></a>Очистка проекта

1. В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.

## <a name="next-steps"></a>Дальнейшие действия
 Теперь, когда вы создали базовую надстройку VSTO для Project, ознакомьтесь с более подробными сведениями о разработке надстроек VSTO в следующих разделах.

- Общие задачи программирования, которые можно выполнять в надстройках VSTO для Project: [программирование VSTO-надстроек](../vsto/programming-vsto-add-ins.md).

- Использование объектной модели проекта: [проектные решения](../vsto/project-solutions.md).

- Построение и отладка надстроек VSTO для проекта: [Создание решений Office](../vsto/building-office-solutions.md).

- Развертывание надстроек VSTO для Project: [развертывание решения Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>См. также статью
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Решения проекта](../vsto/project-solutions.md)
- [Создание решений Office](../vsto/building-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)
