---
title: Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint
description: Создание надстройки уровня приложения для Microsoft PowerPoint. Эта функция доступна для самого приложения, независимо от того, какие презентации открыты.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5adf37c6d55d4704ee370052646e620cbe716c3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824254"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint
  В этом пошаговом руководстве показано, как создать надстройку VSTO для Microsoft Office PowerPoint. Функции, создаваемые в подобном решении, доступны для приложения независимо от того, какие презентации открыты. Дополнительные сведения см. в статье [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

 В этом пошаговом руководстве описаны следующие задачи:

- создание проекта надстройки VSTO для PowerPoint;

- написание кода, использующего объектную модель PowerPoint для добавления текстового поля в каждый новый слайд;

- Построение и запуск проекта для тестирования.

- очистка проекта для прекращения автоматического запуска надстройки VSTO на компьютере разработчика.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- PowerPoint

## <a name="create-the-project"></a>Создание проекта

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Запустите среду [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

3. В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.

4. В развернутом узле **Office/SharePoint** выберите узел **Надстройки Office** .

5. В списке шаблонов проектов выберите шаблон проекта надстройки VSTO для PowerPoint.

6. В поле **имя** введите **фирстповерпоинтаддин**.

7. Нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает проект **фирстповерпоинтаддин** и открывает файл кода **ThisAddIn** в редакторе.

## <a name="write-code-that-adds-text-to-each-new-slide"></a>Написание кода, добавляющего текст к каждому новому слайду
 Затем добавьте код в файл ThisAddIn. Новый код использует объектную модель PowerPoint для добавления текстового поля в каждый новый слайд. По умолчанию файл кода ThisAddIn содержит следующий созданный код:

- Частичное определение класса `ThisAddIn` . Этот класс предоставляет точку входа для кода и обеспечивает доступ к объектной модели PowerPoint. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Оставшаяся часть `ThisAddIn` класса определяется в скрытом файле кода, который не следует изменять.

- Обработчики событий `ThisAddIn_Startup` и `ThisAddIn_Shutdown` . Эти обработчики событий вызываются, когда PowerPoint загружает и выгружает надстройку VSTO. Их можно использовать для инициализации надстройки VSTO в процессе ее загрузки, а также для освобождения ресурсов, используемых вашей надстройкой VSTO при ее выгрузке. Дополнительные сведения см. [в разделе события в проектах Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-text-box-to-each-new-slide"></a>Добавление текстового поля в каждый новый слайд

1. В файл кода ThisAddIn добавьте в класс `ThisAddIn` указанный ниже код. Этот код определяет обработчик событий для события [Microsoft.Office.Interop.PowerPoint.EApplication_Event. пресентатионневслиде](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) объекта [приложения](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) .

    Когда пользователь добавляет новый слайд в активную презентацию, этот обработчик событий добавляет текстовое поле в верхнюю часть нового слайда, а также добавляет в поле текст.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. Если используется C#, добавьте в обработчик событий `ThisAddIn_Startup` указанный ниже код. Этот код необходим для соединения `Application_PresentationNewSlide` обработчика событий с событием [Microsoft.Office.Interop.PowerPoint.EApplication_Event. пресентатионневслиде](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs" id="Snippet2":::

   Для изменения каждого нового слайда в приведенных выше примерах кода используются следующие объекты:

- Поле `Application` класса `ThisAddIn` . `Application`Поле возвращает объект [приложения](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) , который представляет текущий экземпляр PowerPoint.

- `Sld`Параметр обработчика событий для события [Microsoft.Office.Interop.PowerPoint.EApplication_Event. пресентатионневслиде](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) . `Sld`Параметр является объектом [слайда](/previous-versions/office/developer/office-2010/ff763417(v=office.14)) , который представляет новый слайд. Дополнительные сведения см. в разделе [решения PowerPoint](../vsto/powerpoint-solutions.md).

## <a name="test-the-project"></a>Тестирование проекта
 При построении и запуске проекта убедитесь, что текстовое поле отображается в новых слайдах, добавляемых в презентацию.

### <a name="to-test-the-project"></a>Тестирование проекта

1. Нажмите клавишу **F5** для построения и запуска проекта.

     При построении проекта код компилируется в сборку, которая включается в выходную папку сборки для проекта. Visual Studio также создает ряд записей реестра, которые позволяют PowerPoint обнаружить и загрузить надстройку VSTO, и настраивает параметры безопасности на компьютере разработчика, разрешая запуск надстройки VSTO. Дополнительные сведения см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).

2. В PowerPoint добавьте новый слайд в активную презентацию.

3. Убедитесь, что следующий текст добавляется в новое текстовое поле в верхней части слайда.

     **Этот текст добавляется с помощью кода.**

4. Закройте PowerPoint.

## <a name="clean-up-the-project"></a>Очистить проект
 Завершив разработку проекта, удалите с компьютера сборку надстройки VSTO, записи реестра и параметры безопасности. В противном случае надстройка VSTO будет запускаться при каждом открытии PowerPoint на компьютере разработчика.

### <a name="to-clean-up-your-project"></a>Очистка проекта

1. В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.

## <a name="next-steps"></a>Дальнейшие действия
 Теперь, когда вы создали базовую надстройку VSTO для PowerPoint, изучите более подробную информацию о разработке надстроек VSTO в следующих разделах:

- Общие задачи программирования, которые можно выполнять в надстройках VSTO для PowerPoint. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

- Использование объектной модели PowerPoint. Дополнительные сведения см. в разделе [решения PowerPoint](../vsto/powerpoint-solutions.md).

- Настройка пользовательского интерфейса PowerPoint, например, путем добавления настраиваемой вкладки на ленту или создания собственной настраиваемой области задач. Дополнительные сведения см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

- Построение и отладка надстроек VSTO для PowerPoint. Дополнительные сведения см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).

- Развертывание надстроек VSTO для PowerPoint. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>См. также статью
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Решения PowerPoint](../vsto/powerpoint-solutions.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Создание решений Office](../vsto/building-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)
